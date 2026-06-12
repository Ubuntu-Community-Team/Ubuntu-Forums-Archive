---
title: "Zyxel ZyAir G-220 works on server not desktop"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by ferreter on 2007-11-21
Hello,

I'm able to get my zyxel usb wireless adapter working just fine on a server install of 7.10 by setting up the wireless information in /etc/network/interfaces. This includes setting up like so:

auto eth2
iface eth2 inet dhcp
wireless-essid *my-essid*
wireless-key *mywireless-key-in-hex*

On reboot this interface comes up without issues every time. 

Now on ubuntu/kubuntu workstation, it never comes up automatically. I have to jump through hoops to get it to work correctly. First I have to bring the interface down, then I have to manually enter in the iwconfig command with all relevant information at a command line, then I bring it back up again and it works.

The only difference I see is this ieeesoftmac module which the zd1211rw module seems to load with. That and the network-manager as well. I'm totally stumped as to why this keeps occurring. It would not be so bad if I wasn't setting up the laptop for a person who never would want to deal with the command line. 

For the record, on the desktop I used some of the pre-up lines in the /etc/network/interfaces file to try to fix the issue with little difference. I also removed network-manager and then I was never able to get connected no matter what I did. Am I to guess that I have to do the whole wicd thing to get this to work or is there anyway to get this to work with the native services? Other boot CDs work just fine as well.

Thanks!

---

