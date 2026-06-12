---
title: "Adobe Flash Player Issues"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by phosphide on 2009-02-04
I have tried downloading Adobe Flash Player 10, however I am running into issues. 

I just booted Linux so I have no previous version. Check. 
I downloaded the .deb file from the Adobe website. Check. 
When I run Package Installer I get error: Wrong Architecture 'i386' My processor is an intel t7100 x86, 4 gigs of ram, and dual booting vista and linux. I'm fairly new at this and am stilling working out the Unix commands. Any suggestions? Thanks in advance.

---

### Post by petervk on 2009-02-04
Can you post the name of the package you downloaded and the version of the linux kernel you are running?

You can get the exact version of the linux kernel by running the
```
uname -r
```
command in a terminal.

---

### Post by RomeReactor on 2009-02-04
Hi. Also try:
```
uname -m
```
and post back the result. As far as I could find, your processor is 64-bit capable. Are you sure you're running Ubuntu 32-bit?

---

### Post by stderr on 2009-02-04
I'm not 100% sure about 64-bit, but I'm 99% sure it also exists in repos for it too. If it does, you should install from Ubuntu repos rather than grabbing a package off the web, as from repos it will get automatically updated. If you install from downloading a random .deb, you will have to update it manually, which is far, far more difficult! Always install from repos if you can.

Try:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by stchman on 2009-02-04
> **phosphide said:**
> I have tried downloading Adobe Flash Player 10, however I am running into issues. 

I just booted Linux so I have no previous version. Check. 
I downloaded the .deb file from the Adobe website. Check. 
When I run Package Installer I get error: Wrong Architecture 'i386' My processor is an intel t7100 x86, 4 gigs of ram, and dual booting vista and linux. I'm fairly new at this and am stilling working out the Unix commands. Any suggestions? Thanks in advance.

Sounds like you are running the 64 bit version of Ubuntu.  The t7100 is indeed a Core 2 processor capable of supporting 64 bit OS.  I have a tutorial that will install the 64 bit flash on your system.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

Please only use this if you are sure you have 64 bit Ubuntu.  The way to verify is to open a terminal and type:

```
uname -a
```

If you have 64 bit the line will end with x86_64.

---

### Post by phosphide on 2009-02-04
> **stchman said:**
> Sounds like you are running the 64 bit version of Ubuntu.  The t7100 is indeed a Core 2 processor capable of supporting 64 bit OS.  I have a tutorial that will install the 64 bit flash on your system.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

Please only use this if you are sure you have 64 bit Ubuntu.  The way to verify is to open a terminal and type:

```
uname -a
```

If you have 64 bit the line will end with x86_64.

Yes, I am running 64 bit Ubuntu and I followed the process in the link and it is now working. I appreciate the help. Thanks to the previous posters for their help as well.

[QUOTE=sdterr]I'm not 100% sure about 64-bit, but I'm 99% sure it also exists in repos for it too. If it does, you should install from Ubuntu repos rather than grabbing a package off the web, as from repos it will get automatically updated. If you install from downloading a random .deb, you will have to update it manually, which is far, far more difficult! Always install from repos if you can[/QUOTE]
You know, I actually tried doing that except I couldn't figure it out very well. I tried doing the add and remove programs too. That's all part of being a newb.

---

