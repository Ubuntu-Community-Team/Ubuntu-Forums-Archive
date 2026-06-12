---
title: "Wired LAN problems. This will be an easy fix for some one!"
date: 2015-05-13
forum: Networking &amp; Wireless
---

### Post by Martin_Ormerod on 2015-05-13
Hi Everyone!
I did search the forums and then I went to the library and checked out several books too! (Ubuntu Unleashed by Matthew Helmke, Ubuntu Server by Kyle Rankin to mention a couple)
This may be the easiest fix ever and it may just be a simple hardware issue...

Here we go!

I want to create an Ubuntu LAN with no internet connection. I went to Goodwill and bought 4 identical machines. I loaded Ubuntu 14.04 on all of them. I plugged all of them into a Netgear GS105 switch. Next, I named them Server, Client1, Client2 and Client3. I created shared folders on all four machines. Rebooted everything. Clicked on "Browse Network" - "Windows Network"
Sure enough, nothing there. Wasnt really expecting it to be quite that simple.
So..
Before I start with the terminal and ifconfig, ethtool, etc. Is there a glaring, noob mistake here? Is this how a LAN would be constructed hardware wise? Im fairly happy using the command line but just want to make sure the hardware is in place before wasting anyone's time.
Have mercy on me, guys. Dumping Windows was an exciting yet daunting step for me!
Thanks!

---

### Post by tgalati4 on 2015-05-14
Welcome to the forums.  If the usernames are identical on each machine, then the shared folders should show up automatically.  What version of Ubuntu did you install?  To have other computers see a folder share, you need to be running *avahi*:

```
ps -ef | grep avahi
```

It might look something like:

> tgalati4@Mint17 ~ $ ps -ef | grep avahi
avahi      680     1  0 Apr22 ?        00:00:04 avahi-daemon: running [Mint17.local]
avahi      681   680  0 Apr22 ?        00:00:00 avahi-daemon: chroot helper
tgalati4 11828  2415  0 06:57 pts/2    00:00:00 grep --colour=auto avahi


To make server operations easier, one normally sets up a static IP address on the server.  The clients can still be on dhcp.  It's also helpful to put the server's IP address and name in /etc/hosts.

Some more reading:

[https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)

[http://askubuntu.com/questions/338442/how-to-set-static-ip-address](http://askubuntu.com/questions/338442/how-to-set-static-ip-address)

[https://help.ubuntu.com/stable/ubuntu-help/net-fixed-ip-address.html](https://help.ubuntu.com/stable/ubuntu-help/net-fixed-ip-address.html)

---

