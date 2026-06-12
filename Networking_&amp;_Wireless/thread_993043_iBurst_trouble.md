---
title: "iBurst trouble"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by dabraude on 2008-11-25
Hi all

i'm having issues with installing my iburst pcmcia card.

i followed the step by step guide at [https://help.ubuntu.com/community/MobileWirelessBroadband](https://help.ubuntu.com/community/MobileWirelessBroadband)

but when i tried to restart the pcmcia system using the command
```
sudo /etc/init.d/pcmcia restart
```
it came up with a command not found error so i restarted the entire machine

when i enter
```
lsmod | grep ib_
```
it comes up with 4 results:
ib_pcmcia    123000    1
ib_net         8836    1 ib_pcmcia
pcmcia        40876    1 ib_pcmcia
pcmcia_core   40596    4 ib_pcmcia,pcmcia,yenta_socket,rsrc_nonstatic

the sript seems to run fine and i checked that the user name and password are correct

but when i run
```
sudo ifup ib0
```
it returns:

ib0: ERROR while getting interface flags: No such device
ib0: ERROR while getting interface flags: No such device
Failed to bring up ib0

I have triple checked the spelling and numbers in all the files but as a linux newbie i'm now lost as to what to do. thanks for help in advance

---

