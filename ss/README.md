# Server(Centos7)：
1.Install wget
```
yum -y install wget  
```
2.Download and Run
```
wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/hceng/learn/master/ss/SS/shadowsocks-all.sh && sudo chmod +x shadowsocks-all.sh && sudo ./shadowsocks-all.sh
```
3.Run bbr
```
wget --no-check-certificate -O bbr.sh https://raw.githubusercontent.com/hceng/learn/master/ss/BBR/bbr.sh && sudo chmod +x bbr.sh && sudo ./bbr.sh
```
4.Server port monitor
```
//a.install python3
yum -y install openssl-devel bzip2-devel expat-devel gdbm-devel readline-devel \
               sqlite-devel gcc automake autoconf libtool make ntpdate  
wget https://www.python.org/ftp/python/3.6.3/Python-3.6.3.tgz
tar zxvf Python-3.6.3.tgz
cd ./Python-3.6.3 && ./configure prefix=/usr/local/python3 && make && make install

//b.Download SSPort
wget --no-check-certificate -O SSPort.py https://raw.githubusercontent.com/hceng/learn/master/ss/SSPort/SSPort.py 
wget --no-check-certificate -O config.ini https://raw.githubusercontent.com/hceng/learn/master/ss/SSPort/config.ini

//c.Modify configuration file:IP and Email

//d.Self-start
wget --no-check-certificate -O autostart.sh https://raw.githubusercontent.com/hceng/learn/master/ss/SSPort/autostart.sh  && sudo chmod +x autostart.sh && mv autostart.sh /etc/init.d/ && systemctl enable autostart.sh
```

5.Others

- Start, stop, restart, view status::
```
/etc/init.d/shadowsocks-* start | stop | restart | status
```

- View connections:
```
yum install lsof -y  //CentOs
apt-get install lsof -y //Ubuntu

lsof -i -n -P | egrep -c ':1080.+ESTABLISHED'  //Port:1080

lsof -i -n -P | egrep ':1080.+ESTABLISHED'
```

- Uninstall：
```
./shadowsocks-all.sh uninstall
```

# Client:
- Android: [shadowsocks-android](https://github.com/shadowsocks/shadowsocks-android/releases)
- iPhone/iPad: [Shadowrocket(freeluffy).ipa](https://github.com/hceng/learn/blob/master/ssr/Shadowrocket(freeluffy).ipa)
- Windows: [shadowsocks-windows](https://github.com/shadowsocks/shadowsocks-windows/releases)
- MacOS: [ShadowsocksX-NG](https://github.com/shadowsocks/ShadowsocksX-NG/releases)
- Linux: [CharlesScripts](https://github.com/the0demiurge/CharlesScripts/blob/master/charles/bin/ssr)

# Bookmark:
- [IP availability detection tool](https://www.toolsdaquan.com/ipcheck/)
- [bandwagonhost](https://bandwagonhost.com/index.php)
- [vultr](https://vultr.com/)
- [AEAD Ciphers](https://shadowsocks.org/en/spec/AEAD-Ciphers.html)