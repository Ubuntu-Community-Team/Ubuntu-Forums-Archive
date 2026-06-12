---
title: "Questions before changing to Ubuntu (from MS)"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by oingk on 2010-02-17
Hi everyone. I have been using windows XP for a long time and lately been dual booting with Ubuntu 9.10, though I can't say I have used it a lot yet since until now I had to do most things on Windows. I am now thinking of changing to Ubuntu only, but first I have some questions. There are a bit too many, but feel free to only answer as many as you can:  1] With Ubuntu, do I have to periodically update the drivers, and how do I do this?  2] With Ubuntu, do I have to periodically run a "Checkdisk" before startup to check the hard-disk for any issues, like in Windows? How?  3] Do I have to periodically "defragment" my hard-drive like in Windows? How?  4] Will I need a firewall? An antivirus? An antispyware/malware/adware?  5] Would a "CCleaner"-like program for Linux be of any use? Which one do you suggest?  6] Can I disable startup processes and other services like I do in Windows to make the machine run faster?  7] I want the opportunity to still run some Windows applications that I couldn't find linux-alternatives for. I've found info that I can do this with Wine, is that correct and is it advisable by you?  8] Are there any specific common issues that a new Ubuntu user might run into that I should know of? For example are there any serious cautions to stop me from messing up badly?  Sorry for the lenghty message :) Thanks.

---

### Post by oingk on 2010-02-17
Oh no I'm sorry for the format of this message, this is not how I've written it, don't know what went wrong.

---

### Post by jfr1tz on 2010-02-17
> **oingk said:**
> Hi everyone. I have been using windows XP for a long time and lately been dual booting with Ubuntu 9.10, though I can't say I have used it a lot yet since until now I had to do most things on Windows. 

I am now thinking of changing to Ubuntu only, but first I have some questions. There are a bit too many, but feel free to only answer as many as you can:  

1] With Ubuntu, do I have to periodically update the drivers, and how do I do this?  

2] With Ubuntu, do I have to periodically run a "Checkdisk" before startup to check the hard-disk for any issues, like in Windows? How?  

3] Do I have to periodically "defragment" my hard-drive like in Windows? How?  

4] Will I need a firewall? An antivirus? An antispyware/malware/adware?  

5] Would a "CCleaner"-like program for Linux be of any use? Which one do you suggest?  

6] Can I disable startup processes and other services like I do in Windows to make the machine run faster?  

7] I want the opportunity to still run some Windows applications that I couldn't find linux-alternatives for. I've found info that I can do this with Wine, is that correct and is it advisable by you?  

8] Are there any specific common issues that a new Ubuntu user might run into that I should know of? For example are there any serious cautions to stop me from messing up badly?  Sorry for the lenghty message :) Thanks.

iz called enter, to the right(reading your questions now)

1 in most cases ubuntu takes care of this through the update process
2 it periodically checks your disk automatically, no intervention required
3 no the default filesystem does not need defragmenting.
4 firewall maybe if you need to filter traffic to certain services but not by default. for the rest no, but you may want to scan shared folders for virusses if these are used by windows systems. 
5 no registry no problem (so no)
6 yeah there are the system services and services that start per user session, managed via a gui in the system menu.
7 wine, yes, sometimes works, winehq.com has info on what and how applications work with wine.
8 dont know :)

---

### Post by oingk on 2010-02-17
Hehe thanks, I know about enter but somehow my message got automatically messed up, no worries.

---

### Post by halitech on 2010-02-17
1. no

2. no

3. no

4. no

5. no

6. yes

7. correct although I haven't found any that there is not a native app to replace it

8. video and wireless drivers

---

### Post by kanikilu on 2010-02-17
> **oingk said:**
>  1] With Ubuntu, do I have to periodically update the drivers, and how do I do this?Not really...unless you get new hardware or *want* to get the latest and greatest drivers for your 3D graphics card (for example). If it's working, though, no need to try to fix what's not broken.

> 2] With Ubuntu, do I have to periodically run a "Checkdisk" before startup to check the hard-disk for any issues, like in Windows? How? See "fsck". I believe by default it will check a filesystem every X reboots. I want to say it's every 30, but someone correct me if I'm wrong.

> 3] Do I have to periodically "defragment" my hard-drive like in Windows? No.

> 4] Will I need a firewall? An antivirus? An antispyware/malware/adware? If you are running services such as a web server, then a firewall should be used. If just a home workstation, it's probably not needed. Antivirus is not particularly necessary, but has been discussed in great length on the forums in the past, so just do a search if you want.

> 5] Would a "CCleaner"-like program for Linux be of any use? Which one do you suggest? Kind of depends on what functionality of CCleaner you are referring to. Here's a guide on how to clean up unnecessary "junk" files: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

> 6] Can I disable startup processes and other services like I do in Windows to make the machine run faster?

Yes. It kind of depends on the DE and what you are trying to disable, but in Gnome, a good place to start is System ->  Preferences -> Startup Applications

> 7] I want the opportunity to still run some Windows applications that I couldn't find linux-alternatives for. I've found info that I can do this with Wine, is that correct and is it advisable by you? Wine will work for some things, but in my experience, I've learned not to count on it to work flawlessly. If you absolutely need something to run in Linux without dual-booting, virtualization (VMWare or VirtualBox) is pretty much your only option. Although that's not necessarily ideal, since you are basically running a full-blown version of Windows under Linux, so it does take some system resources...

> 8] Are there any specific common issues that a new Ubuntu user might run into that I should know of? For example are there any serious cautions to stop me from messing up badly?  Sorry for the lenghty message :) Thanks. Don't make the mistake of not backing up important data/files before installing Ubuntu...should be obvious, but you'd be surprised how many people come to the forums wondering where Windows and all their files and programs have "gone" :rolleyes:

---

### Post by colobix on 2010-02-17
Have you really been using Ubuntu? Because you asked about things like spyware and firewall etc.
OK, theres no such thing as virus, spyware or anything like that with linux.
Most drivers are already installed or will be installed after new updates.
UPdates are happening automaticly and you can even set them to be installed in the background if you want to.
THere is actually a firewall that starts at startup. this firewall is to close open ports.
The reason why you dont have to worry about disk problems and viruses, spywares etc. like you have to in windows is because of how the system works.
YOu know, to install, uninstall or any other system things you gonna have to insert your password.
In windows you are always logged in as the admin which is a risk in itself.
If ubuntu doesnt support your hardware for some reason or if you are having trouble with anything, just come to the forums and 100s of people will gladly help you out.

YOu would never get that kind of service with windows.

---

### Post by achase79 on 2010-02-17
1) If you use the drivers in the repositories, the update manager

2) Regularly (on a per startup basis) fsck is run automatically upon startup

3) Ext2 and Ext3 don't need defraging, supposably ext4 will but I havn't worked with it enough yet

4) Firewall is built in.  Antivirus programs are for only Windows viruses.  There are no malware/adware programs because it is very difficult to pass on vulnerablilities in open source software because everyone can see the code.

5) "sudo apt-get autoremove" will clean up the package manager cache.  And some automation scripts can find old files and clean them.

6) System->Settings->Sessions & Startup can add or remove startup items.  You can also remove services in System->Settings->Services.

7) Check out [http://winehq.org]("http://winehq.org").

8) Check the stickies in this forum

---

### Post by oingk on 2010-02-17
Thanks very much guys :)

---

### Post by oingk on 2010-03-08
I marked this as "Solved", but now another question came to me.

With Ubuntu, should I still worry about threats based on scripts? So that would NoScript firefox addon be of any value, for example?

---

