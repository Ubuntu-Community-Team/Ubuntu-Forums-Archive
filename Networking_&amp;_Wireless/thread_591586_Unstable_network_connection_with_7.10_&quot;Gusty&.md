---
title: "Unstable network connection with 7.10 &quot;Gusty&quot;"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by frbe0101 on 2007-10-25
I have a Dell Inspiron 1420, After upgrading to "Gusty" the network manager works fine upon booting up, but when I attempt to change wireless/wired network connections the network setting manager freezes and the connection is lost. According to lshw the wireless network card deactivates and resetting the network via a terminal "networking restart" does nothing, So far only rebooting resets it. If someone could just tell me how to reset it without rebooting that would be helpful, although having a complete solution to the problem would be more appreciated.

---

### Post by josephcherng on 2007-10-25
i have the same problem on my inspiron 1501. Ctrl + Alt + Backspace, then login in again allows the network manager to reappear but i'm not sure if a connection can be made.

also, is it just me or does the wireless connection only go up to 24 Mb/s...no faster.

---

### Post by frbe0101 on 2007-10-25
I have not looked at the speeds yet, but when I log out and log back in it usually is still frozen.

---

### Post by inchaos on 2007-10-25
I'm having the exact same problem with my 1420n.  

It's driving me nuts.  

What to do?

---

### Post by inchaos on 2007-10-25
Also, as to the download speeds, my connection info says I've got 54 Mbps with my router and I just tested my download speed, I've got 2.5 Mbps for that...not bad for cable, eh?

---

### Post by tuaranoi on 2007-10-25
my boss having the same problem on his DELL XPS M1330!

whenever he change location, from house to office, he cannot connect unless reset, the connection will lost sometime after a few hours and if the PC suspend.

---

### Post by frbe0101 on 2007-10-26
My network connection speeds seem to be unaffected. Ok so does anyone have any ideas how the fix it?

---

### Post by Chuckels550 on 2007-10-26
Check Sticky's HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc. at the top of this forum.  Network Manager has been a thorn for quite a few releases.

---

### Post by inchaos on 2007-10-26
This bug has been reported on Launchpad if anyone cares to help us figure it out/confirm it's origin.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154549](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154549)

---

### Post by TheWizzard on 2007-11-03
same problem here.
i don't have networkmanager installed. i'd guess there is something wrong with the drivers of the wi-fi card.

---

### Post by charles woodward on 2007-11-03
There is a problem connecting to wireless networks - and there are a number of threads on this issue.

I've just posted the solution that worked for me (which I picked up from suggestions on various other threads) on the `Problems connecting to network on boot...` thread.  

Try that solution - it worked for me, and it seems to have worked for others too.  Hope you get your connections working soon.

---

### Post by xskater on 2008-01-24
I'm having problems with my network card in my dell n1420, while surfing the web it randomly disconnects and won't let me reconnect unless I restart the computer. Anyone have any ideas on how to fix this?

---

### Post by TheWizzard on 2008-01-24
> **xskater said:**
> I'm having problems with my network card in my dell n1420, while surfing the web it randomly disconnects and won't let me reconnect unless I restart the computer. Anyone have any ideas on how to fix this?

install the manufacturer's drivers.
worked for me (linksys with rt61 chipset).

---

