---
title: "problems with clamav"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by oaridus on 2010-11-09
Hi guys, how do I upgrade my clamav engine. it says it is outdated. also the freshclam command does not work. it says 

ERROR: Please edit the example config file /usr/local/etc/freshclam.conf
ERROR: Can't open/parse the config file /usr/local/etc/freshclam.conf

what does this mean. please help

---

### Post by arochester on 2010-11-09
CLAMAV

Have you got ClamTk installed - the graphic front-end of ClamAV?

Start it FROM THE TERMINAL with the command: gksudo clamtk

This gives you the superuser rights which enable you to update.

(Don't know about Freshclam)

---

### Post by rburkartjo on 2010-11-11
oar, here is a link
basically all you have to do is add the ppa to your software sources. i had to do the same to get the  engine update

[https://launchpad.net/~ubuntu-clamav/+archive/ppa](https://launchpad.net/~ubuntu-clamav/+archive/ppa)

---

### Post by Carlos Lam on 2010-11-21
Hi [rburkartjo]("http://art.ubuntuforums.org/member.php?u=459705"),

I am an Ubuntu beginner and I have been looking for solutions to the  outdated ClamAV engine problem for quite a while. I have seen many posts and websites and I have to say most of them are either  technically incorrect (such as starting clamtk in root which is NOT recommended by ClamAV. It doesn't solve the problem anyway) or hugely complicated for beginners.

Your suggested solution of downloading the updates from the Ubuntu ppa works beautifully. My ClamAV engine is now up to date. Thanks!

---

### Post by oboedad55 on 2010-11-21
OK, great. I have used BitDefender in the past and it works well too. Here's a link; [http://download.bitdefender.com/repos/](http://download.bitdefender.com/repos/) If you don't want to add PPAs you can download a copy here and install it yourself; 
[http://www.bitdefender.com/solutions/antivirus-for-unices.html](http://www.bitdefender.com/solutions/antivirus-for-unices.html)
OTOH, in fifteen years I haven't had a Linux virus so I don't bother with anti-virus software.

---

### Post by beew on 2010-11-21
> **oboedad55 said:**
> OK, great. I have used BitDefender in the past and it works well too. Here's a link; [http://download.bitdefender.com/repos/](http://download.bitdefender.com/repos/) If you don't want to add PPAs you can download a copy here and install it yourself; 
[http://www.bitdefender.com/solutions/antivirus-for-unices.html](http://www.bitdefender.com/solutions/antivirus-for-unices.html)
OTOH, in fifteen years I haven't had a Linux virus so I don't bother with anti-virus software.

+1 to that. IMO if you must use an AV use a real one like bd, otherwise many people are fine without any AV. ClamAV is crap, it is slow,  resource demanding, hard to set up and worse, it has dismal detection rate. I would rather do nothing than to go through the troubles with ClamAv.  I figure the only reasons that it is recommended by so many people are  1) It is open source 2) Virus is not a real problem in Linux. And the people who recommend ClamAv apparently only use it to scan emails, for which it is adequate.

---

### Post by Carlos Lam on 2010-11-22
I installed ClamAV and went through all the troubles of getting it updated because I didn't know there are better (free) options in Linux!  Will certainly give BD a try.

By the way, it seems that ClamAV can't even automatically scan incoming/outgoing emails with Thunderbird 3......I can't get it to work anyway.

---

