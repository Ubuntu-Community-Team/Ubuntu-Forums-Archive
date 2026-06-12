---
title: "pptpconfig kills internet access"
date: 2005-05-12
forum: Networking &amp; Wireless
---

### Post by plockery on 2005-05-12
I am running pptpconfig gui and can connect to my microsoft work vpn with no problems.
But when I stop pptpconfig and quit the program, the internet is no longer available.
The network is said to be unreachable.
I can ping my ADSL modem (1500 mbs broadband) but no internet sites at all.
If I start pptpconfig again it then tells me the network is unreachable too.
The only way of getting out of this to recover the internet is to reboot the computer.
I have pptpconfig set to "all to tunnel" which as far as I know is the only way it will work.
My guess is that for some reason the program is not releasing the tunnel once the program quits.
So all intenet access is cut off.
Can anyone tell me:
1. What is going on?
2. If there is a way I can recover the internet (kill a process or some other way) from the command line without having to reboot the computer?

Peter.

---

### Post by plockery on 2005-05-13
This problem seems to have resolved itself.
Internet is working again after quitting pptpconfig.
So not sure what the problem was.
Will have to keep monitoring it if it happens again.

---

