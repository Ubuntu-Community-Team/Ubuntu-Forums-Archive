---
title: "Cannot move slider in flash videos."
date: 2009-10-29
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-10-29
Hi everyone,

I can no longer adjust the slider that moves the time progress in flash videos. When I click and drag, nothing happens. I installed flash using this webpage:
[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-150888](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-150888)

Can anyone help?

Thanks!

EDIT: I also have no fullscreen flash capability

---

### Post by clhsharky on 2009-10-29
HI

That link shows older flash, try this one.
[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

---

### Post by asuastrophysics on 2009-10-30
That script installed successfully:
```
jjake@girdy-laptop:~$ su
Password: 
root@girdy-laptop:/home/jake# '/home/jake/Desktop/Get64bitFlash' 
mkdir: cannot create directory `/tmp/pluginstall': File exists

 This script is used to setup the Flash 10 Alpha. 
 By entering yes below you acknowlage that you 
 are installing development software and you 
 will file bug reports with Adobe for every 
 problem you incounter.

 Do you agree? yes or no : 
(please type the whole word in lower case letters)yes
Flash installing.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--2009-10-30 01:01:02--  http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
Resolving download.macromedia.com... 96.17.51.191
Connecting to download.macromedia.com|96.17.51.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3727613 (3.6M) [application/x-gzip]
Saving to: `libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz.2'

100%[======================================>] 3,727,613    770K/s   in 4.8s    

2009-10-30 01:01:07 (752 KB/s) - `libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz.2' saved [3727613/3727613]

libflashplayer.so
Please restart Firefox to enable Flash
root@girdy-laptop:/home/jake# 

```

Now every video I want to view just shows a black screen. How do I fix this?

---

### Post by asuastrophysics on 2009-10-30
If I could still download libflashplayer.so and put it in the plugins directory, none of this would be an issue. It's all these stupid script files that people create. They're ruining my file system. Now I have to track down every file the script made and remove them, and then install flash the old fashioned way.

I don't see why 5 years after Ubuntu came out we still don't have a plugin in Firefox to do this.

---

