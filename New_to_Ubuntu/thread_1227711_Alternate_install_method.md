---
title: "Alternate install method"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by Morphaeus on 2009-07-31
I've been using Ubuntu for about 6 months and I'm getting the hang of things. I would like to install Ubuntu from the LiveCD without actually booting up the OS. Similar to the way WinXP installs. Is this possible?

---

### Post by Ozitraveller on 2009-07-31
Then you should try :

ubuntu-9.04-alternate-i386.iso

The Perfect Server - Ubuntu Jaunty Jackalope (Ubuntu 9.04) [ISPConfig 2]
[http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2)

Only the first 2 pages are relevant to what you want.

:)

---

### Post by Morphaeus on 2009-07-31
So simple, can't believe I missed that. Thank you for your prompt reply

On a different note, every image I've downloaded and burned hasn't worked when it came down to install. I burned the images with PowerISO and verified data without any problems. Do you know why the discs would be broken then?

---

### Post by Ozitraveller on 2009-07-31
Sorry I don't know Poweriso, I use Nero or [http://cdburnerxp.se/](http://cdburnerxp.se/) (free), ImgBurn (free)

check this out:
[http://www.makeuseof.com/tag/the-best-free-alternatives-to-nero-cddvd-burner/](http://www.makeuseof.com/tag/the-best-free-alternatives-to-nero-cddvd-burner/)

---

### Post by konqueror7 on 2009-07-31
have you tried burning it in lower speeds? around x4 - x8?

---

### Post by plucky on 2009-07-31
Don't forget to check the **MD5SUM** of the ISO.See [link](https://help.ubuntu.com/community/HowToMD5SUM)

Good Luck

---

### Post by Morphaeus on 2009-08-01
I think PowerISO just sucks to be honest. I realized that I always used it to burn the images I downloaded. So I used ImgBurn instead and everything went fine. Also, did a verify under ImgBurn and found 300 errors on the disc PowerISO burned. Very surprising but I know better now.

Thank you everyone for all of your kind and prompt help

---

### Post by presence1960 on 2009-08-01
> **Morphaeus said:**
> I think PowerISO just sucks to be honest. I realized that I always used it to burn the images I downloaded. So I used ImgBurn instead and everything went fine. Also, did a verify under ImgBurn and found 300 errors on the disc PowerISO burned. Very surprising but I know better now.

Thank you everyone for all of your kind and prompt help

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by jackmetal on 2009-10-15
I've always used the liveCD method of install, but am now trying the alternate CD method (since I want to configure LVM and encrypted filesystems.  I have tried a number of times, but for some reason, I just can't get the partitioning correct.  Is there a tutorial somewhere that walks you through using the alternate CD to install Ubuntu using LVM and encrypted filesystems?  Can you do encrypted filesystems without LVM (maybe that's where I'm running into problems, I just can't get the hang of partioning with all the options...)  :-)

Thank You VERY much in advance for any help!!!!!

--edit--  for anyone interested or having issues like me - 
I've continued searching and I've found a couple to try:
[http://oei.yungchin.nl/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/](http://oei.yungchin.nl/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/)
and
[http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)

FYI: The second link above, helped me the most and got me through my install easily.  I decided against LVM for the moment, I'll try that a little later.  I've used LVM over the years on many other *nix systems, but just haven't seen the need on my personal servers and desktops (yet).  Anyone have any good reasons that I should move to LVM?

But.... If anyone has any better one (using 9.04 -or 9.10 beta, which is what I'm going with), it would be much appreciated!
Thanks!!

---

### Post by plucky on 2009-10-15
Try Hermans site [Ubuntu Karmic Koala Encrypted Flash Memory  Installation](http://members.iinet.net/~herman546/p19.html) as it looks useful.

I have not tried it myself and the Howto is still under development.

It is part of this very useful [Illustrated Dual Boot Site](http://members.iinet.net/~herman546/index.html)

Good Luck

---

### Post by jackmetal on 2009-10-15
Hi plucky, thanks for that HowTo.  It had some pointers to some good info.  It's excellent for a "guided" partitioning install, but unfortunately I was doing it manually.  

This one is really good for a manual partitioning install, if you ever need it: [http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)

I used it and got it all working great, did some configurations, rebooted numerous times and Then I ran into an issue... :-(  I did an apt upgrade and now it won't boot because it's not finding my encrypted root filesystem.  So now I'm searching and trying to figure out how to fix that (and wondering if I should have just left my root filesystem un-encrypted.  :-(

Thanks again!!

---

