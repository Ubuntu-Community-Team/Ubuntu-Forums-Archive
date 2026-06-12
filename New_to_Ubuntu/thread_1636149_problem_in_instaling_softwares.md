---
title: "problem in instaling softwares"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by gmghulamabbas on 2010-12-02
Good evening everybody;

I am very new in ubuntu. i am trying  to install engineering softwares from ubuntu software center but i am having an error "Failed to download package file - Check your Internet connection." while my internet is proroperly working ... Plz can anybody helps me to fix this error???

guys waiting for your positive response. 


Thanks

Regards
Ghulam Abbas

---

### Post by Frogs Hair on 2010-12-02
This has happened to me and I have had to wait a while and try again . Try running sudo apt-get update in the terminal to see if you're sources refresh and try again.  Welcome to the Forums

---

### Post by gmghulamabbas on 2010-12-03
THanks for helping ... i tried as u said ... but now i m having this error ... i do not know what to do now ... plz help me to fix this error ... 

```
gmghulamabbas@abbas:~$ apt get-update 
The program 'apt' is currently not installed.  You can install it by typing:
sudo apt-get install openjdk-6-jdk
gmghulamabbas@abbas:~$ sudo apt-get install openjdk-6-jdk
[sudo] password for gmghulamabbas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ca-certificates-java icedtea-6-jre-cacao java-common libaccess-bridge-java libaccess-bridge-java-jni libgif4 libice-dev libpthread-stubs0 libpthread-stubs0-dev
  libsm-dev libx11-dev libxau-dev libxcb1-dev libxdmcp-dev libxt-dev openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib ttf-dejavu-extra tzdata-java
  x11proto-core-dev x11proto-input-dev x11proto-kb-dev xtrans-dev
Suggested packages:
  default-jre equivs openjdk-6-demo openjdk-6-source visualvm icedtea6-plugin sun-java6-fonts ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho
  ttf-kochi-mincho ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts ttf-bengali-fonts
The following NEW packages will be installed:
  ca-certificates-java icedtea-6-jre-cacao java-common libaccess-bridge-java libaccess-bridge-java-jni libgif4 libice-dev libpthread-stubs0 libpthread-stubs0-dev
  libsm-dev libx11-dev libxau-dev libxcb1-dev libxdmcp-dev libxt-dev openjdk-6-jdk openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib ttf-dejavu-extra tzdata-java
  x11proto-core-dev x11proto-input-dev x11proto-kb-dev xtrans-dev
0 upgraded, 25 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.8MB/51.7MB of archives.
After this operation, 141MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ci.archive.ubuntu.com/ubuntu/ maverick/main x11proto-core-dev all 7.0.17-1 [95.2kB]
Get:2 http://ci.archive.ubuntu.com/ubuntu/ maverick/main libice-dev amd64 2:1.0.6-1 [67.1kB]
Get:3 http://ci.archive.ubuntu.com/ubuntu/ maverick/main libxau-dev amd64 1:1.0.6-1 [20.4kB]                                                                           
Get:4 http://ci.archive.ubuntu.com/ubuntu/ maverick/main libxdmcp-dev amd64 1:1.0.3-2 [22.8kB]                                                                         
Get:5 http://ci.archive.ubuntu.com/ubuntu/ maverick/main x11proto-input-dev all 2.0-2 [62.5kB]                                                                         
Get:6 http://ci.archive.ubuntu.com/ubuntu/ maverick/main x11proto-kb-dev all 1.0.4-1 [27.3kB]                                                                          
Get:7 http://ci.archive.ubuntu.com/ubuntu/ maverick/main xtrans-dev all 1.2.5-1 [68.5kB]                                                                               
Get:8 http://ci.archive.ubuntu.com/ubuntu/ maverick/main libpthread-stubs0 amd64 0.3-2 [3,202B]                                                                        
Get:9 http://ci.archive.ubuntu.com/ubuntu/ maverick/main libpthread-stubs0-dev amd64 0.3-2 [2,412B]                                                                    
Get:10 http://ci.archive.ubuntu.com/ubuntu/ maverick/main libxcb1-dev amd64 1.6-1 [81.1kB]                                                                             
Get:11 http://ci.archive.ubuntu.com/ubuntu/ maverick/main libx11-dev amd64 2:1.3.3-3ubuntu1 [3,506kB]                                                                  
Get:12 http://ci.archive.ubuntu.com/ubuntu/ maverick/main libx11-dev amd64 2:1.3.3-3ubuntu1 [3,506kB]                                                                  
Err http://ci.archive.ubuntu.com/ubuntu/ maverick-updates/main openjdk-6-jre-lib all 6b20-1.9.1-1ubuntu3                                                               
  404  Not Found [IP: 91.189.92.171 80]
Get:13 http://ci.archive.ubuntu.com/ubuntu/ maverick/main libsm-dev amd64 2:1.1.1-1 [28.3kB]                                                                           
Get:14 http://ci.archive.ubuntu.com/ubuntu/ maverick/main libxt-dev amd64 1:1.0.7-1 [525kB]                                                                            
Err http://security.ubuntu.com/ubuntu/ maverick-security/main openjdk-6-jre-lib all 6b20-1.9.1-1ubuntu3                                                                
  404  Not Found [IP: 91.189.88.37 80]
Err http://security.ubuntu.com/ubuntu/ maverick-security/main openjdk-6-jre-headless amd64 6b20-1.9.1-1ubuntu3                                                         
  404  Not Found [IP: 91.189.88.37 80]
Err http://security.ubuntu.com/ubuntu/ maverick-security/main openjdk-6-jre amd64 6b20-1.9.1-1ubuntu3                                                                  
  404  Not Found [IP: 91.189.88.37 80]
Err http://ci.archive.ubuntu.com/ubuntu/ maverick-updates/main openjdk-6-jdk amd64 6b20-1.9.1-1ubuntu3                                                                 
  404  Not Found [IP: 91.189.92.171 80]
Err http://security.ubuntu.com/ubuntu/ maverick-security/main openjdk-6-jdk amd64 6b20-1.9.1-1ubuntu3                                                                  
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com/ubuntu/ maverick-security/main icedtea-6-jre-cacao amd64 6b20-1.9.1-1ubuntu3                                                            
  404  Not Found [IP: 91.189.92.166 80]
Fetched 1,238kB in 2min 35s (7,951B/s)                                                                                                                                 
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-lib_6b20-1.9.1-1ubuntu3_all.deb  404  Not Found [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b20-1.9.1-1ubuntu3_amd64.deb  404  Not Found [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre_6b20-1.9.1-1ubuntu3_amd64.deb  404  Not Found [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jdk_6b20-1.9.1-1ubuntu3_amd64.deb  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea-6-jre-cacao_6b20-1.9.1-1ubuntu3_amd64.deb  404  Not Found [IP: 91.189.92.166 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Thanks

Regards
**Ghulam Abbas**

---

### Post by tajiknomi on 2010-12-03
[SIZE=2]Ping your IP,...

In terminal, type:-

*ping 91.189.88.37.80*

if its doesn't work, then try to TURN the **p*roxy off***, Turn On, and see if it works.....
[/SIZE]

---

### Post by mastablasta on 2010-12-03
> **gmghulamabbas said:**
> THanks for helping ... i tried as u said ... but now i m having this error ... i do not know what to do now ... plz help me to fix this error ... 
 
```
gmghulamabbas@abbas:~$ apt get-update 

 
you misspelled the command.
 it should be
 
[CODE] 
sudo apt-get update 

``` 
 
aslo you should check your sources and find a new server for repositories closer to your country or in your country. that will also give you faster transfer speeds.

---

### Post by sikander3786 on 2010-12-03
Welcome to the forums :-)

Are you behind a proxy server? If yes, did you configure it under Software Sources?

If you are not using a proxy server, go to Software Center > Edit > Software Center and select the Main Server.

Then go to Terminal and post the output of these commands.

```
sudo apt-get update
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
cat /etc/apt/sources.list
```

Post the output individually and individually wrap them with code tags # from post menu. [/code] at the end [code] at the beginning.

---

