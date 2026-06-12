---
title: "System fails to boot after adding ndiswrapper to /etc/modules"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by drgatsby on 2007-12-29
I am having a problem with my D-Link wireless card. I am able to get it to work using ndiswrapper and installing the driver. But I have to enter sudo modprobe ndiswrapper followed by iwconfig into the terminal every time I restart to activate the wireless connection.

To solve this problem I entered this into the terminal:

echo ndiswrapper | sudo tee -a /etc/modules

upon restart my computer crashes and fails to boot. It gets stuck at the same point every time. I am able to use ctrl-alt-F1 to get to a command prompt but I am not able to use the gedit command to remove ndiswrapper from the /etc/modules file. I have tried everything I know how to do to get it to boot. Is anyone able to help?

I'm a total newbie so be gentle. It's an old desktop that I wanted to learn to use linux on. I'm running gutsy and it is a current version of ndiswrapper. The wireless card is a D-Link DWL-G510. It is running using the Win98 driver mrv8k51.inf.

Thanks

---

### Post by clayt0njknight on 2007-12-29
try getting to the point you can enter commands again, and input *modprobe -r ndiswrapper*  and restart your box.  let me know what you end up with.

---

### Post by drgatsby on 2007-12-29
I was able to remove ndiswrapper from /etc/modules file using nano.  Now it will boot and everything works fine.  I just need to find another way to get ndiswrapper to load at startup.  I am back to the point where every time I restart I need to enter:

sudo modprobe ndiswrapper

iwconfig


After that the wireless card works great, but I would like to skip that step.

---

