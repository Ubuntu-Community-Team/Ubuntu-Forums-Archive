---
title: "can't get on the net"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by gazoo29 on 2008-07-17
Hey all, I've just installed Hardy on a fresh HDD on my Dell Inspiron 6400.  Problem is Firefox and updating don't work.  Hardware test says full internet connection is established, but update fails and Firefox just says "Looking up...".  I'm using a Motorola SB5101 cable modem w/ ethernet connection and no router.  This makes enjoying Ubuntu very hard.  I'm dying to see differences from windows (especially Compiz).  Can anyone help out a newbie?

---

### Post by schmildo on 2008-07-18
I don't know very much about cable modems unfortunatly. But i'm pretty used to connectivity issues. :)
(problem is i'm using windows at the moment and i don't have access to my linux machine so some of my commands might be a little off)
We'll need to find out more about what's happening with your connection.

Try some of these commands in the console.

ping 203.21.20.20 (or some other internet IP address)
ping [www.google.com](www.google.com) (or some other web address)
arp -a     (i think the 'a' is lowercase i can't remember. this should respond with MAC addresses of any LAN computer your computer has chatted with recently)
ifconfig -a  (this should show a list of all the network adapters you have on the computer and some of the settings)

Post the output of these commands so people here can look at it and help you out.

Rock on.
:guitar:

---

### Post by Francewhoa on 2008-12-27
Rebooting the cable modem worked for me. To do so with Ubuntu 8.04.1:

[LIST=1]
[*]Unplug modem's power cable.
[*]Wait for 30 seconds.
[*]Re-plug modem's power cable. One by one the modem's 4 green lights will blink then stay ON. Whole green lights blinking process takes up to 2 minutes. Orange light will keep blinking that's normal.
[*]*This is an optional step only if above steps don't work.*
Do all previous steps. Then unplug the computer's network cable. Re-plug the computer's network cable. Wait until the Network icon is done processing. Network icon is located at the top right side of your Ubuntu desktop.
[/LIST]
If above doesn't work try same steps without Router.
Modem > Computer

Instead of 
Modem > Router > Computer

The source of the problem is that the modem is still storing the settings from previous computer. Settings such as mac address & system id's from previous operating system (Windows or others). Rebooting the modem fixed this problem.

Thanks to [tturrisi]("http://ubuntuforums.org/showpost.php?p=2793405&postcount=4")

If all of the above don't worked [more solutions can be found here]("http://ubuntuforums.org/showthread.php?t=465423").

---

