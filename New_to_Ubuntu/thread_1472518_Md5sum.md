---
title: "Md5sum"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by baldylocks on 2010-05-04
Ok I am trying to generate a boot cd of Ubuntu to salvage an old XP laptop.

Have downloaded Ubuntu-10.04-desktop-i386.iso using google chrome onto my new windows 7 machine.

I now want to MD5Sum the file to check it is ok before I burn but I am LOST as to how to do this in win 7- I'm a total virgin at this sort of stuff please help/advise. Ta!

---

### Post by xumuk37 on 2010-05-04
```
md5sum /path/to/file.ISO
```


something like this... 

```
root@lap:/home/xumuk# md5sum /home/xumuk/files/ubuntu-10.04-desktop-amd64.iso 
3e0f72becd63cad79bf784ac2b34b448  /home/xumuk/files/ubuntu-10.04-desktop-amd64.iso
root@lap:/home/xumuk#
```

---

### Post by sunk8 on 2010-05-04
> **baldylocks said:**
> Ok I am trying to generate a boot cd of Ubuntu to salvage an old XP laptop.

Have downloaded Ubuntu-10.04-desktop-i386.iso using google chrome onto my new windows 7 machine.

I now want to MD5Sum the file to check it is ok before I burn but I am LOST as to how to do this in win 7- I'm a total virgin at this sort of stuff please help/advise. Ta!

Before u post on the forums, please search in the community documentation...
Chk this out:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by baldylocks on 2010-05-04
Yeah i found that but as i am a total beginner it lost me...

is it telling me to go into the root directory to check a download????

---

### Post by BitJunkie on 2010-05-04
Toward to the bottom of the HowTo page provided by sunk8, there is a section called "MD5SUM on Windows". That should get you what you need on Windows.

---

### Post by dizmayed on 2010-05-04
Baldylocks:

Here's another option:

winmd5sum is a small app with <simple> interface. 

[http://www.softpedia.com/progScreenshots/winMdSum-Screenshot-23968.html](http://www.softpedia.com/progScreenshots/winMdSum-Screenshot-23968.html)

I use it with WinXP but the documentation says it's compatible with WinVista and 7.

cheers,

diz

---

