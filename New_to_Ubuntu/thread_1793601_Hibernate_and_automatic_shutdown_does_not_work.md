---
title: "Hibernate and automatic shutdown does not work"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by anemone42 on 2011-06-29
I have installed Ubuntu as wubi (next to windows 7). When I expect the computer to shut down (either to hibernate or as part of, you know, shutdown), it doesn't. All the programs end, I am logged out, but I still have a picture on the screen  (ubuntu default picture).

Help!

---

### Post by DogMatix on 2011-06-29
I don't think hibernate works with a Wubi installation.

---

### Post by amjjawad on 2011-06-30
> **anemone42 said:**
> I have installed Ubuntu as wubi (next to windows 7). 
It's "inside" Windows NOT next to it ;)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

> 
When I expect the computer to shut down (either to hibernate or as part of, you know, shutdown), it doesn't. All the programs end, I am logged out, but I still have a picture on the screen  (ubuntu default picture).

Help!

> Hibernation is not supported under Wubi, moreover Wubi filesystem is  more vulnerable to hard-reboots (turning off the power) and power  outages than a normal filesystem, so try to avoid unplugging the power.  An Ubuntu installation to a dedicated partition provides a filesystem  that is more robust and can better tolerate such events.
[http://wubi.sourceforge.net/faq.php](http://wubi.sourceforge.net/faq.php)

Use google or [http://www.googlubuntu.com](http://www.googlubuntu.com) to find more about that. I have no experience with Wubi and I don't use it.

---

### Post by anemone42 on 2011-06-30
Okay, stating my original problem again. When I expect the computer to shut down, because I chose shutdown, it does not.

---

### Post by anemone42 on 2011-09-28
While my problem is similar to the one described here:

[http://ubuntuforums.org/showthread.php?p=10489760](http://ubuntuforums.org/showthread.php?p=10489760)

the solution doesn't work for me.

---

### Post by bcbc on 2011-09-29
Use Alt+SysRq R-E-I-S-U-B to force reboot. Try processing all available updates.

Look in /var/log/syslog to see if there are any messages that might explain it.

---

### Post by anemone42 on 2011-09-29
The stuff in the syslog, just before I logged out / shut down last time:

Sep 29 03:15:22 ubuntu dhclient: DHCPREQUEST of 192.168.0.10 on eth1 to 192.168.0.1 port 67
Sep 29 03:15:23 ubuntu dhclient: DHCPACK of 192.168.0.10 from 192.168.0.1
Sep 29 03:15:23 ubuntu dhclient: bound to 192.168.0.10 -- renewal in 1536 seconds.
Sep 29 03:17:01 ubuntu CRON[2190]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

Other than that, it's something like 1200 lines to process. What am I looking for?

I've had this problem with a previous installation, and it didn't help to update. Sometimes I would grow to a new version number, that version would run once, do some weird shutdown, and then never run again.

---

### Post by dr1094 on 2011-09-29
I also have Ubuntu installed on my laptop, and I've installed it using wubi. When the computer starts it shows up two options: windows, or ubuntu. On my laptop shutdown function works fine, but hibernation does not. there maybe something wrong with the specs you chose for ubuntu. 

I chose 30 GB for Ubuntu, the system takes up about 2-4gb, and i use the remaining for my files. You should list your specs for your laptop here, maybe it's a hardware issue.

---

### Post by bcbc on 2011-09-29
Sometimes (sometimes) you get some very helpful messages in the syslog. I normally pick an event and then work backwards looking for something interesting. There is also a lot of gobbledygook there.
You could just attach the whole log...

What computer brand/model/wireless card etc. do you have?

---

### Post by anemone42 on 2011-09-29
Syslog attached.

Hm. That syslog wasn't very interesting. I'll have to do it again later.

---

### Post by anemone42 on 2011-09-29
> **dr1094 said:**
> I also have Ubuntu installed on my laptop, and I've installed it using wubi. When the computer starts it shows up two options: windows, or ubuntu. On my laptop shutdown function works fine, but hibernation does not. there maybe something wrong with the specs you chose for ubuntu. 

I chose 30 GB for Ubuntu, the system takes up about 2-4gb, and i use the remaining for my files. You should list your specs for your laptop here, maybe it's a hardware issue.

Windows does shutdown fine.

I am not talking hibernation, as that doesn't work with wubi. (Right?)

I think I chose default options for wubi, nothing spectacular.

I think the default option for size is 17GB, so I chose that. All my files are on the Windows side, so I can see them from both systems.

Laptop: HP 620. Which other specs?

---

### Post by anemone42 on 2011-09-29
> **bcbc said:**
> Sometimes (sometimes) you get some very helpful messages in the syslog. I normally pick an event and then work backwards looking for something interesting. There is also a lot of gobbledygook there.
You could just attach the whole log...

What computer brand/model/wireless card etc. do you have?

Computer: laptop, HP 620.

Not sure where I can see the type of wireless card.

---

### Post by bcbc on 2011-09-29
Check this out - sounds similar to your issue: [http://ubuntuforums.org/showthread.php?t=1795824](http://ubuntuforums.org/showthread.php?t=1795824)

Also this one: [http://ubuntuforums.org/showpost.php?p=11228838&postcount=6](http://ubuntuforums.org/showpost.php?p=11228838&postcount=6)

Note: those two threads suggest blacklisting one of two drivers, but they have not blacklisted the same one.

---

### Post by anemone42 on 2011-09-29
> **bcbc said:**
> Check this out - sounds similar to your issue: [http://ubuntuforums.org/showthread.php?t=1795824](http://ubuntuforums.org/showthread.php?t=1795824)

Also this one: [http://ubuntuforums.org/showpost.php?p=11228838&postcount=6](http://ubuntuforums.org/showpost.php?p=11228838&postcount=6)

Note: those two threads suggest blacklisting one of two drivers, but they have not blacklisted the same one.

I blacklisted one, and the computer froze. I blacklisted the other, it had no effect.

As I had already hinted at ...

---

### Post by anemone42 on 2011-09-29
> **bcbc said:**
> Use Alt+SysRq R-E-I-S-U-B to force reboot. Try processing all available updates.

Look in /var/log/syslog to see if there are any messages that might explain it.

I've tried different combinations with the sys rq button (combined with delete). Alt + SysRq does nothing. fn + SysRq = print screen.

---

### Post by bcbc on 2011-09-29
oh yeah... (note to self: read the link)

So, based on this post: [http://ubuntuforums.org/showpost.php?p=10516001&postcount=12](http://ubuntuforums.org/showpost.php?p=10516001&postcount=12) - *timgood* mentioned that following the original instructions caused his machine to freeze and he gave some alternate instructions. Did you follow that?

Also this is probably best handled by the people in the networking and wireless subforum. I'll see if a mod can move it so you get appropriate help (I'm not very good at the network issues).

---

### Post by anemone42 on 2011-09-29
I just tried this:

```
tail /etc/modprobe.d/blacklist.conf
...
blacklist amd76x_edac
blacklist rt2860sta
``````
sudo modprobe -rf rt2800pci
sudo modprobe -rf rt2860sta
sudo modprobe rt2860sta
```Last command was followed by freeze.

Maybe it's stupid to expect it to work, when it is actually blacklisted?

---

### Post by bcbc on 2011-09-29
It's not very clear from the post, I have to agree. I'll see if I can find something more informative. In the meantime, why don't you post on that thread and see if you get some help from others there?

---

### Post by bcbc on 2011-09-30
> **anemone42 said:**
> I just tried this:

```
tail /etc/modprobe.d/blacklist.conf
...
blacklist amd76x_edac
blacklist rt2860sta
``````
sudo modprobe -rf rt2800pci
sudo modprobe -rf rt2860sta
sudo modprobe rt2860sta
```Last command was followed by freeze.

Maybe it's stupid to expect it to work, when it is actually blacklisted?

So the order shown by timgood was:
```
sudo modprobe -rf rt2860sta
sudo modprobe rt2860sta
echo blacklist rt2800pci | sudo tee -a /etc/modprobe.d/blacklist.conf
```
You first blacklisted the wrong one, then added the 'modprobe -rf rt2800pci'.

So, I'd remove the blacklist. Then reboot.
Then repeat timgood's instructions, and hopefully a better result.

---

### Post by amjjawad on 2011-09-30
See if this thread is helpful: [http://ubuntuforums.org/showthread.php?t=1643545](http://ubuntuforums.org/showthread.php?t=1643545)

---

### Post by anemone42 on 2011-10-02
> **bcbc said:**
> Look in /var/log/syslog to see if there are any messages that might explain it.

syslog attached. Do you see anything?

---

### Post by anemone42 on 2011-10-02
> **bcbc said:**
> So, I'd remove the blacklist. Then reboot.
Then repeat timgood's instructions, and hopefully a better result.

Yeah, no effect. Still froze up on :
sudo modprobe rt2860sta

I guess I would have to add this line:

SUSPEND_MODULES="rt2800pci"
In /etc/pm/config.d/config

---

### Post by anemone42 on 2011-10-02
> **amjjawad said:**
> See if this thread is helpful: [http://ubuntuforums.org/showthread.php?t=1643545](http://ubuntuforums.org/showthread.php?t=1643545)

I'm not sure. It seems to add an extra step to the blacklisting. But then, it's also specifically not about a computer freezing instead of shutting down. So ...

---

### Post by amjjawad on 2011-10-02
> **anemone42 said:**
> I'm not sure. It seems to add an extra step to the blacklisting. But then, it's also specifically not about a computer freezing instead of shutting down. So ...

I know it has nothing to do with shutting down, but it has to do with your network card. We both seem to have the same driver and I guess the same steps will be helpful.

chili555 suggest to add "suspend" and that worked perfectly with me but might not with you. Try, no harm ;)

---

### Post by anemone42 on 2011-10-02
Just to cover one base more:

```
lisea@ubuntu:~$ lsmod | grep rt
parport_pc             32111  0 
rt2860sta             494649  0 
rt2800pci              18159  0 
rt2800lib              43824  1 rt2800pci
crc_ccitt              12595  2 rt2860sta,rt2800lib
rt2x00pci              13986  1 rt2800pci
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
parport                36746  3 parport_pc,ppdev,lp
```

So I certainly have some of the symptoms.

---

### Post by anemone42 on 2011-10-06
Okay, current state of affairs:

```
lisea@ubuntu:~$ bin/rtcheck.sh 
-----------------------------------------------
SUSPEND_MODULES="rt2800pci"
-----------------------------------------------
blacklist rt2800pci
-----------------------------------------------
parport_pc             32111  0 
rt2860sta             494649  1 
crc_ccitt              12595  1 rt2860sta
parport                36746  3 parport_pc,ppdev,lp
-----------------------------------------------
lisea@ubuntu:~$ 
lisea@ubuntu:~$ cat bin/rtcheck.sh 
#/bin/sh

echo "-----------------------------------------------"
cat /etc/pm/config.d/config 
echo "-----------------------------------------------"
tail -n 1 /etc/modprobe.d/blacklist.conf
echo "-----------------------------------------------"
lsmod | grep rt
echo "-----------------------------------------------"
```

In part this was achieved through these commands:

```
sudo modprobe -rf rt2800pci
sudo modprobe -rf rt2860sta
sudo modprobe rt2860sta
```

I blacklisted rt2800pci first (meaning it won't be loaded in the future), then removed it right now with the 3 commands above. The computer froze as a result of the last command, but after boot it finally did what it was supposed to do.

**Success! My computer finally understands how a shutdown works!**

---

### Post by amjjawad on 2011-10-07
> **anemone42 said:**
> Okay, current state of affairs:

```
lisea@ubuntu:~$ bin/rtcheck.sh 
-----------------------------------------------
SUSPEND_MODULES="rt2800pci"
-----------------------------------------------
blacklist rt2800pci
-----------------------------------------------
parport_pc             32111  0 
rt2860sta             494649  1 
crc_ccitt              12595  1 rt2860sta
parport                36746  3 parport_pc,ppdev,lp
-----------------------------------------------
lisea@ubuntu:~$ 
lisea@ubuntu:~$ cat bin/rtcheck.sh 
#/bin/sh

echo "-----------------------------------------------"
cat /etc/pm/config.d/config 
echo "-----------------------------------------------"
tail -n 1 /etc/modprobe.d/blacklist.conf
echo "-----------------------------------------------"
lsmod | grep rt
echo "-----------------------------------------------"
```In part this was achieved through these commands:

```
sudo modprobe -rf rt2800pci
sudo modprobe -rf rt2860sta
sudo modprobe rt2860sta
```I blacklisted rt2800pci first (meaning it won't be loaded in the future), then removed it right now with the 3 commands above. The computer froze as a result of the last command, but after boot it finally did what it was supposed to do.

**Success! My computer finally understands how a shutdown works!**

Great, good job :)
If you don't have another Q, please mark this thread as SOLVED from Thread Tools :)

---

