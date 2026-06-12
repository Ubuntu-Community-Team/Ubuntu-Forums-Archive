---
title: "All of a sudden after reboot nm-applet says no nerwork connection but?"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by orb9220 on 2006-08-29
I am connected and posting right now ath0 is enabled and connected to my default ssid but why all of a sudden does nm-applet say no network connections?

Any help on this I am ready to give up on nm-applet because of past issue's and no one answering on these forums I guess no one new the answer's.

1) nm-applet on reboot would try to connect to an ssid of USOUTDOOR that was not as strong a signal as my default. And know matter how many times I connected to my default ssid and rebooted it would go back to the one I  don't use why?

2) No way to remove ssid's from the list so it displays only one's you want again why?

3) When I run nm-applet in xfce instead of default gnome then it runs three instances of itself which is probally a xcfe issue but still can't an answer on it.

4) version 0.6.2 still in repos even tho 6.3 was released in june and 6.4 in july. 

These are my beefs with this program, I kind of like it and want to continue to use it but I don't see anything being done in a hurry to improve or fix it.

Any help is greatly appreciated.

Well I went in and look at my gedit /etc/network/interfaces
and all of sudden these lines were added to bottom of file and I don't know why?

I just commented them out and rebooted and blingo-blamo it worked. Am a bit puzzled tho on how they got thier.

iface ath0 inet dhcp
wireless-essid [www.personaltelco.net](www.personaltelco.net)

auto ath0

---

### Post by dhaneshr on 2006-08-30
I have a similar problem running Dapper on a Dell D600 and the Intel IPW2100 wireless device. I have been using Ggnome-network-manager for some time without problems. These past few weeks though, I have been able to connect to my AP without any problems, but nm-applet shows that there are no wireless connection available ? How is this so ? 

I am dumbfounded.

---

### Post by dhaneshr on 2006-08-30
Hi orb,

I did exactly the same thing as you, editing the /etc/network/interfaces file and now nm-applet is back up-to-speed. Thanks for your tip man.

dhaneshr

---

### Post by Slothman on 2006-08-30
Thankyou Thankyou Thankyou!!! I've been scratching my head over this one for days now and wasn't getting anywhere!! Network Manager wasn't picking up my wireless card or even giving me the option of creating a new wireless connection... After looking in /etc/network/interfaces i found these lines

iface eth1 inet dhcp
wireless-essid My ESSID
wireless-key s: XXXXXX

auto ath0
iface ath0 inet dhcp

I simply commented these lines out (god knows how they got there) and rebooted and network manager worked fine, and i'm glad to say that i'm writing this post using my wireless connection 8)

Thanks again for the post Orb9220 :-D

---

### Post by wcattey on 2008-03-06
It was a bit unclear which lines you meant by "these".

Apparently commenting out EVERYTHING  in /etc/network/interfaces except:

auto lo
iface lo inet loopback

remedies the problem.  Or at least it did for me.

---

