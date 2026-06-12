---
title: "Configuring Ethernet card"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by NikS on 2009-09-06
Hi,
I use a broadband internet connection for which I have to first connect to a LAN network and then provide my username and password.
I have all the details required to connect to it:
IP, Subnet mask, Gatewa address, preferred DNS, alt. DNS, username and password with me.
And I was able to configure my Ubuntu 8.04 for connecting to internet. But, I had to format my drives and reinstall the OS(Same version) but now the same details are not working! :confused:

This issue was there even for the last installation, but I was trying out some changes, frequently restarting, and it started working. But this time I have tried out everything I had done the last time but still I am not being able to connect. :(

Can anyone please help me with this??

Thanks...!

---

### Post by Bachstelze on 2009-09-06
Maybe you need to use [font=monospace]pppoeconf[/font]?

---

### Post by NikS on 2009-09-06
Thanks for you reply..:)

Can you please enlighten how to use it??

Thing is, right now I am not booted into Ubuntu(no net connectivity there!!), I will have to boot into ubuntu and try the approach.. can you please explain in a bit more details so that I can copy it down to a file which can be accessible from ubuntu and try it out??

---

### Post by Bachstelze on 2009-09-06
> **NikS said:**
> Can you please enlighten how to use it??

No, because I have never used it myself. I just know that it is the program you use to configure PPPoE connections, which is probably what you have. Open a terminal and run [font=monospace]sudo ppoeconf[/font], it should be pretty straightforward.

---

### Post by NikS on 2009-09-06
Ok...!!! :o

Thanks for the suggestion..
I will try that and will reply back!! :P

---

### Post by NikS on 2009-09-06
Hi HymnToLife,
I tried out your suggestion, but its not working... I think I do not have the application you mentioned..
I am getting: "command not found" error..

Is there anything else I should do..??:(
Please help me, I need net on My ubuntu!!!

---

### Post by cariboo on 2009-09-06
Pppoeconf, is installed by default. In a terminal type:

```
locate pppoeconf
```

you should get a result that looks like this:

```
locate pppoeconf
/usr/sbin/pppoeconf
/usr/share/doc/pppoeconf
/usr/share/doc/pppoeconf/README.Debian
/usr/share/doc/pppoeconf/changelog.gz
/usr/share/doc/pppoeconf/copyright
/usr/share/locale-langpack/en_GB/LC_MESSAGES/pppoeconf.mo
/usr/share/man/man8/pppoeconf.8.gz
/usr/share/menu/pppoeconf
/usr/share/pixmaps/pppoeconf.xpm
/var/lib/dpkg/info/pppoeconf.list
/var/lib/dpkg/info/pppoeconf.md5sums
/var/lib/dpkg/info/pppoeconf.postinst
/var/lib/dpkg/info/pppoeconf.postrm
```

If you get the above result you will see that pppoeconf is located in /usr/sbin. To run the command, in the same terminal type:

```
sudo pppoeconf
```

and fill out the information as needed.

---

### Post by NikS on 2009-09-07
Hey.. It worked!!!!

Thanks a lot!! (I must have made some mistake when I tried it last time, may be a typo!! Sorry...)

Its working!!! :P
Thanks!!!

---

