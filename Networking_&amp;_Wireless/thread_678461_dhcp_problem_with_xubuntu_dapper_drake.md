---
title: "dhcp problem with xubuntu dapper drake"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by casinohawk on 2008-01-25
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=387421](http://ubuntuforums.org/showthread.php?t=387421) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				i recently installed xubuntu 6.06.1 & i can't seem to access the internet. During installation it said my  connection wasn't configured for dhcp. I've tried a few solutions from other posts  but to no avail. one solution said to add 

auto eth0

to

iface eth0 inet dhcp

in the file /etc/network/interfaces
so it should look like this:

auto eth0
iface eth0 inet dhcp

in the file /etc/network/interfaces  that line didn't seem to be in that file. my file says:

# The loopback network interface
auto lo
iface lo inet loopback

i also used the network desktop interface to "activate" the connection & the system froze up.
I'm new to this so any help would be appreciated.thankshttp://ubuntuforums.org/images/smilies/guitar.gif
:guitar:

---

