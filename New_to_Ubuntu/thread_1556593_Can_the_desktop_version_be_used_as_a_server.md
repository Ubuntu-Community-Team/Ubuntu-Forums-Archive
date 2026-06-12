---
title: "Can the desktop version be used as a server?"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by MEADE999 on 2010-08-19
Hi guys,

Im new here!

I am looking at running my own dedicated web server from home and I am checking the different versions of ubuntu on their website. I see there is a server edition, i am guessing that this is all command promopts and no graphical interface?

Can a server be run from the desktop verison? 

ie, can I run a server on Ubuntu with a graphical interface so that it is easier to navigate etc?

many thanks in advance for advice.

mike

---

### Post by endotherm on 2010-08-19
yep, done it for years. just beware, the desktop manager introduces a lot of code, so there is the potential that it will make your server easier to exploit, if it is public facing.

---

### Post by MEADE999 on 2010-08-19
Ah, really? thats interesting.

What if I have a firewall that only allows ports 22 and 80? and if I setup a whitelist that only allows access to port 22 from my ip. 

Would this still pose a security risk?

thanks

---

### Post by endotherm on 2010-08-19
ok, we're getting into the difference between known and unknown vulnerabilities. 
yes your configuration is pretty secure as long as you lock down the services behind both ports. this takes care of the known vulns. the reason I bring up potential security issues from installing X and Gnome, is that you are greatly expanding the codebase on the server, and the more code you have, the more likely you are exposing an vuln. it's an esoteric concern, but security issues usually are.

---

### Post by KdotJ on 2010-08-19
As a side note, are you planning to run the server headless? As in with no monitor connected? In the past, I have seen people having issues with ubuntu not booting as it says it cant find a monitor. Though This may be not be a problem any more.

---

### Post by wojox on 2010-08-19
If you have the time, download the Server Version and learn the command line. You will then have unlocked the full potential of Linux. ;)

---

### Post by Spice Weasel on 2010-08-19
It can be used pretty well, but using the default desktop is a bad idea for the server. It's far too bulky. I'd recommend using a desktop such as IceWM (Link in my signature) or Fluxbox which are both easy to install. In the end you will most likely end up doing a lot of configuring the server using the terminal anyway, so it's easier to use the Server Edition. Entirely your choice though.

---

### Post by pricetech on 2010-08-19
> **MEADE999 said:**
> What if I have a firewall that only allows ports 22 and 80? and if I setup a whitelist that only allows access to port 22 from my ip. 

I run more than one server using the desktop version.  Only one is what you'd consider a "dedicated" server and even on it I occasionally use the desktop, so I've just never set one up using the server version.  I've had no issues, but then I'm ridiculously careful what I expose the Internet.

I am wondering though, and this is why I quoted you, are you directly connected to the Internet with this computer?  If not, then you won't need to whitelist yourself for port 22, just don't forward it.

---

### Post by liquidfunk on 2010-08-19
It can be. It used to be the case that servers never had GUIs. However, Red Hat 5 has a GUI for its server distro, and that performs very well. 

It all comes down to how meaty your machine is.

---

### Post by KdotJ on 2010-08-19
> **wojox said:**
> If you have the time, download the Server Version and learn the command line. You will then have unlocked the full potential of Linux. ;)

+1 this is what I did...
And I'm so glad I did, it taught me so much and I learnt how to fix problems by the command line. All of my admin stuff for my server is done on my laptop via ssh

---

### Post by bodhi.zazen on 2010-08-19
> **MEADE999 said:**
> Hi guys,

Im new here!

I am looking at running my own dedicated web server from home and I am checking the different versions of ubuntu on their website. I see there is a server edition, i am guessing that this is all command promopts and no graphical interface?

Can a server be run from the desktop verison? 

ie, can I run a server on Ubuntu with a graphical interface so that it is easier to navigate etc?

many thanks in advance for advice.

mike

If you are running a few services for a lan, such as nfs or samba, and you actually use the machine as a desktop, it is fine.

For a dedicated web server, IMHO, a desktop does not add much, and in fact introduces a number of potential security problems.

Most of running a dedicated server involves editing configuration files (text files) and / or restarting services and / or updates so a desktop does not add much.

If you feel you need a graphical interface, I highly suggest web tools such as webmin.

---

### Post by DaGeek247 on 2010-08-20
If it is just for personal use you could use xampp. Although it is meant for personal use, you could set it up as a secure server, if you wanted to. I posted a question about it [here]("http://ubuntuforums.org/showthread.php?t=1550197"), it might help you. (not the security part, but a way to make it run easy)

---

