---
title: "DNS / DSL problems in 9.10"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by Desert Sailor on 2009-11-12
I recently switched to DSL from Cable, (In my area DSL is actually better than our local cable supplier).  However my 9.10 install doesn't seem to approve.  Was working fine on Cable, now not resolving DNS on DSL.  Actually the problem isn't 9.10 exactly, because I can ping, and Update Manager and Apt-Get are working but no WWW. pages are being found and I can't get mail.  

My 9.04 install is working fine on the same Internet connection.  So here are my questions...

1. Do you think the problem is in Network Manager, or could it be in Firefox and Thunderbird at the same time? 

2. Is this a common problem or unique to my install?  and, 

3. Would you guess that this is something that will get patched soon, or should I just quit using my 9.10 install and roll back to 9.4 until next year? 

I await your exalted opinions....(lol).

---

### Post by AgenT on 2009-11-13
First, give the exact error you receive and where. Show a screenshot if you think it will help.

Are you sure you can ping the same website you are trying to reach via your web browser? Try a few different ones.

This problem actually sounds like with your internet provider, but who knows.

Use a different web browser, such as epiphany. Do you still get the problem? If so, get wireshark and trace your internet connection when you try to view a website and see what is going on behind the hood and where the problem lies.

I am having DNS issues since upgrading to 9.10, but mine are with delayed DNS response (causes a delay in website load). In case that helps. Good luck.

Things to look out for:
1) funny router or modem firewall being turned on
2) bad nameservers being provided by your provider (restart your modem)
3) bad nameservers in memory (restart your computer right AFTER restarting your modem)

---

### Post by AgenT on 2009-11-13
I fixed my DNS problem. [Disabling IPv6 for grub 2]("http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html") ([or this for grub 1]("http://www.webupd8.org/2009/05/how-to-disable-ipv6-in-ubuntu-jaunty.html")) fixed it for me!

Don't know whether you have grub 1 or 2? First, check if you have the program update-grub2 and if you do, you have grub 2. If you do not, check if you have the program update-grub and if you do, you have grub 1. If you don't have either, your either 1) not not checking properly or 2) not using grub (very small chance since it's installed by default).

---

### Post by ukripper on 2009-11-13
> **Desert Sailor said:**
> 

1. Do you think the problem is in Network Manager, or could it be in Firefox and Thunderbird at the same time? 
have you got proxy settings in firefox enabled? can you post output of below command:
```
cat ~/.mozilla/firefox/**whatever-is-your-profile**.default/prefs.js
```

change above in bold to your profile id

---

### Post by ratcheer on 2009-11-13
> **AgenT said:**
> I fixed my DNS problem. [Disabling IPv6]("http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html") ([or this]("http://www.webupd8.org/2009/05/how-to-disable-ipv6-in-ubuntu-jaunty.html") if you have grub 1) fixed it for me!

That seems odd. I use DSL and my 9.10 installation still has IPv6 and everything works, just fine.

Tim

---

### Post by pbrane on 2009-11-13
There seems to be an issue in 9.10 with some routers not dealing properly with IPv6. At home my Linksys router works fine, very fast DNS lookups. (the nameserver addresses are in /etc/resolv.conf) But at work the 2Wire router I use does REALLY slow lookups. (the nameserver in /etc/resolv.conf is the router address). I started using OpenDNS and lookups are very fast now. This was not an issue in 9.04. Disabling IPv6 and other workarounds I found did not solve it for me.

---

### Post by Desert Sailor on 2009-11-14
Thank you all VERY MUCH...  You're responses got me going and checking a few things and I have tracked down the problem.  

The problem for me is my OLD Actiontec Qwest DSL Modem.  It does not support IPv6 and was/is the problem.  Here is how I came to that conclusion. 

The modem was given to me by a friend when I decided to switch to DSL, I don't know how old it is, but I am certain it is not "new". 

I followed the instructions to disable IPv6 in Firefox and now it works! 
This text from the Web Upd8 web site ([www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.htr](www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.htr)) said...

"...there is nothing wrong with either Ubuntu (Karmic) or IPv6, so if you are experiencing any issues, they are because of your ISP / router / Modem."

That started me thinking about when the problem first began, why it would would work with Comcast, but not DSL, 

NEW DSL MODEM on it's way!!!  

Thanks...Let's mark this one SOLVED.

---

### Post by Digikid on 2010-01-20
Actually this is not a solved issue at all and the fault is entirely Ubuntus.

[http://www.craigmayhew.com/blog/2009/11/slow-dns-lookups-in-firefox-on-ubuntu-9-10-karmic-koala/](http://www.craigmayhew.com/blog/2009/11/slow-dns-lookups-in-firefox-on-ubuntu-9-10-karmic-koala/)

They REALLY need to fix this probleml

---

