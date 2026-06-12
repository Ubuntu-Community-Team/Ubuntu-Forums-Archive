---
title: "wireless does not show in network manager"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by iansane on 2008-07-13
Hi, I used the how to in wifi ubuntu documentation to install ndiswrapper and then installed driver for netgear wg111 through ndisgtk.

I also blacklisted the generic drivers in ubuntu so they would not conflict.

Now there is no wireless network in network manager and when I try to configure from ndisgtk the unlock is greyed out.

It also tells me, "unable to look up session information for process 6770 network-admin" and that's when I'm running ndisgtk as sudo.

When I first plugged the usb dongle in, before installing the driver, I had nice wireless signal indicator and it showed all available networks as if the generic driver was working. After about 5 minutes it would just disapear. It would show back up after unplugging and plugging the dongle back in. Now it won't even do that.

ndis shows driver installed and hardware present but it seems to have installed the driver awfully fast. As soon as I clicked on the inf file it said driver installed in less than a second so I'm wondering if it is really installed.

Any suggestions?

Thanks

---

### Post by Tom--d on 2008-07-13
Try 
```
sudo modprobe ndiswrapper
```
and then see if wireless is working.

If not, reboot and see.

---

### Post by iansane on 2008-07-13
no luck. Actually modprobe was part of the how to but I tried it again and then rebooted but still nothing. Do I need to disable my wired nic card? If so, how do I do that and then reinable it if I need to to get back on line?

I should mention that I am using 64 bit hardy in case there's a known issue.

---

### Post by Tom--d on 2008-07-13
That could be the problem.

Do you have the 64 bit driver and 64 bit ndiswrapper?

---

### Post by iansane on 2008-07-13
well there is only one driver available. I'm assuming it is 32 bit since it is version 1 so this might be hopeless on a 64 bit system. I hate to revert to 32 bit ubuntu since 64 bit runs virtual machine better.

Also I have ndiswrapper from synaptic. It wouldn't give me the 32 bit version would it?

I may have to go back to 32 if I want to use this wireless.

Thanks for the response

---

