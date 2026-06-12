---
title: "Bluetooth kills wireless connection in Gutsy on T42"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by tedrogers on 2007-12-21
Hi all,

Was so pleased to finally get my Bluetooth working on my IBM T42 in Gutsy, but now everytime I turn the bluetooth radio on (Fn + F5 for me) it will kill the wireless connection.

I can see in the network manager applet that it is still seeing my wireless router, but no amount of attempts will result in a successful connection.

The only fix so far is a full power down  reboot. A simple restart of X does nothing to solve the issue.

Any ideas anyone?

Thanks.

---

### Post by TahirH on 2007-12-23
Hello, 

I was having the same issue earlier today.

I switched on my bluetooth adapter (Fn+F5) and the wifi connection went down.

I tried to reconnect and that didn't work, I switched off the bluetooth adapter (Fn+F5) and then tried to reconect to the wifi network and that still didn't work.

In the shell I did "sudo ifconfig eth1 down". Then "sudo ifconfig eth1 up". 
Then I tried to reconnect to the wifi network with the KNetworkManager using the gui.
Still no joy. I then tried Fn+F5 again and by if by magic the wifi reconnected (the bluetooth adapter did not come on, it stayed off).

I think that the bluetooth adapter messes something up on the wifi adapter (probably a hardware issue).

Tahir

---

### Post by tedrogers on 2007-12-24
Well thanks for your input TahirH....my experience is exactly the same.

I wonder if anyone out there has a fix for us...something that is more tidy?

---

### Post by tedrogers on 2007-12-27
Bump Bump Bump!

---

### Post by tedrogers on 2007-12-30
What a weird thing....just hitting Fn + F5 a few more times while trying to reconnect to my wireless router seems to make it work.

This is clumsy as hell, but it works.

A solution / fix would be welcome....but at least I don't have to reboot now.

---

