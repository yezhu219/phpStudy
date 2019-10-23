# PHP 笔记

## 1.  tp5 读取配置

-  通过` config::get('app_debug')` 获取配置
- 通过`config('app_debug')`获取配置

## 2. 功能设计

1. 商品

   1. 1商品分类

   1. 2商品详情

   1. 3商品列表

   1. 4 商品搜索

2. 订单

   2. 1订单分类

   2. 2订单详情

   2. 3订单搜索

## 3. 数据库设计

1. 商品分类表  categroy

   | 字段 | 类型     | 备注   |
   | ---- | -------- | ------ |
   | id   | int      |        |
   | pid  | int      | 父级id |
   | name | var_char | 分类名 |
   |      |          |        |

   

## 4. 问题记录

### 4.1 配置网站根目录

  1. 设置public文件夹为根目录

  2. pathinfo访问模式： 域名/index.php/模块名/控制器名/方法名

     - url重写，隐藏index.php

       ```php
       httpd.conf配置文件中加载了mod_rewrite.so模块
       AllowOverride None 将None改为 All
       把下面的内容保存为.htaccess文件放到应用入口文件的同级目录下
       <IfModule mod_rewrite.c>
         Options +FollowSymlinks -Multiviews
         RewriteEngine On
       
         RewriteCond %{REQUEST_FILENAME} !-d
         RewriteCond %{REQUEST_FILENAME} !-f
        // RewriteRule ^(.*)$ index.php/$1 [QSA,PT,L] php5.7以上版本会报No input file specified.
         RewriteRule ^(.*)$ index.php [L,E=PATH_INFO:$1]  //使用此方法
       </IfModule>
       ```

     - url 重写后访问：域名/模块名/控制器名/方法名

![](.\img\url.png)

   	3.  路由配置问题

![](D:\笔记\img\route-2.png)

![](D:\笔记\img\route-1.png)

> tp5.1 中 use think\Route报错，不使用时没有提示，可以注释掉
>
> 如果想用提示，怎use think\facade\Route

```
facade 用处：不用实例化就可以调用类的方法

 
```

![](./img\使用门面.png)



![](./img\使用门面-1.png)






![](./img\不使用门面.png)





![](./img\不使用门面-1.png)



> 使用门面与不使用门面获取的参数有差异
