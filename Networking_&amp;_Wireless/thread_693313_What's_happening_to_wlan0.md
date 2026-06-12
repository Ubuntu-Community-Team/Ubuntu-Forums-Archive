---
title: "What's happening to wlan0?"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by tlinux on 2008-02-10
In Kubuntu 7.04 sometimes when I boot up I can connect to the Internet and other times I can't. I'm tryiing to connect using a wireless USB adapter. On the times when  it doesn't work, wlan0 does not appear in System Settings->Network&Connectivity->Network Settings->Available Network Interfaces. Only eth0 is shown. When I can connect to the Internet, wlan0 is also shown in the Available Network Interfaces. 

This problem has been occurring at random intervals ever since I got Kubuntu connected to the Internet wirelessly.

What's causing this problem, and more importantly, how can I solve it?

Thank you.

---

### Post by dmizer on 2008-02-10
while the adapter is working, please post the output of the following commands:

```
lsusb
lsmod
ifconfig
```

while the adapter is not working, please post the output of the following commands:
```
lsmod
dmesg
```

---

### Post by tlinux on 2008-02-11
The output when the adapter is working is shown in:

         [http://pastebin.ca/899533](http://pastebin.ca/899533)

I can't get it to fail at the moment. It was out for the last several days, but it started working again this afternoon. I'll keep checking and will post the output when it fails.

---

### Post by tlinux on 2008-02-11
Surprise! The attempt to connect to the Internet failed the very next time I tried it. The output from the requested commands is in the pastebin at:

[http://pastebin.ca/899549](http://pastebin.ca/899549)

I hope this will be of value to you in diagnosing my problem.

Thank you.

---

### Post by dmizer on 2008-02-11
looks like the native module is being dropped, and is flaky.  from your dmesg:
```
[   37.078547] driverloader: module license 'see LICENSE file; Copyright (c)2003-2004 Linuxant inc.' taints kernel.
[   37.078857] Symbol usb_register_driver is being used by a non-GPL module, which will not be allowed in the future
[   37.078860] Please see the file Documentation/feature-removal-schedule.txt in the kernel source tree for more details.
[   37.079481] Symbol usb_deregister is being used by a non-GPL module, which will not be allowed in the future
[   37.079483] Please see the file Documentation/feature-removal-schedule.txt in the kernel source tree for more details.
```

follow this howto for implementing ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Device/WG121](https://help.ubuntu.com/community/WifiDocs/Device/WG121)

and a few additional follow up directions listed here:
[http://ubuntuforums.org/showthread.php?t=583690](http://ubuntuforums.org/showthread.php?t=583690)

good luck, post if you are successful, or if you need more help.

---

### Post by tlinux on 2008-02-11
I'm not using ndiswrapper. I'm using the Linuxant wrapper. What should I do with it?

---

### Post by dmizer on 2008-02-11
follow step two in the howto i linked to above.  also, follow step 1 in the second thread i linked to.  reboot, and you should have better results.

---

### Post by tlinux on 2008-02-11
I followed your recommendations but they didn't work. First, I tried to execute 

               gksudo gedit /etc/modprobe.d/blacklist

but got an error message. That message is shown in the pastebin:

              [http://pastebin.ca/900288](http://pastebin.ca/900288)

However, I was able to find the blacklist file and edit it with kate. Here's what I wound up with:

              [http://pastebin.ca/900292](http://pastebin.ca/900292)

It looks to me like the file is the way the "howto" says it should be.

What should I do now?

Thank you.

---

### Post by dmizer on 2008-02-11
reboot and see if you continue to have the problem.  if not, you're fixed.

if you are still having the problem, it could be the Linuxant wrapper you're using.  you may have more success with the ndiswrapper solution instead.

edit:
actually, you might also try this before trying ndiswrapper (posted in the second thread)
> **ShahBucks said:**
> [SIZE="2"]Finally I just changed the name of the **'wireless'** directory in **/lib/modules/[COLOR="Red"]2.6.22-14-generic[/COLOR]/ubuntu** to '**wireless_old**' so it wouldn't conflict with ndiswrapper. That seems to work fine so far. If anyone else has a better fix, pls. let me know! Thanks![/SIZE]

replace 2.6.22-14-generic with what you find for your own computer under the output for the following:
```
uname -r
```

---

### Post by tlinux on 2008-02-11
Now I'm really screwed! I made the changes as best I understood them, and now Kubuntu is frozen up. I can't get into it even in safe mode. I think the problem occurred because of the change in name of the 'wireless' directory. Maybe I did something wrong, but there's no way to get back into the system and change anything. I think I have two options. I could reinstall Kubuntu or I could just forget it and erase the whole thing. 

Right now the second choice seems best. I've been working with Kubuntu for about two years and have had nothing but trouble. Nothing ever works like it's supposed to at first and trying to find out what the problem is and then fixing it is time consuming and frustrating! A couple of days ago I tried to burn a CD, but K3b failed. Don't know why. I spend more time trying to get Kubuntu to work properly than I do actually using it.

Thanks for your help anyway.

---

### Post by dmizer on 2008-02-12
if you're still interested, you could boot with an ubuntu or knoppix live cd, and correct the changes you made.  or, at the very least ... retrieve important files.

if not, i'm terribly sorry for having brought you to this unfortunate conclusion.

---

