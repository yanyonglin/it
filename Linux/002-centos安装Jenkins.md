1. 安装JDK 如果已经安装忽略
  yum install java-1.8.0-openjdk.x86_64

2.安装jenkins
  wget -O /etc/yum.repos.d/jenkins.repo http://jenkins-ci.org/redhat/jenkins.repo
  rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
  yum -y install jenkins
  
  如果不能安装就到官网下载jenkis的rmp包，官网地址(http://pkg.jenkins-ci.org/redhat-stable/)
  wget http://pkg.jenkins-ci.org/redhat-stable/jenkins-2.7.3-1.1.noarch.rpm
  rpm -ivh jenkins-2.7.3-1.1.noarch.rpm
  
  安装已完成，jenkins默认启动端口8080，如果需要修改端口，执行一下命令修改
  vi /etc/sysconfig/jenkins
  找到JENKINS_PORT="8080"  将8080修改为你想要的端口
  
3.管理jenkins
  //启动
  service jenkins start
  //停止
  service jenkins stop
  //重启
  service jenkins restart
  
  备注:如果启动失败用以下命令
  systemctl start jenkins
  
 4.初始化jenkins
  将以下连接在浏览器中打开
  http://localhost:8080
  如果无法访问，检查IP或者端口是否正确。如果是虚拟机，关闭防火墙.
  centos7一下关闭防火墙
  servcie iptables stop
  centos7以上关闭防火墙(centos7默认防火墙为firewall)
  systemctl stop firewalld.service
  禁止firewall开机启动
  systemctl disable firewalld.service 
  
  查看jenkins初始密码
  cat /var/lib/jenkins/secrets/initialAdminPassword
  将默认密码输入，点击右下角continue 
  选择 install suggest plugins
  稍等片刻，jenkins初始化完毕
  
