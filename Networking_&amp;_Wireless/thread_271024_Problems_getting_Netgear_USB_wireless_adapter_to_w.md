---
title: "Problems getting Netgear USB wireless adapter to work"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by Lynswin on 2006-10-04
Hi

I am completely new to Linux and have managed to install Ubuntu onto my old PC. However, I am having a problem getting my Netgear WG111T usb wireless adapter working. I have tried to install the windows XP drivers (wg11tnd5.sys, netwg11t.inf, athfmwdl.sys, athfmwdl.inf) but I not getting the results I need. The story so far: Copied the Win XP drivers from the CD to my USB device (on other PC) then copied them to the Desktop in Ubuntu. Made a new directory (windriv) and tried to copy the drivers over. All seemed to go OK but the wg11tnd.sys file stayed on the desktop. Ignored that and went on to install the drivers using ndiswrapper and when I used 'sudo ndiswrapper -l' I get the following: athfmwdl = driver installed hardware present, netwg11t.inf = invalid driver and wg11tnd5.sys = invalid driver (not sure why the .sys is on the end of this when none of the others have the extension listed - maybe this is significant). I have tried to copy the wg11tnd5.sys driver over to the windriv directory again and then I get 'cannot overwrite directory '/home/lynda/windriv/wg11tnd5.sys' with non-directory'. I am so confused as I don't really know what I am doing. Please don't assume I know anything about Linux, ndiswrapper or the terminal console as I have just literally followed a 'step by step' guide to install these drivers and unfortunately the guide did not account for these errors!!
Any help would be greatly appreciated.
Thankyou
Lynda

---

### Post by Crooksey on 2006-10-04
The ndiswrapper only wants the .inf drivers, so remove all the invalid ones, then type "man ndiswrapper" to learn howto finish the process of.

When you come to ndiswrapper -d, you need to run lspci, to see what rev your card is, then  type lspci -l to see what your device id is, in the form of xxxx.xxxx, hope that helps.

---

### Post by Lynswin on 2006-10-04
Many thanks for your help. But I am still having a problem.

When I try to remove the 'invalid drivers', by typing 'ndiswrapper -e xxxxxxx' I get 'permission denied'.

Can you help any more?

Thanks

Lynda

---

### Post by Lynswin on 2006-10-04
Sorry to reply to my own thread but I have managed to uninstall and re-install the drivers and now when I type 'ndiswrapper -l' my drivers are installed and hardware present. If I then type 'modprobe ndiswrapper' (not sure why but that is what it says in the guide I am following) nothing happens (not sure if it supposed to). Then I type 'iwconfig' and I get 'no wireless connections' and no 'wlan0'.
Can someone tell me what is going wrong or where I go from here?

Thanks

Lynda

---

### Post by Lynswin on 2006-10-05
Anyone?

---

### Post by Lynswin on 2006-10-05
Looks like Microsoft win again :(

---

### Post by blkdragon on 2006-10-16
what? microsoft win again?

AGAIN?

this has got to stop.

have you configured the actual device properly?

go into network connections and try to let it auto detect, of just type in your own settings for "wan0" or whatever.

NB: if this sounds like i have no idea about what im talking about, its right. I have absoloutely no idea. But following general "troubleshooting" rules, you should be able to make it work.

remember: google is your best friend.

---

