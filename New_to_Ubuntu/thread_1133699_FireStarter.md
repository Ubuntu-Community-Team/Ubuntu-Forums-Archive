---
title: "FireStarter"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by mark.giblin on 2009-04-23
Does Linux need a firewall? I was lead to believe that Linux was secure and not open to these issues of hacks, viruses and other malwares that exist in cyberville.

I am asking as I have installed it and since installing it I have noticed that the HSDPA modem I have to connect to the internet with will at random cease to function and I then can not connect at all and then all of a sudden the modem disapears from the networking list in the task bar.

It takes a fresh reboot (cold boot) for the modem to work again.

I have been running most of today without any issues at all as the firewall is not operating. 

So I can only assume that the problem is in the firewall software.

Anyway my question, why is a firewall needed on Linux?

---

### Post by Roadbloc on 2009-04-23
i have never had to install a firewall or even seen any firewall software on add/remove, although that could just be me being dumb and not thinking of my security.

i think one is built in for i have never had any trouble with hackers and evil programs....

---

### Post by Linux_Kid66 on 2009-04-23
You Should have a firewall for peace of mind if you want, but on my laptop i'm not currently running one.
 
I think Ubuntu has an in-built one, and if there is it hasn't ever troubled me, even on windows hackers and that lot have never tried to get in.
I can reccommend peer Gaurdian though.

---

### Post by tom56 on 2009-04-23
Ubuntu doesn't need a firewall, since there are no ports open by default. FireStarter allows you to change which ports are open/closed, but since they are all closed by default this is not necessary.

---

### Post by Sir Jasper on 2009-04-23
Hi,

I use the Firewall to block to block all outgoing connections except, for my browser and email (i.e. http, https, pop3 and smtp).

I use a few windows programs (using "wine") from within 8.10 and as the Firewall is available but not activated it seems a sensible additional, though perhaps unnecessary, precaution.

Firestarter is for configuing the Firewall. It is not the Firewall itself and after set-up it does not need to be run again if no policy changes are needed.

Copy sudo iptables -nL into your Terminal if you want to see if your Firewall is running. If, as output, you see a menu at the top and lots of zeroes in a table below - then it's working.

My regards

---

### Post by some_random_noob on 2009-04-23
I recommend using a firewall - sure Ubuntu has no open ports by default, but what if you start installing stuff and opening yourself up to attack? You should whitelist out going traffic and allow the following ports: 80, 1863, 25, 110, 20, 21 (don't forget shttp and anything specific to what you have installed!).

You don't have to do that, but it certainly helps. The main thing is to not download too much garbage. Also be careful with browsing. Security problems are far and few, but it pays to be careful (that includes with attachments and running commands/scripts).

---

### Post by Thelasko on 2009-04-23
Firestarter is outdated, use GUFW instead.

---

### Post by mark.giblin on 2009-04-25
Well I kept having my HSDPA modem keep playing up and noticed it was still loading at boot.

I had the "Modem" issue again dispapear from my available connections list, so befr a reboot, I removed it with the package manager / add remove tool.

When the job was done, the modem became available again so no reboot needed!

So the issue is the firewall software.

---

### Post by presence1960 on 2009-04-25
> **mark.giblin said:**
> Does Linux need a firewall? I was lead to believe that Linux was secure and not open to these issues of hacks, viruses and other malwares that exist in cyberville.

I am asking as I have installed it and since installing it I have noticed that the HSDPA modem I have to connect to the internet with will at random cease to function and I then can not connect at all and then all of a sudden the modem disapears from the networking list in the task bar.

It takes a fresh reboot (cold boot) for the modem to work again.

I have been running most of today without any issues at all as the firewall is not operating. 

So I can only assume that the problem is in the firewall software.

Anyway my question, why is a firewall needed on Linux?

For a great article on security in Ubuntu (including firewall) look here: 

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

