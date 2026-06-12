---
title: "Installing Twhirl in Ubuntu 8.10 64-bit"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by halovivek on 2009-02-04
I have followed the [link]("http://www.jigsawboys.com/2008/10/10/how-to-install-twhirl-on-ubuntu/") and tried to install twhirl.
i could install adobe installer. 
but i could not find how to move more. i am posting the results below. need help more.

result from terminal:-

gurudheva@gurudheva-laptop:~$ cd ~/Desktop
gurudheva@gurudheva-laptop:~/Desktop$ wget [http://download.macromedia.com/pub/labs/air/linux/adobeair_linux_a1_033108.bin](http://download.macromedia.com/pub/labs/air/linux/adobeair_linux_a1_033108.bin)
--2009-02-04 11:40:45--  [http://download.macromedia.com/pub/labs/air/linux/adobeair_linux_a1_033108.bin](http://download.macromedia.com/pub/labs/air/linux/adobeair_linux_a1_033108.bin)
Resolving download.macromedia.com... 88.221.39.191
Connecting to download.macromedia.com|88.221.39.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15847512 (15M) [application/x-macbinary]
Saving to: `adobeair_linux_a1_033108.bin'

100%[======================================>] 15,847,512  5.75M/s   in 2.6s    

2009-02-04 11:40:48 (5.75 MB/s) - `adobeair_linux_a1_033108.bin' saved [15847512/15847512]

gurudheva@gurudheva-laptop:~/Desktop$ wget [http://www.twhirl.org/files/twhirl-0.8.air](http://www.twhirl.org/files/twhirl-0.8.air)
--2009-02-04 11:40:57--  [http://www.twhirl.org/files/twhirl-0.8.air](http://www.twhirl.org/files/twhirl-0.8.air)
Resolving [www.twhirl.org](www.twhirl.org)... 64.13.232.236
Connecting to [www.twhirl.org|64.13.232.236|:80](www.twhirl.org|64.13.232.236|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 821082 (802K) [application/vnd.adobe.air-application-installer-package+zip]
Saving to: `twhirl-0.8.air'

100%[======================================>] 821,082      248K/s   in 3.2s    

2009-02-04 11:41:00 (248 KB/s) - `twhirl-0.8.air' saved [821082/821082]

gurudheva@gurudheva-laptop:~/Desktop$ chmod +x adobeair_linux_a1_033108.bin
gurudheva@gurudheva-laptop:~/Desktop$ sudo ./adobeair_linux_a1_033108.bin
[sudo] password for gurudheva: 
gurudheva@gurudheva-laptop:~/Desktop$ 
gurudheva@gurudheva-laptop:~/Desktop$ ./adobeair_linux_a1_033108.bin
gurudheva@gurudheva-laptop:~/Desktop$ sudo su
root@gurudheva-laptop:/home/gurudheva/Desktop# 
root@gurudheva-laptop:/home/gurudheva/Desktop# ./adobeair_linux_a1_033108.bin
root@gurudheva-laptop:/home/gurudheva/Desktop# chmod +x  adobeair_linux_a1_033108.bin
root@gurudheva-laptop:/home/gurudheva/Desktop# ./adobeair_linux_a1_033108.bin
root@gurudheva-laptop:/home/gurudheva/Desktop# sudo ./AdobeAIRInstaller.bin
root@gurudheva-laptop:/home/gurudheva/Desktop# wget [http://www.twhirl.org/files/twhirl-0.8.7-air11.air](http://www.twhirl.org/files/twhirl-0.8.7-air11.air)
--2009-02-04 11:45:41--  [http://www.twhirl.org/files/twhirl-0.8.7-air11.air](http://www.twhirl.org/files/twhirl-0.8.7-air11.air)
Resolving [www.twhirl.org](www.twhirl.org)... 64.13.232.236
Connecting to [www.twhirl.org|64.13.232.236|:80](www.twhirl.org|64.13.232.236|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1020502 (997K) [application/vnd.adobe.air-application-installer-package+zip]
Saving to: `twhirl-0.8.7-air11.air'

100%[======================================>] 1,020,502    282K/s   in 3.5s    

2009-02-04 11:45:45 (282 KB/s) - `twhirl-0.8.7-air11.air' saved [1020502/1020502]

root@gurudheva-laptop:/home/gurudheva/Desktop# /opt/Adobe\ AIR/Versions/1.0/airappinstaller
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
Segmentation fault
root@gurudheva-laptop:/home/gurudheva/Desktop# /opt/Adobe\ AIR/Versions/1.0/airappinstaller
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
Segmentation fault
root@gurudheva-laptop:/home/gurudheva/Desktop#

---

### Post by halovivek on 2009-02-04
Hallo some one help me please?
or i have to BUMP it?

---

### Post by halovivek on 2009-02-05
Bump ...

---

### Post by ymk on 2009-02-06
is your Adobe Air installed now? 

If it is just go [http://www.twhirl.org/project/twhirl](http://www.twhirl.org/project/twhirl) and download Twirl there, and save/open with Air.

---

### Post by halovivek on 2009-02-06
> **ymk said:**
> is your Adobe Air installed now? 

If it is just go [http://www.twhirl.org/project/twhirl](http://www.twhirl.org/project/twhirl) and download Twirl there, and save/open with Air.

hi
i have tried to open in adobe air. it is not getting installed. i dont know what is the problem.

---

### Post by ymk on 2009-02-06
Thats about the limit of experience on this I'm affraid. I did run Tweet deck with no problems you could try that instead.

Only other sugestion would be start afresh, uninstall Air then start again.

---

### Post by ronnoc on 2009-03-11
Hi all. I was running Tweet Deck on Kubuntu 8.04 but have since moved to Xubuntu 8.10 and installed both Air and Tweet Deck. It appears to have installed correctly, however when i open it TD never fully loads. 

Not sure if this is related or not but thought I'd pass on that there might be some issue w air for Linux and Ubuntu 8.10...

---

### Post by Technoviking on 2009-03-11
[http://ubuntuforums.org/showthread.php?t=1051402](http://ubuntuforums.org/showthread.php?t=1051402)

---

