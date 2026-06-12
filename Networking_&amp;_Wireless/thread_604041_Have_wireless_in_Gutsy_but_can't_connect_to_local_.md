---
title: "Have wireless in Gutsy but can't connect to local network"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by mjezell on 2007-11-05
I'm having a strange problem with a clean installation of Gutsy on my Aspire 5000 laptop.  I have my wireless up and running with a good internet connection.  The problem I'm having is connecting to my local network (home).  I've disabled IPv6 and do not run network-manager because all my machines are setup with static IPs.  My wireless driver is bcm43xx and is connecting fine (although I have to re-enter my passcode, WPA1, after each reboot).  I have a mythbox running Feisty server that is connected to the internet wirelessly that I'm able to access through my local network (ssh).  All of my wired boxes are accessible including one XP box.  Ran Gutsy tribe 3-5 on this laptop with mostly successful wireless connections to internet and local network before doing a clean install.  I'm probably missing something simple but am stump at this point. Any suggestions would be appreciated.

---

### Post by gilf on 2007-11-05
Maybe check the contents of  /etc/network/interfaces in your installed system.

Check this against the version on the LiveCD when running that. If it works in live CD but is different in the HD installed version, you might try reverting it to the CD contents. Back up your file before changing it.

Don't know if this will have any effect since you aren't using network manager -- but it does seem to help those problems.

---

### Post by mjezell on 2007-11-05
Thanks for the reply.  Solved my problem by disabling the wired NIC connection.  Don't remember having to do this before but I now have access to my local network.  I think the routing table is set up wrong and I'm trying to figure it out.  Thanks for the input.

---

