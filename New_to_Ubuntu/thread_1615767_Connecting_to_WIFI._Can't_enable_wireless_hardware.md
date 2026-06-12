---
title: "Connecting to WIFI. Can't enable wireless hardware. UBUNTU 10.10"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by gchdevon on 2010-11-07
Hi. Very new to UBUNTU. I apologise for posting in this forum rather than the Internet/wireless forum which might have been more appropriate. However I did try and research on that forum and I soon reached the limits of my understanding.

My wireless card is Intel PRO/ Wireless 3945 ABG [golan].

According to the info on this forum it should work "out of the box".

However following instructions on UBUNTU documentation, I get to a box that says "no wireless extensions".

The documentation then says I must configure my wireless card. At this point I lose the plot and seem to be directed to a number of different pages asking me to do things I don't understand.

I am able to connect to internet with cable.

As part of trying to work this out I installed an application called WIFI radar. It cannot detect anything, unsurprisingly if the wireless card is not enabled.

If somebody does kindly respond I hope they don't mind if I have to clarify some of the terms they might use.

Thanks.

---

### Post by lev-unr on 2010-11-07
What type of laptop are you using? Sometimes you need to simply enable the wireless card (hardware issue) I have seen this same issue even with windows. Is there a button on your laptop that simply enables/disables the wireless?

---

### Post by cdmyrick on 2010-11-08
> **gchdevon said:**
> Hi. Very new to UBUNTU. I apologise for posting in this forum rather than the Internet/wireless forum which might have been more appropriate. However I did try and research on that forum and I soon reached the limits of my understanding.

My wireless card is Intel PRO/ Wireless 3945 ABG [golan].

According to the info on this forum it should work "out of the box".

However following instructions on UBUNTU documentation, I get to a box that says "no wireless extensions".

The documentation then says I must configure my wireless card. At this point I lose the plot and seem to be directed to a number of different pages asking me to do things I don't understand.

I am able to connect to internet with cable.

As part of trying to work this out I installed an application called WIFI radar. It cannot detect anything, unsurprisingly if the wireless card is not enabled.

If somebody does kindly respond I hope they don't mind if I have to clarify some of the terms they might use.

Thanks.


had the same problem, this may help
[http://tenthblog.com/ubuntu-how-to-enable-your-wireless-card-dell-broadcom-bcm4311/](http://tenthblog.com/ubuntu-how-to-enable-your-wireless-card-dell-broadcom-bcm4311/)

if not let me know and ill dig deeper for you :)

---

### Post by ramjet_1953 on 2010-11-08
I have had success with this work-around.

[http://ubuntuforums.org/showthread.php?t=1496856&highlight=intel+2200BG&page=2](http://ubuntuforums.org/showthread.php?t=1496856&highlight=intel+2200BG&page=2)

Look for my post on page 2 and give it a try.

As your card is a 3495 just substitute it for 2200BG in the instructions

Regards,
Roger:)

---

### Post by gchdevon on 2010-11-08
Thanks Lev, I hAVE  a packard bell easynote. It does have a WIFI  button that is on by default, it is on.

Cdmyrick and ramjet. Thank you for responding. The thing is I am very new to UBUNTU. I have worked out where terminal is and what to do to a certain extent but your advice baffles me when I go to the links.

Rick, do I copy and paste the lines of code from the first examples into TERMINAL? I understand that but then editing "rc.local" and the rest is over my head.

ramjet, how do I know whether I have the modpro file you mention, if not how and where do I create it? If it is there if i put the code into terminal that you suggest just changing 2200 for 3495 could I be caUSING SOME complications if the file is not there?

Sorry for being so dense and thank you for your time.

---

### Post by glimmer on 2011-03-24
well i think you should ask your provider about it. i also experience it before and asked the provider and of course to clear my mind about wi-fi. this might help wifibsd.org. it helped me alot though.

---

