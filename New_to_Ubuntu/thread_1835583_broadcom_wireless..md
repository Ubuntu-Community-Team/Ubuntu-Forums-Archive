---
title: "broadcom wireless."
date: 2011-08-29
forum: New to Ubuntu
---

### Post by wozelbeak on 2011-08-29
i am extremely green on the use of linux (ubuntu). i have today installed ubuntu latest version on a old laptop for my elderly parents to use. they only google things and watch the odd video.
my problem is that i can not get the wireless device to show up in the network connections. i have read through a dozen different solutions without any joy.
now bare in mind that i am a total novice on ubuntu. its a compaq nx6325 laptop. it has a broadcom bcm5788 wireless card (i think). i know these cards are renowned for giving problems when installing ubuntu, but this is driving me nuts!
any simple talk through cures will be very welcom.
i do have wired internet on the laptop.

---

### Post by gandaran on 2011-08-29
have you looked in additional drivers after connecting with wired internet (and wait a few minutes to update software packages) for the broadcom driver then enable it?

---

### Post by wozelbeak on 2011-08-29
i think i have found the additional driver previously and installed. now when i click on the tab nothing happens. could you direct me to the location where additional drivers is please? just in case i am accessing the wrong location.

---

### Post by snip3r8 on 2011-08-29
Which version of ubuntu are you running?

---

### Post by wozelbeak on 2011-08-29
11.04 natty.

---

### Post by gandaran on 2011-08-29
> **wozelbeak said:**
> i think i have found the additional driver previously and installed. now when i click on the tab nothing happens. could you direct me to the location where additional drivers is please? just in case i am accessing the wrong location.
on ubuntu classic » system » administration » additional drivers
on unity desktop I don't remember exactly how but I believe it's in the system settings window.
you can also follow this broadcom thread to find the right driver/firmware
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by wozelbeak on 2011-08-29
i have to go to control center and then hardware to get to additional drivers which has a padlock on it?

---

### Post by wozelbeak on 2011-08-30
thanks for the help so far guys but it has not helped me with getting my wireless card recognized.

---

### Post by bkratz on 2011-08-30
> **wozelbeak said:**
> thanks for the help so far guys but it has not helped me with getting my wireless card recognized.



Actually the number you referenced in you first post is the ethernet card not the wireless.

[http://www.broadcom.com/products/Ethernet-Controllers/Home/BCM5788](http://www.broadcom.com/products/Ethernet-Controllers/Home/BCM5788)

You might have better luck with

lspci | grep Network

or

lspci -nn | grep 0280

one should tell what the wireless card is

---

### Post by wozelbeak on 2011-08-30
Hi, thanks for advice so far. here is the correct wireless card.


Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

---

### Post by anewguy on 2011-08-30
This thread has everything you need to get it going - I'd try the part for getting it to work with no internet connection 1st as that worked for me with a similar card on my old laptop.

[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44]("http://ubuntuforums.org/showpost.php?p=10796508&postcount=44")

Post back if you have any questions at all.

I have to take the bus and go to the store to get "fud" (we're in Minnesota) for my "cat" (he really is my best friend so he seems more human than cat to me).  The end result is I'll be away for the couple of hours it takes to do that, but there are plenty of other people who can help as well.

Dave ;)

---

### Post by bkratz on 2011-08-30
> **wozelbeak said:**
> Hi, thanks for advice so far. here is the correct wireless card.


Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

For that card I like this one

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by anewguy on 2011-08-31
> **bkratz said:**
> For that card I like this one

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

That might be better - I noticed it says it's for 11.04, and when I did my old Broadcom on my old laptop there wasn't an 11.04 yet.  I'd try bkratz's way first since it would appear to be more up to date.

Thanks bkratz!

Dave ;)

---

### Post by wozelbeak on 2011-08-31
thanks for your effort guys but i gave up before i read your reply s and installed fedora, which picked up the wireless card on installation.
Fedora running smoothly now.

---

