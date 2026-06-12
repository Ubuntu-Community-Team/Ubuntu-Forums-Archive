---
title: "Wake-On-Lan issue with Realtek r8169: immediate resume after suspend"
date: 2014-07-10
forum: Networking &amp; Wireless
---

### Post by weatherman2 on 2014-07-10
I have two systems with the same integrated network card, a Realtek R111E.  I am trying to get Wake-On-Lan (WOL) to work reliably on both of them, to wake up from suspend over the n etwork.  I have used WOL before with other hardware reliably.

On one system I have Ubuntu 12.04.3.  On the other, I have 14.04.  The behavior is the same on both systems.

Ubuntu loads the r8169 driver.  I make sure WOL is enabled with ethtool.  I suspend, and I am able to WOL successfully by sending the magic packet from another computer.

The problem is that when I WOL and then suspend again, the system suspends and then immediately wakes up.  If I then suspend again immediately, it will stay asleep this time.  Then WOL will work to wake it up again.

This seems to happen only if WOL was used to wake up the system last time - like the magic packet is still there and seen again immediately.  If I wake it up say with the power button instead of WOL, then suspend again, I never get the immediate wake-up.

I tried downloading Realtek's version of r8169 and also r8168.  The problem persists.

I've also tried disabling WOL after resume then re-enable it.  The problem persists.

I don't have this issue with other network cards, in other versions of Ubuntu.

Any ideas?

---

### Post by weatherman2 on 2014-07-10
After some trial and error, I solved my problem by unloading the network card driver (r8169 in my case) and re-loading it, both after resume.  I also had to restart Network Manager because it didn't like that the module had been removed. 
 
[Edit #1: My Realtek network card is identified in Linux as "RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller" but for some reason the r8169 module gets used for it by default.  I found that building the Realtek module r8168 - download from Realtek's website, easy to find a Linux driver that works in Ubuntu up to/including 14.04 - works better than r8169 with my solution below.  It's easy to build the driver using the included script, but you must blacklist r8169 and add r8168 to /etc/modules to use the r8168 at each boot.]

[Edit #2: I found that in Ubuntu 12.04.3 that stopping network-manager and then starting it after the modprobes instead of just restart eliminates an error message, so I changed that below too.]

Here's what I did:

Create a file with your favorite text editor - say gedit - and call the file say "89_wol_reload_network_mod" - in the directory /etc/pm/sleep.d (you need to be sudo to do it):

```

gksu gedit /etc/pm/sleep.d/89_wol_reload_network_mod

```

and in the file put this:

```

#!/bin/sh

case "$1" in
    thaw|resume) 
    service network-manager stop
    modprobe -r r8168
    modprobe r8168
    service network-manager start 
        ;;
    *) exit $NA
        ;;
esac


exit 0

```

Then make the file executable:

```
sudo chmod o+rwx  /etc/pm/sleep.d/89_wol_reload_network_mod
```

---

### Post by kirenpillay1 on 2015-03-12
Thanks very much, your post solved the problem for me. WOL on the R8169 driver did not work at all for me.
After installing the driver and carrying out your steps, my PC now wakes from suspended state and cold boot perfectly.

---

### Post by laborer on 2015-05-07
Thanks a lot, weatherman2!  I had the exact same problem as yours on a HP Pavilion 500 desktop computer with Ubuntu 14.04.  Although your solution doesn't solve my problem, a slightly modified version of the script works perfectly.

```
#!/bin/sh

case "$1" in
    hibernate|suspend)
        service network-manager stop
        modprobe -r r8169
        ;;
    thaw|resume) 
        modprobe r8169
        service network-manager start 
        ;;
esac
```

---

