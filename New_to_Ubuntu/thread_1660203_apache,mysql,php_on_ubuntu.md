---
title: "apache,mysql,php on ubuntu"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-01-05
i have ubuntu 10.10 on my system...can anybody pls tell me from where to download how to install and configure apache,mysql and php on my machine... pls help me.. i m really thankful to all:p:p

---

### Post by mastablasta on 2011-01-05
you want LAMP server?
 
have a look here: 
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)
[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp)
 
[http://www.ubuntugeek.com/step-by-step-ubuntu-10-04-lucid-lynx-lamp-server-setup.html](http://www.ubuntugeek.com/step-by-step-ubuntu-10-04-lucid-lynx-lamp-server-setup.html)

---

### Post by vivek.pandey on 2011-01-05
> **mastablasta said:**
> you want LAMP server?
 
have a look here: 
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)
[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp)
 
[http://www.ubuntugeek.com/step-by-step-ubuntu-10-04-lucid-lynx-lamp-server-setup.html](http://www.ubuntugeek.com/step-by-step-ubuntu-10-04-lucid-lynx-lamp-server-setup.html)

i tried doing this using ur first link but i met with a prob wen i try to restart apache as needed to configure it with mysql or php using thiscommand as mentioned in the tutorial 
sudo /etc/init.d/apache2 restart

i m getting this error pls help
* Restarting web server apache2                                                (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.

---

### Post by mastablasta on 2011-01-05
ok check the apache erro log for more informaiton.
 
though it sounds a bit like you need to open ports (currently ubuntu is configured that it doens't listen to anything and outgoing connection is ok but not incoming as i understand it). so this could be it. hopefully someone with better knowledge of network and servers can give you more help.

---

### Post by vivek.pandey on 2011-01-05
> **mastablasta said:**
> ok check the apache erro log for more informaiton.
 
though it sounds a bit like you need to open ports (currently ubuntu is configured that it doens't listen to anything and outgoing connection is ok but not incoming as i understand it). so this could be it. hopefully someone with better knowledge of network and servers can give you more help.

well i m pretty new to ubuntu.pls tell were i can find apache error log?

---

### Post by scheuri on 2011-01-05
> **neo_aryan said:**
> i tried doing this using ur first link but i met with a prob wen i try to restart apache as needed to configure it with mysql or php using thiscommand as mentioned in the tutorial 
sudo /etc/init.d/apache2 restart

i m getting this error pls help
* Restarting web server apache2                                                (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.

Likely there is already something running port 80 (maybe you download apache1 or an earlier version or LAMP).
To check this, give us the output of the commmand "netstat -a" (without the quotes "").

The error logs are likely under /var/log/apache2 or something similar.

Being new to Ubuntu (and linux in general) also means reading a lot and searching a lot. So, also try to search "Ubuntu error log apache2" in google, maybe someone else has pointed out the exact place where the error.log is.

Good luck
Cheers
Scheuri

---

### Post by vivek.pandey on 2011-01-05
> **scheuri said:**
> Likely there is already something running port 80 (maybe you download apache1 or an earlier version or LAMP).
To check this, give us the output of the commmand "netstat -a" (without the quotes "").

The error logs are likely under /var/log/apache2 or something similar.

Being new to Ubuntu (and linux in general) also means reading a lot and searching a lot. So, also try to search "Ubuntu error log apache2" in google, maybe someone else has pointed out the exact place where the error.log is.

Good luck
Cheers
Scheuri

wat to check n wat to do next after typing netstat -a
in terminal/?

---

### Post by stoogiebuncho on 2011-01-05
Are you trying to set up a development server for testing purposes on your own machine, or are you trying to set up a server to host your website on the internet?

You can post the results of the netstat -a command here so we can look at them.

By the way, what does your user name mean?

---

### Post by mastablasta on 2011-01-05
> **stoogiebuncho said:**
> Are you trying to set up a development server for testing purposes on your own machine, or are you trying to set up a server to host your website on the internet?
 
 
good question there is plenty of free or cheap webhost with LAMP.

---

### Post by vivek.pandey on 2011-01-05
> **stoogiebuncho said:**
> Are you trying to set up a development server for testing purposes on your own machine, or are you trying to set up a server to host your website on the internet?

You can post the results of the netstat -a command here so we can look at them.

By the way, what does your user name mean?

i just wanna set a development server to run my php script or to embed php with mysql.. thats simple websites.. actually m in learning process.. in windows i used to practise it with uniserver and myPHP admin..
here is the result for netstat -a 
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     
tcp        0      0 localhost.lo:postgresql *:*                     LISTEN     
tcp        0      0 *:gdomap                *:*                     LISTEN     
tcp        0      0 localhost.localdom:4001 *:*                     LISTEN     
tcp        0      0 *:9192                  *:*                     LISTEN     
tcp        0      0 localhost.localdo:mysql *:*                     LISTEN     
tcp        0      0 NEO:43258               77.67.41.129:www        ESTABLISHED
unix  3      [ ]         STREAM     CONNECTED     16370    
unix  3      [ ]         STREAM     CONNECTED     16368    
unix  3      [ ]         STREAM     CONNECTED     16367    
unix  3      [ ]         SEQPACKET  CONNECTED     16215    
unix  3      [ ]         SEQPACKET  CONNECTED     16214    
unix  3      [ ]         STREAM     CONNECTED     16213    
unix  3      [ ]         STREAM     CONNECTED     16212    
unix  3      [ ]         STREAM     CONNECTED     15764    
unix  3      [ ]         STREAM     CONNECTED     15763    
unix  3      [ ]         STREAM     CONNECTED     15424    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     15423    
unix  3      [ ]         SEQPACKET  CONNECTED     15321    
unix  3      [ ]         SEQPACKET  CONNECTED     15320    
unix  3      [ ]         STREAM     CONNECTED     15294    /tmp/orbit-vivek/linc-85f-0-5b084e5d871ff
unix  3      [ ]         STREAM     CONNECTED     15293    
unix  3      [ ]         STREAM     CONNECTED     15291    /tmp/orbit-vivek/linc-765-0-294f5105485a3
unix  3      [ ]         STREAM     CONNECTED     15290    
unix  3      [ ]         STREAM     CONNECTED     15268    
unix  3      [ ]         STREAM     CONNECTED     15267    
unix  3      [ ]         STREAM     CONNECTED     15265    
unix  3      [ ]         STREAM     CONNECTED     15264    
unix  3      [ ]         STREAM     CONNECTED     15212    
unix  3      [ ]         STREAM     CONNECTED     15211    
unix  3      [ ]         STREAM     CONNECTED     15207    
unix  3      [ ]         STREAM     CONNECTED     15206    
unix  3      [ ]         STREAM     CONNECTED     15292    /tmp/orbit-vivek/linc-85f-0-5b084e5d871ff
unix  3      [ ]         STREAM     CONNECTED     15204    
unix  3      [ ]         STREAM     CONNECTED     15201    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     15200    
unix  3      [ ]         STREAM     CONNECTED     15199    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     15198    
unix  3      [ ]         STREAM     CONNECTED     15194    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     15193    
unix  2      [ ]         DGRAM                    14653    
unix  3      [ ]         SEQPACKET  CONNECTED     14631    
unix  3      [ ]         SEQPACKET  CONNECTED     14630    
unix  3      [ ]         SEQPACKET  CONNECTED     14628    
unix  3      [ ]         SEQPACKET  CONNECTED     14627    
unix  3      [ ]         STREAM     CONNECTED     14525    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     14524    
unix  3      [ ]         STREAM     CONNECTED     14482    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     14481    
unix  3      [ ]         STREAM     CONNECTED     14480    /tmp/orbit-vivek/linc-83b-0-6f8fa23d9c8cf
unix  3      [ ]         STREAM     CONNECTED     14479    
unix  3      [ ]         STREAM     CONNECTED     14478    /tmp/orbit-vivek/linc-765-0-294f5105485a3
unix  3      [ ]         STREAM     CONNECTED     14476    
unix  3      [ ]         STREAM     CONNECTED     14477    /tmp/orbit-vivek/linc-83b-0-6f8fa23d9c8cf
unix  3      [ ]         STREAM     CONNECTED     14465    
unix  3      [ ]         STREAM     CONNECTED     14463    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     14461    
unix  3      [ ]         STREAM     CONNECTED     14460    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14459    
unix  3      [ ]         STREAM     CONNECTED     14455    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14454    
unix  3      [ ]         STREAM     CONNECTED     14357    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14356    
unix  2      [ ]         DGRAM                    14353    
unix  3      [ ]         STREAM     CONNECTED     13910    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13909    
unix  3      [ ]         STREAM     CONNECTED     13908    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13907    
unix  3      [ ]         STREAM     CONNECTED     13901    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     13900    
unix  3      [ ]         STREAM     CONNECTED     13897    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13896    
unix  3      [ ]         STREAM     CONNECTED     13895    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13894    
unix  3      [ ]         STREAM     CONNECTED     13892    /tmp/orbit-vivek/linc-783-0-56863cc043513
unix  3      [ ]         STREAM     CONNECTED     13891    
unix  3      [ ]         STREAM     CONNECTED     13890    /tmp/orbit-vivek/linc-7e6-0-21483fde2d2d7
unix  3      [ ]         STREAM     CONNECTED     13889    
unix  3      [ ]         STREAM     CONNECTED     13882    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13881    
unix  3      [ ]         STREAM     CONNECTED     13878    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13877    
unix  3      [ ]         STREAM     CONNECTED     13870    @/dbus-vfs-daemon/socket-LX9D7KOj
unix  3      [ ]         STREAM     CONNECTED     13868    
unix  3      [ ]         STREAM     CONNECTED     13869    @/dbus-vfs-daemon/socket-wJK2eI9R
unix  3      [ ]         STREAM     CONNECTED     13867    
unix  3      [ ]         STREAM     CONNECTED     13866    @/dbus-vfs-daemon/socket-ByHdTKJp
unix  3      [ ]         STREAM     CONNECTED     13864    
unix  3      [ ]         STREAM     CONNECTED     13865    @/dbus-vfs-daemon/socket-CBNFN5Yf
unix  3      [ ]         STREAM     CONNECTED     13863    
unix  3      [ ]         STREAM     CONNECTED     13851    @/dbus-vfs-daemon/socket-JWeYRmki
unix  3      [ ]         STREAM     CONNECTED     13849    
unix  3      [ ]         STREAM     CONNECTED     13850    @/dbus-vfs-daemon/socket-AjaUSUTZ
unix  3      [ ]         STREAM     CONNECTED     13848    
unix  3      [ ]         STREAM     CONNECTED     13845    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13844    
unix  3      [ ]         STREAM     CONNECTED     13829    @/dbus-vfs-daemon/socket-HRvL7lHx
unix  3      [ ]         STREAM     CONNECTED     13828    
unix  3      [ ]         STREAM     CONNECTED     13827    @/dbus-vfs-daemon/socket-IAj6AT5M
unix  3      [ ]         STREAM     CONNECTED     13826    
unix  3      [ ]         STREAM     CONNECTED     13818    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13817    
unix  3      [ ]         STREAM     CONNECTED     13798    /tmp/orbit-vivek/linc-7e6-0-21483fde2d2d7
unix  3      [ ]         STREAM     CONNECTED     13797    
unix  3      [ ]         STREAM     CONNECTED     13796    /tmp/orbit-vivek/linc-765-0-294f5105485a3
unix  3      [ ]         STREAM     CONNECTED     13795    
unix  3      [ ]         STREAM     CONNECTED     13785    /tmp/orbit-vivek/linc-7e6-0-21483fde2d2d7
unix  3      [ ]         STREAM     CONNECTED     13784    
unix  3      [ ]         STREAM     CONNECTED     13880    /tmp/orbit-vivek/linc-7d3-0-4a118a022d6bf
unix  3      [ ]         STREAM     CONNECTED     13782    
unix  3      [ ]         STREAM     CONNECTED     13779    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13778    
unix  3      [ ]         STREAM     CONNECTED     13781    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     13776    
unix  3      [ ]         STREAM     CONNECTED     13773    /tmp/orbit-vivek/linc-76d-0-2084f184edf67
unix  3      [ ]         STREAM     CONNECTED     13772    
unix  3      [ ]         STREAM     CONNECTED     13770    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13769    
unix  3      [ ]         STREAM     CONNECTED     13768    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13767    
unix  3      [ ]         STREAM     CONNECTED     13766    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13765    
unix  3      [ ]         STREAM     CONNECTED     13783    /tmp/orbit-vivek/linc-7e0-0-3553ba8d6661c
unix  3      [ ]         STREAM     CONNECTED     13764    
unix  3      [ ]         STREAM     CONNECTED     13758    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13757    
unix  2      [ ]         DGRAM                    13752    
unix  3      [ ]         STREAM     CONNECTED     13748    @/dbus-vfs-daemon/socket-3N5ctPEE
unix  3      [ ]         STREAM     CONNECTED     13746    
unix  3      [ ]         STREAM     CONNECTED     13747    @/dbus-vfs-daemon/socket-OK39MgLE
unix  3      [ ]         STREAM     CONNECTED     13745    
unix  3      [ ]         STREAM     CONNECTED     13737    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13736    
unix  3      [ ]         STREAM     CONNECTED     13733    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13732    
unix  3      [ ]         STREAM     CONNECTED     13731    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13730    
unix  3      [ ]         STREAM     CONNECTED     13726    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13725    
unix  3      [ ]         STREAM     CONNECTED     13722    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13721    
unix  3      [ ]         STREAM     CONNECTED     13710    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13709    
unix  3      [ ]         STREAM     CONNECTED     13708    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13707    
unix  3      [ ]         STREAM     CONNECTED     13704    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13703    
unix  3      [ ]         STREAM     CONNECTED     13681    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     13680    
unix  3      [ ]         STREAM     CONNECTED     13679    /tmp/orbit-vivek/linc-783-0-56863cc043513
unix  3      [ ]         STREAM     CONNECTED     13678    
unix  3      [ ]         STREAM     CONNECTED     13677    /tmp/orbit-vivek/linc-7e8-0-50d138f84e7d6
unix  3      [ ]         STREAM     CONNECTED     13676    
unix  3      [ ]         STREAM     CONNECTED     13672    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     13671    
unix  3      [ ]         STREAM     CONNECTED     13670    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13669    
unix  3      [ ]         STREAM     CONNECTED     13665    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13664    
unix  3      [ ]         STREAM     CONNECTED     13659    /tmp/orbit-vivek/linc-7e2-0-f28bce65ba73
unix  3      [ ]         STREAM     CONNECTED     13658    
unix  3      [ ]         STREAM     CONNECTED     13656    /tmp/orbit-vivek/linc-765-0-294f5105485a3
unix  3      [ ]         STREAM     CONNECTED     13655    
unix  3      [ ]         STREAM     CONNECTED     13657    /tmp/orbit-vivek/linc-7e2-0-f28bce65ba73
unix  3      [ ]         STREAM     CONNECTED     13644    
unix  3      [ ]         STREAM     CONNECTED     13641    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     13640    
unix  3      [ ]         STREAM     CONNECTED     13639    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13638    
unix  3      [ ]         STREAM     CONNECTED     13634    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13633    
unix  3      [ ]         STREAM     CONNECTED     13630    /tmp/orbit-vivek/linc-7e8-0-50d138f84e7d6
unix  3      [ ]         STREAM     CONNECTED     13629    
unix  3      [ ]         STREAM     CONNECTED     13628    /tmp/orbit-vivek/linc-765-0-294f5105485a3
unix  3      [ ]         STREAM     CONNECTED     13627    
unix  3      [ ]         STREAM     CONNECTED     13617    /tmp/orbit-vivek/linc-7e8-0-50d138f84e7d6
unix  3      [ ]         STREAM     CONNECTED     13616    
unix  3      [ ]         STREAM     CONNECTED     13613    /tmp/orbit-vivek/linc-76d-0-2084f184edf67
unix  3      [ ]         STREAM     CONNECTED     13612    
unix  3      [ ]         STREAM     CONNECTED     13611    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13610    
unix  3      [ ]         STREAM     CONNECTED     13606    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13605    
unix  3      [ ]         STREAM     CONNECTED     13289    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     13288    
unix  3      [ ]         STREAM     CONNECTED     13287    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     13286    
unix  3      [ ]         STREAM     CONNECTED     13285    /tmp/orbit-vivek/linc-783-0-56863cc043513
unix  3      [ ]         STREAM     CONNECTED     13284    
unix  3      [ ]         STREAM     CONNECTED     13281    @/dbus-vfs-daemon/socket-ulzdrIzr
unix  3      [ ]         STREAM     CONNECTED     13279    
unix  3      [ ]         STREAM     CONNECTED     13280    @/dbus-vfs-daemon/socket-KeXnllpQ
unix  3      [ ]         STREAM     CONNECTED     13278    
unix  3      [ ]         STREAM     CONNECTED     13275    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13274    
unix  3      [ ]         STREAM     CONNECTED     13271    /tmp/orbit-vivek/linc-7ce-0-4a538603ecb38
unix  3      [ ]         STREAM     CONNECTED     13270    
unix  3      [ ]         STREAM     CONNECTED     13272    @/dbus-vfs-daemon/socket-lc1GFBky
unix  3      [ ]         STREAM     CONNECTED     13269    
unix  3      [ ]         STREAM     CONNECTED     13273    @/dbus-vfs-daemon/socket-LaMtpMki
unix  3      [ ]         STREAM     CONNECTED     13268    
unix  3      [ ]         STREAM     CONNECTED     13265    /tmp/orbit-vivek/linc-783-0-56863cc043513
unix  3      [ ]         STREAM     CONNECTED     13264    
unix  3      [ ]         STREAM     CONNECTED     13263    /tmp/orbit-vivek/linc-7cc-0-10465779ecc3a
unix  3      [ ]         STREAM     CONNECTED     13262    
unix  3      [ ]         STREAM     CONNECTED     13261    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13260    
unix  3      [ ]         STREAM     CONNECTED     13257    @/dbus-vfs-daemon/socket-Fg63FAS3
unix  3      [ ]         STREAM     CONNECTED     13255    
unix  3      [ ]         STREAM     CONNECTED     13256    @/dbus-vfs-daemon/socket-5yX72mRX
unix  3      [ ]         STREAM     CONNECTED     13254    
unix  3      [ ]         STREAM     CONNECTED     13248    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13247    
unix  3      [ ]         STREAM     CONNECTED     13244    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13243    
unix  3      [ ]         STREAM     CONNECTED     13226    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13225    
unix  3      [ ]         STREAM     CONNECTED     13224    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13223    
unix  3      [ ]         STREAM     CONNECTED     13222    /tmp/orbit-vivek/linc-7ce-0-4a538603ecb38
unix  3      [ ]         STREAM     CONNECTED     13220    
unix  3      [ ]         STREAM     CONNECTED     13221    /tmp/orbit-vivek/linc-7cc-0-10465779ecc3a
unix  3      [ ]         STREAM     CONNECTED     13219    
unix  3      [ ]         STREAM     CONNECTED     13217    /tmp/orbit-vivek/linc-765-0-294f5105485a3
unix  3      [ ]         STREAM     CONNECTED     13218    /tmp/orbit-vivek/linc-765-0-294f5105485a3
unix  3      [ ]         STREAM     CONNECTED     13216    
unix  3      [ ]         STREAM     CONNECTED     13215    
unix  3      [ ]         STREAM     CONNECTED     13196    /tmp/orbit-vivek/linc-7cc-0-10465779ecc3a
unix  3      [ ]         STREAM     CONNECTED     13195    
unix  3      [ ]         STREAM     CONNECTED     13194    /tmp/orbit-vivek/linc-7ce-0-4a538603ecb38
unix  3      [ ]         STREAM     CONNECTED     13193    
unix  3      [ ]         STREAM     CONNECTED     13190    /tmp/orbit-vivek/linc-76d-0-2084f184edf67
unix  3      [ ]         STREAM     CONNECTED     13189    
unix  3      [ ]         STREAM     CONNECTED     13186    /tmp/orbit-vivek/linc-76d-0-2084f184edf67
unix  3      [ ]         STREAM     CONNECTED     13185    
unix  3      [ ]         STREAM     CONNECTED     13180    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13179    
unix  3      [ ]         STREAM     CONNECTED     13174    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13173    
unix  3      [ ]         STREAM     CONNECTED     13170    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13169    
unix  3      [ ]         STREAM     CONNECTED     13160    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13159    
unix  3      [ ]         STREAM     CONNECTED     13158    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13157    
unix  3      [ ]         STREAM     CONNECTED     13151    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13150    
unix  3      [ ]         STREAM     CONNECTED     13069    /tmp/orbit-vivek/linc-783-0-56863cc043513
unix  3      [ ]         STREAM     CONNECTED     13068    
unix  3      [ ]         STREAM     CONNECTED     13067    /tmp/orbit-vivek/linc-76d-0-2084f184edf67
unix  3      [ ]         STREAM     CONNECTED     13066    
unix  3      [ ]         STREAM     CONNECTED     13065    @/tmp/.ICE-unix/1852
unix  3      [ ]         STREAM     CONNECTED     13064    
unix  3      [ ]         STREAM     CONNECTED     13048    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     13047    
unix  3      [ ]         STREAM     CONNECTED     12999    /tmp/orbit-vivek/linc-788-0-6b9b74e95d7cb
unix  3      [ ]         STREAM     CONNECTED     12998    
unix  3      [ ]         STREAM     CONNECTED     12995    /tmp/orbit-vivek/linc-765-0-294f5105485a3
unix  3      [ ]         STREAM     CONNECTED     12994    
unix  3      [ ]         STREAM     CONNECTED     12979    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12978    
unix  3      [ ]         STREAM     CONNECTED     12977    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12976    
unix  3      [ ]         STREAM     CONNECTED     12975    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12974    
unix  3      [ ]         STREAM     CONNECTED     12973    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12972    
unix  3      [ ]         STREAM     CONNECTED     12970    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12969    
unix  3      [ ]         STREAM     CONNECTED     12965    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12964    
unix  3      [ ]         STREAM     CONNECTED     12963    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12962    
unix  3      [ ]         STREAM     CONNECTED     12961    /tmp/orbit-vivek/linc-7c1-0-20a2db4483c5
unix  3      [ ]         STREAM     CONNECTED     12960    
unix  3      [ ]         STREAM     CONNECTED     12958    /tmp/orbit-vivek/linc-765-0-294f5105485a3
unix  3      [ ]         STREAM     CONNECTED     12957    
unix  3      [ ]         STREAM     CONNECTED     12959    /tmp/orbit-vivek/linc-7c1-0-20a2db4483c5
unix  3      [ ]         STREAM     CONNECTED     12947    
unix  3      [ ]         STREAM     CONNECTED     12944    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     12943    
unix  3      [ ]         STREAM     CONNECTED     12942    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12941    
unix  3      [ ]         STREAM     CONNECTED     12937    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12936    
unix  3      [ ]         STREAM     CONNECTED     12933    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12932    
unix  3      [ ]         STREAM     CONNECTED     12931    @/tmp/.ICE-unix/1852
unix  3      [ ]         STREAM     CONNECTED     12930    
unix  3      [ ]         STREAM     CONNECTED     12868    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12867    
unix  3      [ ]         STREAM     CONNECTED     12863    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12862    
unix  3      [ ]         STREAM     CONNECTED     12851    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12850    
unix  3      [ ]         STREAM     CONNECTED     12845    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12844    
unix  3      [ ]         STREAM     CONNECTED     12839    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12838    
unix  3      [ ]         STREAM     CONNECTED     12837    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12836    
unix  3      [ ]         STREAM     CONNECTED     12829    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12828    
unix  3      [ ]         STREAM     CONNECTED     12826    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12825    
unix  3      [ ]         STREAM     CONNECTED     12765    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12764    
unix  3      [ ]         STREAM     CONNECTED     12763    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12762    
unix  3      [ ]         STREAM     CONNECTED     12761    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12760    
unix  3      [ ]         STREAM     CONNECTED     12759    /tmp/orbit-vivek/linc-777-0-4fe86b142b30
unix  3      [ ]         STREAM     CONNECTED     12758    
unix  3      [ ]         STREAM     CONNECTED     12757    /tmp/orbit-vivek/linc-784-0-af214e8439c7
unix  3      [ ]         STREAM     CONNECTED     12756    
unix  3      [ ]         STREAM     CONNECTED     12755    /tmp/orbit-vivek/linc-765-0-294f5105485a3
unix  3      [ ]         STREAM     CONNECTED     12752    
unix  3      [ ]         STREAM     CONNECTED     12753    /tmp/orbit-vivek/linc-765-0-294f5105485a3
unix  3      [ ]         STREAM     CONNECTED     12750    
unix  3      [ ]         STREAM     CONNECTED     12744    /tmp/orbit-vivek/linc-769-0-28d48c716d7d0
unix  3      [ ]         STREAM     CONNECTED     12743    
unix  3      [ ]         STREAM     CONNECTED     12741    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     12740    
unix  3      [ ]         STREAM     CONNECTED     12738    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12737    
unix  3      [ ]         STREAM     CONNECTED     12727    /home/vivek/.pulse/68ae869a497e97375e64e15c00000009-runtime/native
unix  3      [ ]         STREAM     CONNECTED     12726    
unix  3      [ ]         STREAM     CONNECTED     12705    /tmp/orbit-vivek/linc-796-0-63cd0fda68dd9
unix  3      [ ]         STREAM     CONNECTED     12704    
unix  3      [ ]         STREAM     CONNECTED     12701    /tmp/orbit-vivek/linc-765-0-294f5105485a3
unix  3      [ ]         STREAM     CONNECTED     12700    
unix  3      [ ]         STREAM     CONNECTED     12692    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12691    
unix  3      [ ]         STREAM     CONNECTED     12637    /tmp/orbit-vivek/linc-783-0-56863cc043513
unix  3      [ ]         STREAM     CONNECTED     12636    
unix  3      [ ]         STREAM     CONNECTED     12634    /tmp/orbit-vivek/linc-765-0-294f5105485a3
unix  3      [ ]         STREAM     CONNECTED     12633    
unix  3      [ ]         STREAM     CONNECTED     12623    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12622    
unix  3      [ ]         STREAM     CONNECTED     12621    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12620    
unix  3      [ ]         STREAM     CONNECTED     13002    /tmp/orbit-vivek/linc-782-0-516bee3945d3f
unix  3      [ ]         STREAM     CONNECTED     12604    
unix  3      [ ]         STREAM     CONNECTED     12601    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     12600    
unix  3      [ ]         STREAM     CONNECTED     12579    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12570    
unix  2      [ ]         DGRAM                    12567    
unix  3      [ ]         STREAM     CONNECTED     12561    /tmp/orbit-vivek/linc-73c-0-66f249f24e6a6
unix  3      [ ]         STREAM     CONNECTED     12560    
unix  3      [ ]         STREAM     CONNECTED     12751    /tmp/orbit-vivek/linc-784-0-af214e8439c7
unix  3      [ ]         STREAM     CONNECTED     12559    
unix  3      [ ]         STREAM     CONNECTED     12565    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12550    
unix  3      [ ]         STREAM     CONNECTED     12558    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     12548    
unix  3      [ ]         STREAM     CONNECTED     12551    @/tmp/.ICE-unix/1852
unix  3      [ ]         STREAM     CONNECTED     12547    
unix  3      [ ]         STREAM     CONNECTED     12556    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     12542    
unix  3      [ ]         STREAM     CONNECTED     12635    /tmp/orbit-vivek/linc-783-0-56863cc043513
unix  3      [ ]         STREAM     CONNECTED     12537    
unix  3      [ ]         STREAM     CONNECTED     12533    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     12532    
unix  3      [ ]         STREAM     CONNECTED     12538    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12527    
unix  3      [ ]         STREAM     CONNECTED     12610    /tmp/orbit-vivek/linc-780-0-441f545042c11
unix  3      [ ]         STREAM     CONNECTED     12524    
unix  3      [ ]         STREAM     CONNECTED     12707    /tmp/orbit-vivek/linc-777-0-4fe86b142b30
unix  3      [ ]         STREAM     CONNECTED     12523    
unix  3      [ ]         STREAM     CONNECTED     12525    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12521    
unix  3      [ ]         STREAM     CONNECTED     12522    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     12517    
unix  3      [ ]         STREAM     CONNECTED     12520    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     12514    
unix  3      [ ]         STREAM     CONNECTED     12512    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12506    
unix  3      [ ]         STREAM     CONNECTED     12510    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12498    
unix  3      [ ]         STREAM     CONNECTED     12509    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12497    
unix  3      [ ]         STREAM     CONNECTED     12508    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12496    
unix  3      [ ]         STREAM     CONNECTED     12488    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12487    
unix  3      [ ]         STREAM     CONNECTED     12434    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12433    
unix  3      [ ]         STREAM     CONNECTED     12429    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12428    
unix  3      [ ]         STREAM     CONNECTED     12425    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12424    
unix  3      [ ]         STREAM     CONNECTED     12381    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12380    
unix  3      [ ]         STREAM     CONNECTED     12286    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12285    
unix  3      [ ]         STREAM     CONNECTED     12284    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12281    
unix  3      [ ]         STREAM     CONNECTED     12154    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12153    
unix  3      [ ]         STREAM     CONNECTED     12149    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12148    
unix  3      [ ]         STREAM     CONNECTED     12064    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12063    
unix  3      [ ]         STREAM     CONNECTED     12061    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     12060    
unix  3      [ ]         STREAM     CONNECTED     12055    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12054    
unix  3      [ ]         STREAM     CONNECTED     12053    /tmp/orbit-vivek/linc-76d-0-2084f184edf67
unix  3      [ ]         STREAM     CONNECTED     12052    
unix  3      [ ]         STREAM     CONNECTED     12024    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12023    
unix  3      [ ]         STREAM     CONNECTED     12018    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     12017    
unix  3      [ ]         STREAM     CONNECTED     11971    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11970    
unix  3      [ ]         STREAM     CONNECTED     11969    /tmp/orbit-vivek/linc-766-0-2261f7b37e5e9
unix  3      [ ]         STREAM     CONNECTED     11968    
unix  3      [ ]         STREAM     CONNECTED     11965    /tmp/orbit-vivek/linc-765-0-294f5105485a3
unix  3      [ ]         STREAM     CONNECTED     11964    
unix  3      [ ]         STREAM     CONNECTED     11949    /tmp/orbit-vivek/linc-769-0-28d48c716d7d0
unix  3      [ ]         STREAM     CONNECTED     11948    
unix  3      [ ]         STREAM     CONNECTED     11945    /tmp/orbit-vivek/linc-765-0-294f5105485a3
unix  3      [ ]         STREAM     CONNECTED     11944    
unix  3      [ ]         STREAM     CONNECTED     11930    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     11929    
unix  3      [ ]         STREAM     CONNECTED     11927    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11926    
unix  2      [ ]         DGRAM                    11865    
unix  3      [ ]         STREAM     CONNECTED     11862    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11861    
unix  3      [ ]         STREAM     CONNECTED     11859    /tmp/orbit-vivek/linc-73c-0-66f249f24e6a6
unix  3      [ ]         STREAM     CONNECTED     11858    
unix  3      [ ]         STREAM     CONNECTED     11855    /tmp/orbit-vivek/linc-765-0-294f5105485a3
unix  3      [ ]         STREAM     CONNECTED     11854    
unix  3      [ ]         STREAM     CONNECTED     11850    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11849    
unix  3      [ ]         STREAM     CONNECTED     11639    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     11638    
unix  3      [ ]         STREAM     CONNECTED     11579    @/tmp/dbus-XEWgMVSinR
unix  3      [ ]         STREAM     CONNECTED     11578    
unix  3      [ ]         STREAM     CONNECTED     11576    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11575    
unix  3      [ ]         STREAM     CONNECTED     11572    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11571    
unix  3      [ ]         STREAM     CONNECTED     11570    
unix  3      [ ]         STREAM     CONNECTED     11569    
unix  3      [ ]         STREAM     CONNECTED     11558    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11557    
unix  3      [ ]         STREAM     CONNECTED     11409    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11408    
unix  2      [ ]         DGRAM                    11295    
unix  3      [ ]         STREAM     CONNECTED     11294    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11293    
unix  3      [ ]         DGRAM                    11006    
unix  3      [ ]         DGRAM                    11005    
unix  3      [ ]         STREAM     CONNECTED     10870    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10869    
unix  3      [ ]         STREAM     CONNECTED     10848    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10847    
unix  2      [ ]         DGRAM                    10846    
unix  3      [ ]         STREAM     CONNECTED     10795    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10794    
unix  3      [ ]         STREAM     CONNECTED     10790    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10789    
unix  3      [ ]         STREAM     CONNECTED     10714    @/tmp/gdm-session-WvGESocL
unix  3      [ ]         STREAM     CONNECTED     10713    
unix  3      [ ]         STREAM     CONNECTED     10710    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10709    
unix  3      [ ]         STREAM     CONNECTED     10462    
unix  3      [ ]         STREAM     CONNECTED     10461    
unix  3      [ ]         STREAM     CONNECTED     9955     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9954     
unix  2      [ ]         DGRAM                    9904     
unix  3      [ ]         STREAM     CONNECTED     9856     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9855     
unix  3      [ ]         STREAM     CONNECTED     9643     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9642     
unix  3      [ ]         STREAM     CONNECTED     8745     /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     8744     
unix  3      [ ]         STREAM     CONNECTED     8635     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8634     
unix  2      [ ]         DGRAM                    8602     
unix  2      [ ]         DGRAM                    8587     
unix  2      [ ]         DGRAM                    8585     
unix  3      [ ]         STREAM     CONNECTED     8529     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8528     
unix  3      [ ]         STREAM     CONNECTED     8482     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8481     
unix  2      [ ]         DGRAM                    8480     
unix  3      [ ]         STREAM     CONNECTED     8440     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8439     
unix  3      [ ]         STREAM     CONNECTED     8356     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8355     
unix  2      [ ]         DGRAM                    8354     
unix  3      [ ]         STREAM     CONNECTED     8351     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8350     
unix  3      [ ]         STREAM     CONNECTED     8328     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8326     
unix  3      [ ]         STREAM     CONNECTED     8320     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8319     
unix  2      [ ]         DGRAM                    8315     
unix  3      [ ]         STREAM     CONNECTED     8185     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8184     
unix  3      [ ]         STREAM     CONNECTED     8130     
unix  3      [ ]         STREAM     CONNECTED     8129     
unix  2      [ ]         DGRAM                    8126     
unix  3      [ ]         STREAM     CONNECTED     7931     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7930     
unix  2      [ ]         DGRAM                    7882     
unix  3      [ ]         STREAM     CONNECTED     7878     
unix  3      [ ]         STREAM     CONNECTED     7877     
unix  3      [ ]         STREAM     CONNECTED     7879     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7821     
unix  3      [ ]         DGRAM                    6375     
unix  3      [ ]         DGRAM                    6374     
unix  3      [ ]         STREAM     CONNECTED     6317     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     6316     


pls somebody help bcos it has been really aweful job to get the output of the command else weneveri was giving the command the whole terminal was getting filled with the output and as i was unable to scroll up till the point wre i gave the command i dont know y the scroll bar wasnt going upo,it was difficult to get the entire output 4 u ppl...

---

### Post by vivek.pandey on 2011-02-11
hi everyone

my problem hasnt solved yet..so please help

---

### Post by vivek.pandey on 2011-02-11
???

---

### Post by vivek.pandey on 2011-02-11
???

---

### Post by jimwill on 2011-02-11
The only thing I might be able to help you out with is capturing the long output.
You can redirect the output to a file with the > redirect command.
netstat -a > file.txt
then you can use a text editor to look at it or whatever you need. (You can also remove personal info while in the editor - replace personal info with something else)

hope you get the rest working. 
Personally I used the ubuntu server setup on my test server, no gui so everthing is done via command line. But also installed webmin which lets me do a lot of things on it from my other computer. (which is no problem since the server has no display/keyboard/mouse!!!)

---

