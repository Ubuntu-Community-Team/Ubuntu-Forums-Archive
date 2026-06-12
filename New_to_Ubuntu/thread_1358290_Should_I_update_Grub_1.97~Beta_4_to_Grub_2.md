---
title: "Should I update Grub 1.97~Beta 4 to Grub 2?"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by mikodo on 2009-12-18
Hello Everyone:

I see a lot of people talking about Grub 2. I, in Karmic I have Grub 1.97 ~Beta 4. Should I be updating it to Grub 2? If so, is it safe to do so? If you folks think I should, I'll look around, to find how to do it.

Thanks.

---

### Post by philinux on 2009-12-18
I reckon 1.97 , not beta, is the latest verison at the moment.

```
grub-install -v
grub-install (GNU GRUB 1.97)
```

---

### Post by mikodo on 2009-12-18
> **philinux said:**
> I reckon 1.97 , not beta, is the latest verison at the moment.

```
grub-install -v
grub-install (GNU GRUB 1.97)
```

Thanks Phil,

Here is what I got when I ran that code:

mikodo@mikodo-desktop:~$ sudo grub-install -v
grub-install (GNU GRUB 1.97~beta4)
mikodo@mikodo-desktop:~$ grub-install (GNU GRUB 1.97)
bash: syntax error near unexpected token `GNU'
mikodo@mikodo-desktop:~$ 


I haven't gone to grub yet to see it it changed, presumably it didn't.


Mike

---

### Post by philinux on 2009-12-18
Try updating your system. Either use the code below or use update manager.

```
sudo apt-get update && sudo apt-get upgrade
```

"grub-install -v" just shows the version number you are using. Which for you is still beta 4. It works so no real problem there.

---

### Post by mikodo on 2009-12-18
> **philinux said:**
> Try updating your system. Either use the code below or use update manager.

```
sudo apt-get update && sudo apt-get upgrade
```

"grub-install -v" just shows the version number you are using. Which for you is still beta 4. It works so no real problem there.

ran the code; I just want to enter the response to have available to you in case you see a problem.


mikodo@mikodo-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for mikodo: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release [44.1kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages [116kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages [14B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources [35.9kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources [14B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages [68.3kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources [16.2kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages [5987B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources [3414B]
Fetched 290kB in 2s (99.2kB/s)                     
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  rsyslog upstart
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 788kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main upstart 0.6.3-11 [511kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main rsyslog 4.2.0-2ubuntu5.1 [277kB]
Fetched 788kB in 4s (194kB/s)   
(Reading database ... 167553 files and directories currently installed.)
Preparing to replace upstart 0.6.3-10 (using .../upstart_0.6.3-11_i386.deb) ...
Unpacking replacement upstart ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up upstart (0.6.3-11) ...
Installing new version of config file /etc/init/rc-sysinit.conf ...

(Reading database ... 167553 files and directories currently installed.)
Preparing to replace rsyslog 4.2.0-2ubuntu5 (using .../rsyslog_4.2.0-2ubuntu5.1_i386.deb) ...
Unpacking replacement rsyslog ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up rsyslog (4.2.0-2ubuntu5.1) ...
Installing new version of config file /etc/rsyslog.conf ...
rsyslog start/running, process 2528

mikodo@mikodo-desktop:~$ 


Thanks. I rebooted, as indicated I should, and still see Grub 1.97~Beta4 in loader.

---

### Post by philinux on 2009-12-18
My apologies. I was running lucid. ;)

Karmic is still on beta4 for now. Lucid is running the release.

No worries then. I'm sure an update will get through sometime. Meanwhile leave well alone.

---

### Post by mikodo on 2009-12-18
> **philinux said:**
> My apologies. I was running lucid. ;)

Karmic is still on beta4 for now. Lucid is running the release.

No worries then. I'm sure an update will get through sometime. Meanwhile leave well alone.

No worries; You answered my question, and I'll be certain to leave well enough alone. 

Thanks,

Mike

---

### Post by kansasnoob on 2009-12-18
I see this is already marked solved but just FYI, I filed a bug report partly requesting these packages be upgraded in Karmic and this is the reply:

> Colin Watson  wrote on 2009-12-07:  	  #4

By the way, we're not going to do a full update in karmic-proposed; the changes are just too big and very many of them are not required in a stable release. If you want to help to identify individual isolated changes that are needed, feel free (in separate bugs).


[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457)

---

### Post by llawwehttam on 2009-12-18
My policy is and always has been 'if it ain't broke don't fix it'

---

### Post by mikodo on 2009-12-18
> **llawwehttam said:**
> My policy is and always has been 'if it ain't broke don't fix it'


I will start adopting this. I was thinking that it might help resolve some issues I was having with disappearing panels I have at times. I started a thread on this a little while ago.

I heard you, and it is very good advice.

Thanks,

Mike

---

### Post by presence1960 on 2009-12-18
> **mikodo said:**
> I will start adopting this. I was thinking that it might help resolve some issues I was having with disappearing panels I have at times. I started a thread on this a little while ago.

I heard you, and it is very good advice.

Thanks,

Mike

GRUB has nothing to do with your panels. GRUB usually resides on the MBR of a hard disk and it is a bootloader. What it does when it boots is it points to a directory which has your boot files and gives you the menu to choose which OS you want to boot provided you have more than one OS on your machine. If you only have one OS it boots that OS immediately. Once the OS boots GRUB's work is finished and has no effect on whatever OS you chose to run.

---

### Post by mikodo on 2009-12-18
> **presence1960 said:**
> GRUB has nothing to do with your panels. GRUB usually resides on the MBR of a hard disk and it is a bootloader. What it does when it boots is it points to a directory which has your boot files and gives you the menu to choose which OS you want to boot provided you have more than one OS on your machine. If you only have one OS it boots that OS immediately. Once the OS boots GRUB's work is finished and has no effect on whatever OS you chose to run.

Thanks for the information.

Mike

---

