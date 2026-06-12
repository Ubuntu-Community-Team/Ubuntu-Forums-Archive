---
title: "Overview of wireless networking in Ubuntu using ipw2100"
date: 2004-11-11
forum: Networking &amp; Wireless
---

### Post by 2fargon on 2004-11-11
Hi all,
I was really enthusiastic about Ubuntu and still am. I loved it when I installed Ubuntu, to see that my centrino laptop picked up a wireless internet connection automatically (well, almost).

Now I have a problem using the laptop in different wireless networks.

When I boot up at home, the wireless internet works fine, since I had installed ubuntu while at home, but when I am at school, the laptop does not pick up the wireless connection there. In fact, I have tried a handful of networks, and the wireless seems to work only at home.

Can somebody please refer me to a guide that will tell me how to set-up and troubleshoot wireless networks? What I would really love is a guide that answers the question "How do I get my laptop to detect multiple wireless networks and how do I switch between multiple wireless networks effortlessly?". I hope the answer is not "Use WIndows XP" :P

Thanks folks.

---

### Post by dataw0lf on 2004-11-16
I'm not much for wireless, I'll admit, especially for Linux. Obviously, when your wireless card was detected, an entry into /etc/network/interfaces was added, to include your ESSID, key, etc.  If you want to scan for other networks, iwlist wlan0 scan should do it for you.   Course, if you know the ESSID, channel, etc., of the AP you're trying to access, you can always manually enter it into /etc/network/interfaces.  Read the man pages on the various commands in wireless tools, as well, and you should be well on your way.
dataw0lf

---

### Post by bukdor on 2004-11-29
Do you have the Intel PRO/Wireless LAN 2100 3B adapter in your Centrino? Because that is the same as mine.

And I would install Ubuntu onto it, but I don't know if I should install it onto my laptop. Because I heavily rely on wireless networks.

---

### Post by 2fargon on 2004-12-02
[QUOTE=bukdor]Do you have the Intel PRO/Wireless LAN 2100 3B adapter in your Centrino? Because that is the same as mine.

And I would install Ubuntu onto it, but I don't know if I should install it onto my laptop. Because I heavily rely on wireless networks.[/QUOTE]

Yes, bukdor, and yes, everything works. It is just that I have trouble working with different networks - one at home, one at work and one at starbucks :)

Go ahead and give ubuntu a try, you'll be pleased.

---

### Post by chambery on 2004-12-06
If (like me) you don't want to become an expert in Linux wireless network configuration and save some time poring over man pages and obtuse command output, grab **netapplet** from Synaptic.  I'm still having trouble connecting to networks/internet, but it does make configuration and switching between network adapters simple.

---

