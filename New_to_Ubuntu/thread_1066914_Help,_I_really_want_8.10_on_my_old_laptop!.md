---
title: "Help, I really want 8.10 on my old laptop!"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by frikki on 2009-02-11
Has anyone installed Ubuntu on a T30? I have tried installing it on two T30's and I have the same problem on both, if I enable only the CD drive as a boot device to see the error it says:

PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Intel Boot Agent.
Operating System not found

I have the Ubuntu 8.10 CD and I am running latest firmware version on one of the T30 and an older one on the other T30. Both behave in same manner. I have installed Debian without problem (until realizing wifi problems) and I have tried the 8.10 CD in my T43 and it works fine there.

Thanks.

---

### Post by Fire_Chief on 2009-02-11
You may need to try an older version of Ubuntu (7.04 or maybe even 6.06). If the system will recognize and install it, then you can do an upgrade to 8.10 from within the running OS.

Cheers!

---

### Post by snowpine on 2009-02-11
> **Fire_Chief said:**
> You may need to try an older version of Ubuntu (7.04 or maybe even 6.06). If the system will recognize and install it, then you can do an upgrade to 8.10 from within the running OS.


Bad advice. If you install 7.04 and try to upgrade, you will get an error message, as 7.04 has reached its end of life and is no longer supported. 

frikki, I had a similar problem with my old Dell laptop, and the solution in my case was to add all_generic_ide to my boot options. Not sure if that advice applies in your case. But, there are a lot of Thinkpad users here on the forums, so keep looking and I think you'll find your answer. Good luck!

---

### Post by kansasnoob on 2009-02-11
> **Fire_Chief said:**
> You may need to try an older version of Ubuntu (7.04 or maybe even 6.06). If the system will recognize and install it, then you can do an upgrade to 8.10 from within the running OS.

Cheers!

Well, 6.06 will upgrade directly to 8.04 because they're both LTS, but in order to upgrade 7.04 you'd have to upgrade to 7.10, and then 8.04. Since 7.04 is no longer supported that would be shaky at best!

I'm curious what the system specs are? Especially cpu and RAM?

---

### Post by icanfly0307 on 2009-02-11
> **frikki said:**
> 
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Intel Boot Agent.
Operating System not found 

Basically, your laptop is trying to boot from the network (ie from the ethernet cable via PXE). I don't think your CD/DVD Drive is set as a boot device. And I'm guessing that your hard drive is empty. That's why your lappy trys to boot from the network and then jumps to the hard drive where it can't find any os.

Try going into the BIOS. It should have boot device settings in there. Set the CD Drive as the first boot device, restart the computer with the UbuntuCD in and it should work. Hope this helps.

---

### Post by LowSky on 2009-02-11
A t30 may run Xubuntu but a little slow, you need at least 256MB of RAM to run any version of Ubutnu (384MB is reccomended)
Other issues might arise due to the machines age, like APCI settings

Also Debian is the backbone of Ubuntu, so any issues you had with Debian you may have with Ubuntu, or can be solved by using any solutions that the Ubuntu people came up with.

---

### Post by frikki on 2009-02-11
Thanks all.

icanfly0307: I have of course set my BIOS to boot from CD, but I know now that the messages I get are from trying to boot from the the network.  I disabled everything but the CD-drive and then I get only "Operating System not found".  The computer turns the CD but does not want to run the disk

kansasnoob: The T30's are 2366 family, one is R6G ([http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=2366R6G)it](http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=2366R6G)it) has 256mb though, one slot is broken. The other is 1,6mhz and has 512mb.

I will try to write the CD again, maybe check out some other version, this does not make sense though.

---

### Post by Coreigh on 2009-02-11
This page offers several methods of installing Ubuntu including without a CD:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

One of them may prove useful to you.

---

### Post by LowSky on 2009-02-11
Sounds like you made a bad CD, remeber you cant just place the file onto a disk, it need to be made corretly.

here is a decent iso buring program
[http://www.magiciso.com/tutorials/miso-burnwin.htm](http://www.magiciso.com/tutorials/miso-burnwin.htm)

---

### Post by kansasnoob on 2009-02-11
You know you can check the md5sum of the cd by mounting it in the system that does run (I think you said T43) and running in terminal:

```
cd /cdrom
md5sum -c md5sum.txt | grep -v 'OK$'
```

It takes quite a while. Like 15 to 20 minutes!

I doubt you could get the Live CD to run with 256 MB RAM, but the machine with 512 MB should be able to run it OK.

Somehow, it still sounds like a "boot" issue to me - like something related to BIOS ............ or maybe stupid thought .............. a faulty CD ROM drive????????????

---

### Post by sneeks on 2009-02-11
have you tried any other live cd's to check the drive,as it sounds like a drive problem to me too.
replacements are cheap!!!!!!!!!!!!

---

### Post by frikki on 2009-02-11
Thank you all, I am now using 8.04 on my T30 (writing this), I burned a cd at 2x speed using the other T30 :) and it worked fine now!!  Maybe this would have worked for the 8.10, think I will just try this one out, maybe try installing 8.10 later.  Now it is getting all the hardware to work, at least my graphics card needs some work. The wifi card gave me no problems, unlike Debian.

Thanks again.

---

