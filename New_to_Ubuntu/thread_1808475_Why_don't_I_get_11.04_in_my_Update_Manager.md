---
title: "Why don't I get 11.04 in my Update Manager?"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-07-20
Hello everybody. :)
Well, the title says it all. I have 10.04 in an Acer Aspire 5000, and am loving every minute.
Yesterday, I learned about 11.04. In the Ubuntu webpage it says I should get it on the Update manager (like I got 10.04), but it's not happening. 
Why? And how do I get it?

Thanks in advance. :)

---

### Post by halitech on 2011-07-20
you should only get a notification for the next version so if you have 10.04, the notification would be for 10.10, not 11.04. I think you need to turn that notification on in the update manager before you get it.

---

### Post by Inodoro Pereyra on 2011-07-20
Thanks for the quick reply.
How do I do that?

---

### Post by coffeecat on 2011-07-20
Open Update Manager, then click on the Settings button -> Updates tab. Under release upgrade at the bottom of the Software Sources window, change "Long Term Support Releases only" to "Normal Releases". Close the Sources window and refresh the metadata by clicking on the Check button. But as halitech points out, you will be prompted to update to 10.10 before you can update to 11.04.

---

### Post by Inodoro Pereyra on 2011-07-20
Just did. Thank you both. :D

So I'm guessing after this update I should be prompted to update to 11.04, right?

---

### Post by Swagman on 2011-07-20
If your using wubi then be prepared for..... issues.

---

### Post by halitech on 2011-07-20
after you get finished with the 10.10 update, then yes, you should get prompt for 11.04.

---

### Post by Inodoro Pereyra on 2011-07-20
Thanks again.

What are the...issues Swagman is talking about? I'm running XP Sp3 on my laptop, and 7 Ultimate Sp1 on my desktop.

---

### Post by Swagman on 2011-07-20
doing distro update in Wubi is known to have issues.. like b0rking !!

If you have anything you want to keep in your ubuntu install then move it over to your windows drive whilst you do the upgrade.. just in case

[edit]

I must be seeing things.. I thought I read you were using wubi

---

### Post by halitech on 2011-07-20
if you are using WUBI to run Ubuntu, it means it is running in a virtual file system which can be ... unstable so to speak

---

### Post by coffeecat on 2011-07-20
Swagman makes a good point. Are you using Wubi? If so, I'll point you to a thread you ought to know about.

Also - do have plenty of spare bandwidth? Can you afford to download an Ubuntu 11.04 ISO? If so, I suggest you do so, burn the ISO to CD and run it live before doing the upgrade to 11.04 - just to make sure there are no issues with your hardware and 11.04. I believe there is an option to upgrade a 10.10 system to 11.04 from the CD but I've never tried it.

---

### Post by Inodoro Pereyra on 2011-07-20
At this point, I'm getting more and more confused about what "wubi" means. In both computers I installed Ubuntu from inside Windows. From XP in my laptop, and from 7 in my desktop. Is that wubi?

Swagman: borking???:confused:

Coffeecat: No, I don't have the bandwidth. :(

---

### Post by Swagman on 2011-07-20
**YES** you **ARE** running a wubi install

b0rking means... breaking it !!

---

### Post by halitech on 2011-07-20
> **Inodoro Pereyra said:**
> At this point, I'm getting more and more confused about what "wubi" means. In both computers I installed Ubuntu from inside Windows. From XP in my laptop, and from 7 in my desktop. Is that wubi?

Swagman: borking???:confused:

Coffeecat: No, I don't have the bandwidth. :(

it would probably be less bandwidth to download the 11.04 ISO then to download updates for 10.10 and then 11.04

---

### Post by Inodoro Pereyra on 2011-07-20
Hmmm...I think I'm gonna upgrade on my laptop for now, until I'm sure everything goes well, and then make the jump on the desktop. 

Thanks again everybody. You guys are the best! :D

---

### Post by Inodoro Pereyra on 2011-07-20
> **halitech said:**
> it would probably be less bandwidth to download the 11.04 ISO then to download updates for 10.10 and then 11.04

I'm downloading 10.10 right now, at a whooping...16 Kb/s! :(
When I tried to download the Ubuntu ISO (9.10), it spent hours trying, to finally tell me it couldn't do it, and I ended having to request the CD by mail.

---

### Post by halitech on 2011-07-20
ugg, you on dialup? might be worth requesting an 11.04 cd as well if you are that slow

---

### Post by linuxman94 on 2011-07-20
> **halitech said:**
> ugg, you on dialup? might be worth requesting an 11.04 cd as well if you are that slow

You'd have to buy it now because canonical no longer offers shipit

---

### Post by Inodoro Pereyra on 2011-07-20
> **halitech said:**
> ugg, you on dialup? might be worth requesting an 11.04 cd as well if you are that slow

Worse. I'm on wi-fi.:lol:
Just the crappy router my landlady bought (802.11**b, **of course), for the 5 people living in my house. 

> **linuxman94 said:**
> You'd have to buy it now because canonical no longer offers shipit

Yet another reason not to get it. :(

---

### Post by halitech on 2011-07-20
> **linuxman94 said:**
> You'd have to buy it now because canonical no longer offers shipit

ahh, didn't know that, last version I got shipped was 8.04

---

### Post by RpDn on 2011-08-12
If you don't mind, I just thought I'd ask through this topic, a little followup for more clarification...

I have a Toshiba laptop, multi-booting XP, Win7, Splashtop, and Meerkat 10.10... and Meerkat's update-manager says there's an upgrade to Narwhal 11.04.

Would that be the best method... to let the **update-manager** upgrade the wubi'd Meerkat installation to get to Narhwal (besides the risks in any software update) ...and preserve the current desktop/settings/apps, etc?

I mean... the update-manager would upgrade Meerkat "in place" to Narwhal... totally ignoring the Windows environment, etc, yes? (and the fact that it's a WUBI install!?)

And that would be better than an ISO CD or another WUBI... in order to keep the existing desktop/software and simply upgrade to Narwhal... or ...can one 'upgrade' a WUBI setup from ISO or newer WUBI?  An ISO CD install or WUBI install is going to be a fresh installation, isn't it... and wouldn't preserve the current desktop/personal/apps installed? (Not that I've done that much with it, but set up apps.) Although running 'live' from CD, totally separate from current Meerkat, would be a good hardware test of Narwhal on my system.

If it was a straight Meerkat only system, I'd just go for it... but having a WUBI setup complicates things, so I thought I'd check.  I'm ok with repairing Windows multi-boot... if Ubuntu gets borked then I'd just live with that and do a fresh WUBI Narwhal install, etc.

To boil it down... even though it's a WUBI setup, ***update-manager*** is the best way to upgrade it to a new major version, yes?

(And you say there's a thread on the 'issues'? ;))

Thanks

---

### Post by coffeecat on 2011-08-12
@RpDn, there are two main issues to consider.

The upgrade from 10.10 to 11.04 itself.

Special considerations regarding wubi.

Upgrading from 10.10 to 11.04 using the update manager should be painless, despite some reports to the contrary that have appeared on this forum. I have done it myself, leading to a perfectly good 11.04 installation. The problems that are reported may be due to specific hardware issues or a heavily-customised system which has affected the upgrade process.

Specific problems with wubi are mostly to do with the grub bootloader. The thread you refer to is probably the wubi megathread:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

The good news seems to be:

> With the release of 11.04, it appears that the major issues affecting Wubi installs are over.

But you would be wise to read at least the first post in that thread.

Before upgrading, a couple of sensible precautions. Back up all important data. Then, if something goes badly wrong, you can always do a fresh install and restore your personal files. This advice would apply to both wubi and non-wubi installs, and to Windows and MacOS for that matter.

Secondly, you might want to download the 11.04 ISO, burn it to a CD and run it live to exclude the possibility of hardware problems with your particular setup and 11.04.

---

### Post by RpDn on 2011-08-12
Thanks for that advise... such upgrades give me more timely reason to do backups ;)... though I anticipate a good upgrade; I haven't worked Ubuntu more than basic apps setup, duplicating casual desktop use, yet. I'll run the ISO to preview too... maybe from USB if I can, for fun.

---

