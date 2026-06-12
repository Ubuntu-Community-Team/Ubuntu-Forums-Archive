---
title: "[SOLVED] Upgrade to OOo 3 on Ubuntu Hardy Heron"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by CBHedricks on 2009-01-10
I have upgraded my Hardy Heron from OOo 2.4 to OOo 3.0 with partial success.  All links in the launcher are present but Base and Formula are grayed out.

After doing a little research, it appeared that I was lacking Sun Java support and that was hindering some of the OOo components.  I installed the latest JAVA Run Time, checked that it is the default, and followed the procedure as listed for making sure that I had all the packages installed.

Launched OOo again and it still does not contain Base or Formula.  I do not need base that much, but formula is necessary for what I work with on this computer.

If anyone can offer some ideas it would be great!

OS: Ubuntu 8.04 LTS (Hardy Heron)
CPU: Intel P4 2.4
Mem: 1gb DDR 233
20gb IDE HDD
Onboard Video (SIS Chipset)
Onboard Audio (AC '97)
WiFi: Netgear W511 PCMCIA

Thanks in advance.

CB

---

### Post by Daveth on 2009-01-10
I used something akin to this guide- worked the second time around for me.

[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

---

### Post by Norm24 on 2009-01-10
Check out this thread:
[http://ubuntuforums.org/showthread.php?t=993516](http://ubuntuforums.org/showthread.php?t=993516)

I have the full suite up and running.

---

### Post by CBHedricks on 2009-01-10
The link you mentioned is similar to my first attempt that caused Ubuntu to "loose" gnome and a lot of other important data, and resulted in a "clean" re-install of Ubuntu from DVD.

I have elected to add repository for OOo in Software Sources, also add in "universe" for Java updates and it automatically updated to OOo 3 and Java as well.

The installation of OOo 2.4 had Base and Formula enabled... I would think that the upgrade would also have that same functionality as well.

Will try again on the link you posted, it seems to be more complete than the one that I attempted.

Wish me luck.

CB

---

### Post by fooman on 2009-01-10
if you have already added the repositories,  then just open a terminal and type or copy/paste the following:

```
sudo apt-get install openoffice.org
```

that should get you everything you need. :)

---

### Post by CBHedricks on 2009-01-10
LOL..., love your avatar... 

I have uninstalled OOo, Cleaned, and re-installed OOo via command line per instructions in links presented.  I have this as a message from BASH:

Setting up openoffice.org (1:3.0.1~rc1-2ubuntu1~hardy1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
linuxbox@home:~$

It seems that it locks down access to libc6 for some reason that I am completely unfamiliar with.  Any suggestions?

---

### Post by fooman on 2009-01-10
hmm...did the package download/install?  ...was that the complete output?

---

### Post by CBHedricks on 2009-01-10
I now have OOo 3 installed and have access to all Icons.  The processing of libc6 appears to take about 10 mins to complete then a reboot and now all OOo icons are showing and available for use.  Thanks to all replies to this thread, it gave me a good idea or three and more confidence to try the 'command line' approach again...

Good things to know about OOo:

1. Add software repositories for OOo and make sure you have Sun's Java packages installed.
2. Remove OOo 2.x before you attempt to either upgrade or install new OOo.
3. Use command line "apt-get" to remove old office files, clean out cache and install new OOo from repositories.

Works like a charm this time around and I did not have to 're-install' anything.

Thanks again for the help guys!

CB

---

