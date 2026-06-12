---
title: "Firefox/Flash virus?"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by h2z on 2009-12-11
I want to install ubuntu on my mom's pc, she's not a complete newbie when it comes to computers, but she's not as paranoid as myself when it comes to surfing the web so I always end up cleaning her windows machine. I would be clueless if such a virus\exploit would hit her ubuntu machine. Is there something to do to prevent firefox\flash based threats from emerging? or removing them if necessary?

---

### Post by JamesParnell on 2009-12-11
Unless you share files to and from windows machines, virus software isnt really needed at all. But still, if you want that added security, download clam antivirus
```
sudo apt-get install nautilus-clamscan

```
is the code for the install i think


EDIT: i'm about to run it myself to find out :D
EDIT AGAIN: scratch that, it probably worked but its not in my menu so it fails :P

---

### Post by wangsuda on 2009-12-11
There are two add ons for Firefox that are excellent: adblock plus (blocks ads) and noscript (blocks all sorts of evil). I find they make page loading very fast. As far as viruses go, most viruses are written for Windows based machines. they won't affect (in a negative way) a Linux based machine.

---

### Post by h2z on 2009-12-11
I thought the whole point in using ubuntu is to eliminate the need for an antivirus (I dont use one on my pc...). Is there a way to make my mom run in a very limited user (even more limited than the normal user)? All of the maintenance will be made my myself and she will not be installing anything on her own.

---

### Post by wangsuda on 2009-12-11
> **h2z said:**
> Is there a way to make my mom run in a very limited user (even more limited than the normal user)? All of the maintenance will be made my myself and she will not be installing anything on her own.There's really no point, is there? She won't be getting viruses thanks to a Linux kernel. If you want to set up a limited use user, go to system>administration>users and groups.

---

### Post by cartisdm on 2009-12-11
> **wangsuda said:**
> There are two add ons for Firefox that are excellent: adblock plus (blocks ads) and noscript (blocks all sorts of evil). I find they make page loading very fast. As far as viruses go, most viruses are written for Windows based machines. they won't affect (in a negative way) a Linux based machine.

+1  These are always the first two add-ons I install after a format

---

### Post by Cuco3 on 2009-12-11
I haven't tried it yet, but I'd just create a new account and disable all user privileges except "Capture TV/Use 3D Acceleration", "Configure Printers", and "Use CD-ROM drives". You might even be able to disable all of them and it still might work. You have to try it out.

---

### Post by Yvan300 on 2009-12-11
Well unless your mother knows the root password, she is a limited user. The most you can do without the root password is view system files. You can't install any programs or anything.

---

