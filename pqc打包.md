









### SQL代码：

###设置主键自增从1开始

```
TRUNCATE TABLE 表名
```

####条件查询  条件显示：

```sql
select  form_id,(CASE WHEN file_type = 'O' THEN '外來文件' when file_type='G' then '技術文件' ELSE 'ISO文件' END) || '-' ||  (case when file_name is null then '' else file_name end)  as form_name,
            (case when router_stage2 = '0' then '新增'
                    when router_stage2 = '1' then '變更' else '作廢' end)as form_type,
             (case  when router_stage = '0' then '開立'
                    when router_stage = '1' then '送簽中'
                    when router_stage = '2' then '結案'
                    else '作廢' end) as form_state,
            create_user as form_employ,create_date as form_date
        from flow_system.flow_maintain_isofiles
```



### cmd方式结束进程

​		1、查看进程

```
netstat -ano | findstr 8080
```

![img](https://img-blog.csdnimg.cn/20200311164353996.png)

​		2、结束进程

​	

```
	taskkill /F /PID 15716
```

![img](https://img-blog.csdnimg.cn/202003111647019.png)

### app重新打包

1、到10.57.30.111上

打开hbuilderX

发行-云打包

生成安卓证书（需要有jre的环境）：

使用keytool -genkey命令生成证书：

```
keytool -genkey -alias pqc -keyalg RSA -keysize 2048 -validity 36500 -keystore pqc.keystore
```

![image-20210112101947935](images/image-20210112101947935.png)

testalias是证书别名，可修改为自己想设置的字符，建议使用英文字母和数字
test.keystore是证书文件名称，可修改为自己想设置的文件名称，也可以指定完整文件路径

查看证书信息：

```
keytool -list -v -keystore test.keystore  
```

![image-20210112102054656](images/image-20210112102054656.png)

云打包配置：

**1>证书别名：生成证书时使用-alias参数设置的证书别名；
2>私钥密码：生成证书时使用的keystore密码；
3>证书文件：生成证书时使用-keystore参数设置的证书保存路径；**

**打包完成自动返回下载地址，点击链接下载APP安装

2、到10.57.30.102上

放C:\02.Website\API\TMP 文件夹里 改名PQC.apk

### git提交代码

鼠标右键打开git bash here:
<1>输入git config --global [user.name](http://user.name/) “你的用户名”
<2>输入git config --global user.email “你的邮箱”
<3>输入git init
<4>输入git remote add origin 你刚才建立的项目连接

```
<5>输入git add .
<6>输入git commit -m “注释”
```

<7>输入git config http.postBuffer 524288000 (特别提醒: 此行是在本地设置缓存, 有些项目文件较大, 使用http无法上传,可设置此命令)

```
<8>输入git push -u origin master 将代码推送到gitlab端
```

![image-20210112104831750](images/image-20210112104831750.png)

```
git remote add origin https://github.com/wyh136136/spingcloud2021.git
git branch -M master
git push -u origin master
git config --system http.sslcainfo "E:/Git/mingw64/ssl/certs/ca-bundle.crt"  
```

```css
##angular更改单独模块的样式

:host ::ng-deep{
  .ant-table-thead>tr>th {
    color: white;
    /* font-weight: bolder; */
    background: #143f8d;
    border-bottom: 1px solid #e8e8e8;
    -webkit-transition: background 0.3s ease;
    transition: background 0.3s ease;
  }
      a {
        color: #190996;
        text-decoration: none;
      }
     
}
#####angular自定义样式

```



相同点：在启动类上面添加 @EnableDiscoveryClient、@EnableEurekaClient 这二个注解作用，都可以让该服务注册到注册中心上去。

不同点：@EnableEurekaClient 只支持Eureka注册中心，@EnableDiscoveryClient 支持Eureka、Zookeeper、Consul 这三个注册中心。



### postgresql日期转换

```
函数	                      返回类型	          描述	               例子
to_char(timestamp, text)	text	 把时间戳转换成字串	  	 to_char(current_timestamp, 'HH12:MI:SS')
to_char(interval, text)	    text	 把时间间隔转为字串	to_char(interval '15h 2m 12s', 'HH24:MI:SS')
to_char(int, text)	        text	          把整数转换成字串	to_char(125, '999')
to_char(double precision, text)	text	   把实数/双精度数转换成字串	to_char(125.8::real, '999D9')
to_char(numeric, text)	  text	把numeric转换成字串	to_char(-125.8, '999D99S')
to_date(text, text)	date	把字串转换成日期	to_date('05 Dec 2000', 'DD Mon YYYY')
to_timestamp(text, text)	timestamp	把字串转换成时间戳	to_timestamp('05 Dec 2000', 'DD Mon YYYY')
to_timestamp(double)	timestamp	把UNIX纪元转换成时间戳	to_timestamp(200120400)
to_number(text, text)	numeric	把字串转换成numeric	to_number('12,454.8-', '99G999D9S')
```

