---
title: "Invalid Argument in Avast installation"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by Zombir on 2010-11-19
I usually work on some other operating system and switch to Ubuntu once in a while for my academic work. So I don't have much experience with Ubuntu. 

Anyway, yesterday I tried to install Avast! in my Ubuntu. I downloaded the .deb package and did:

```

sudo dpkg -i avast4workstation_1.3.0-2_i386.deb

```in my terminal to install it. But when I tried to access Avast! through:
 
Applications -> Accessories -> avast! Antivirus

I got this error message: 

"An error occurred in avast engine: invalid argument"

Now my computer has been previously used by someone else and he had Avast! in the first place in Ubuntu. But he did some stupid thing - something that made him to install Ubuntu over the existing one. 

Is it because of some stale file left from the previous Avast! that I cannot install Avast? Please help thanks.

---

### Post by wilee-nilee on 2010-11-19
Here is a quote if you actually go to the avast forum this is the answer you will find.

All that all you need to do is edit /etc/sysctl.conf by adding this:
**kernel.shmmax = 128000000**

So from the terminal run and add the last line in the quote, make sure there is no # in front just put it after the very last stanza.

```
sudo gedit /etc/sysctl.conf
```

---

### Post by Zombir on 2010-11-20
Thank you and extremely sorry for tiring you, not looking up the net first. :oops: It looked so unique to me that I didn't think it would be there in the net.  Anyway this solved my problem. Thanks a lot again.

---

### Post by northd_tech on 2011-11-11
> **wilee-nilee said:**
> Here is a quote if you actually go to the avast forum this is the answer you will find.

All that all you need to do is edit /etc/sysctl.conf by adding this:
**kernel.shmmax = 128000000**

So from the terminal run and add the last line in the quote, make sure there is no # in front just put it after the very last stanza.

```
[COLOR=Red]sudo gedit[/COLOR] /etc/sysctl.conf
```

That **kernel.shmmax = 128000000  **worked for me with Avast 1.4.0 antivirus under Ubuntu Lucid Lynx 10.04.3 LTS (64bit) and this kernel:

> Linux hostname 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC 2011 x86_64 GNU/LinuxIt also worked with the 2.6.32-35-generic and 2.6.32-21-generic kernels.

Of course, I believe that one should always use **gksu** with **gedit** (and other graphic applications), so the proper command should be:

```
gksu gedit /etc/sysctl.conf
```then add the "**kernel.shmmax = 128000000**" line, save, and exit/quit **gedit**, then reboot- Avast 1.4.0 should now work fine with no error messages.

**gksudo gedit or sudo gedit?**
[http://ubuntuforums.org/showthread.php?t=1259203](http://ubuntuforums.org/showthread.php?t=1259203)

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

[http://ubuntuforums.org/showthread.php?t=306156](http://ubuntuforums.org/showthread.php?t=306156)

[http://ubuntuforums.org/showthread.php?t=701812](http://ubuntuforums.org/showthread.php?t=701812)

---

