---
title: "Command line connects, X apps fail"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by Daenen on 2006-09-28
Hi,

Recently installed Xubuntu Dapper on my notebook and after couple of hours fiddling and configuring mostly have it how I want. Very impressed with this release at first install as I've had a lot of other distros behaving badly or just refusing to install :) 

Originally couldn't get the wireless working at all. I've got a Intel 2915ABG using the ipw2200 driver. After troubleshooting for a while I tried configuring the connection manually using iwconfig and found that eth1 was missing from my interfaces. Added:
```
iface eth1 inet dhcp
```
to the /etc/network/interfaces file. Success!

The only problem is that the network-admin app and wifi-radar (downloaded) both fail to connect. I suspect that they are trying to use the wlan interface but have no idea how to fix this. 

Any help would be appreciated as I'm currently connecting by running a script after boot which is a pain!

---

### Post by Daenen on 2006-10-02
Any suggestions at all? I was hoping it was something simple which might have a quick fix but i guess not :(

---

### Post by az on 2006-10-02
The ipw2200 driver is supposed to be pretty well supported.  I doubt that the problem is that NM is looking for wlan1 instead of eth1.  Why did you not configure the device using the networking tool?  Did it not show up there?

I know that NM used to not use a device if it was already configured - maybe this is your problem?

---

### Post by Daenen on 2006-10-02
Thanks for the reply. After testing to get some more info network-admin is now connecting fine... strange but I'm not complaining :-k 

The only thing I can think of is that i've powered down and up since adding the eth1 entry to my interfaces file a few days ago although I wouldn't have though this would make a difference.

To think I spent the weekend connecting by editing and running a .sh with iwconfig and ifup ](*,)

Thanks again :-D

---

