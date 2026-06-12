---
title: "Avoid reinstalling wireless drivers after Ubuntu Update"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by leomyster on 2011-04-17
Hello All,

I have Acer Aspire 5745 laptop. I have this problem wherein I need to reinstall or re-setup my Broadcom wireless driver every time I run Update Manager. I may be wrong, but I think this is because every time the update manager runs, it updates the linux kernel or the core or something like that. So, for each update, I end up setting the wireless all over again.

In my previous attempt, I updated Ubuntu and forgot the procedure to fix the wireless.

With the very first installation of Ubuntu 10.04, I was able to set up the wireless using this link: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

But, after updating Ubunut, the same procedure does not work.
Wireless is my only way of accessing the Internet, and if I need to download any packages, I have to first get that in my Desktop, and then transfer using a pen drive.

Now, coming to the point. Is there any way I can prevent this? As in, any thing that I can do to prevent reinstalling the wireless drivers, with each update of Ubuntu. 

I really want to keep Ubuntu updated, and do not want to keep re-installing the wireless drivers. Is there anything that I can do here?

I read somewhere about locking package. Will this help? f so, which are the packages that I should lock?

Thanks,
Mithun

EDIT: I have now freshly installed Ubuntu 10.04, since while attempting to re-install the last time after the update, I messed it up, and Ubuntu was not loading! So, with this fresh install, my wireless is now working after following the above mentioned link, and I am raring to go and update Ubuntu. But skeptical, since I do not know how to get the wireless running after the update.

---

### Post by Bucky Ball on 2011-04-17
This would generally happen as a result of updating the Linux kernel. I can't help but I have exactly the same problem with a different card. Kernel update kills it and I have to reinstall drivers manually everytime. Boring. I have a thread about that but it got no action.

Incidentally, if you can get online with a cable your Broadcom drivers should be offered and installed automagically, depending on the card (and I am presuming it's BCM43XX one. ;)

---

### Post by K_45 on 2011-04-17
Scroll down until you get to Synaptic to lock the version:

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

If you can find the package you can look it.

---

### Post by leomyster on 2011-04-17
Hello Bucky,

I am not sure. but I think I have to re-install even the wired drivers after the update. I have Atheros ethernet, and I remember updating that as well.

Currently, with this new installation, I have to install the ethernet driver (Check my earlier thread: [http://ubuntuforums.org/showthread.php?t=1653017](http://ubuntuforums.org/showthread.php?t=1653017)), but i remember that when I updated Ubuntu yesterday, wireless stopped working. So I tried using wired connection, but it did not detect my Atheros again!!

So, wired / wireless - both need re-installation.

@K_45 Thank you for the link. But now, I need to know which packages need to be locked. If you have any idea please let me know.

Thank you all,
Mithun

---

### Post by leomyster on 2011-04-17
Hello Bucky,

I am not sure. but I think I have to re-install even the wired drivers after the update. I have Atheros ethernet, and I remember updating that as well.

Currently, with this new installation, I have to install the ethernet driver (Check my earlier thread: [http://ubuntuforums.org/showthread.php?t=1653017](http://ubuntuforums.org/showthread.php?t=1653017)), but i remember that when I updated Ubuntu yesterday, wireless stopped working. So I tried using wired connection, but it did not detect my Atheros again!!

So, wired / wireless - both need re-installation.

@K_45 Thank you for the link. But now, I need to know which packages need to be locked. If you have any idea please let me know.

Thank you all,
Mithun

---

