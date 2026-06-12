---
title: "Wired Networking possible problem with Gutsy"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by MrLaister on 2008-01-11
I have searched the forum to see if this problem has been posted previously and I couldn't find one like it. However, apologies if this is a re-post.

I have just installed a clean ubuntu gutsy onto a computer which has been running ubuntu since dapper. I noticed when i doft rebooted from windows into gutsy (including the live cd) the network activity light on my hub never lit up. after about 3 hours of internet trawling and finding bugs and their fixes, and still having no luck i resorted to shutting the machine down and physically unplugging it from the wall.

Well surprise surprise the network activity led lit up straight into a ubuntu boot.

The network card is onboard a gigabit motherboard and is in the class RTL-8139/8139C/8139C+ - Realtek

After searching for kernel compatibility it seems like this networking chip is very compatible with linux in general, having 95% of the users saying it works out of the box.

I find it strange that this problem could even occur, and I wonder if anyone has experienced anything similar, or if this is a known issue.

If anyone would like any more information about it, I'll try my best to find out for you :)

-MrLaister

---

### Post by MrLaister on 2008-01-11
After updating from Ubuntu's fresh install to up-to-date packages, I can still create the same problem with the network card.

If i soft reboot from windows into windows everything still works.
If i soft reboot from windows into ubuntu, the NIC won't operate

If I shut the computer down and switch the computer on, the problem still persists.

If I shut the computer down and remove the plug socket for longer than, say, 10 seconds, the problem is removed.

-MrLaister

---

### Post by CLANWIRE on 2008-01-12
> **MrLaister said:**
> After updating from Ubuntu's fresh install to up-to-date packages, I can still create the same problem with the network card.

If i soft reboot from windows into windows everything still works.
If i soft reboot from windows into ubuntu, the NIC won't operate

If I shut the computer down and switch the computer on, the problem still persists.

If I shut the computer down and remove the plug socket for longer than, say, 10 seconds, the problem is removed.

-MrLaister

that looks annoying.

---

### Post by bravemosquito on 2008-01-13
I've got the same problem - SureCOM EP-320X-R with 8139c chip... Before updating everything works fine but after that... :(

---

### Post by moliones on 2008-01-26
This sounds like you may be suffering from a problem described at [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

Specifically, the Wake-on-lan problem

Hope this helps

---

### Post by ugm6hr on 2008-01-26
> **moliones said:**
> This sounds like you may be suffering from a problem described at [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

Specifically, the Wake-on-lan problem

Hope this helps

Agree.  Information on how to fix it:
[http://ubuntuforums.org/showpost.php?p=4077372&postcount=14](http://ubuntuforums.org/showpost.php?p=4077372&postcount=14)

---

