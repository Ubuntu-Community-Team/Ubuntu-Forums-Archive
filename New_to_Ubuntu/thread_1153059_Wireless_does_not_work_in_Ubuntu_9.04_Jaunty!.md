---
title: "Wireless does not work in Ubuntu 9.04 Jaunty!"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by dvl300 on 2009-05-08
I have recently installed Ubuntu 9.04 Jaunty
and i went through the usual installments of
installing all the repositories and packages
needed to install and run ndisgtk
(downloaded in windows and copied to pendrive
as i only have wireless!)

Copied the windows .inf driver,installed it in
windows wireless driver get an error along the
lines of it cant find the hardware?

But after you ignore it
it says that the hardware is present in the main
window of window wireless drivers

Is it not working because i did it through wubi?
although i wouldn't of thought it made any
difference?

Downloading the ISO now! as wubi installs amd64
type which my PC i built does support but i
prefer I386!

I also add privileges to both root and my own
user to connect to wireless and tried the vista
driver instead of xp and it still will not work!

Ran lsusb in terminal it shows that my USB
wireless adapter(buffalo UC-G300N)is
connected and detected also when i click
config in windows wireless driver it comes
up with it can't find the configurator!

And my previous version of Ubuntu 8.04
worked just fine with my wireless
adapter!, is this just a bug! or have i
done something wrong? don't think so?
though!
:confused:
Thanks
DVL300

---

### Post by Nxion on 2009-05-08
Well you might wanna give this a try.
[URL="http://ubunturt2870.pbworks.com/FrontPage"]
http://ubunturt2870.pbworks.com/FrontPage[/URL]

---

### Post by dvl300 on 2009-05-08
no good

---

### Post by Nxion on 2009-05-08
> **dvl300 said:**
> no good

Can you give me more info other than "no good". If we don't have the info why it does not work then we can't diagnosis the issues and resolve the problem.

---

### Post by dvl300 on 2009-05-08
i have an buffalo UC-G300N wireless usb adaptor not a ralink
and i only have wireless

---

### Post by tomszyszko on 2009-05-08
If yoy installed today, you may be experiencing the wireless bug caused by a missing package for the new kernel. If you run update manager from an ethernet connection you may fix the problem and be able to use a native linux driver.

---

### Post by superprash2003 on 2009-05-08
also post output of **lshw -C network** from the terminal

---

### Post by dvl300 on 2009-05-08
okay back in 5!

---

### Post by Nxion on 2009-05-08
Yes you do have an Buffalo UC-G300N. The wireless adapter you are using has a ralink chipset. This is the reason why I attached the guide. I Googled your card that you provided in your first post and what came up was that the chipset was a ralink 2870. 

[http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=nqn&q=buffalo+UC-G300N+in+ubuntu+jaunty&btnG=Search]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=nqn&q=buffalo+UC-G300N+in+ubuntu+jaunty&btnG=Search")

The guide I found is for devices that use the ralink chipset. This guide shuld work. Give it a try.

---

### Post by dvl300 on 2009-05-08
root@ubuntu:/home/geek09# lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:f7:0e:32
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 26:ab:ef:92:33:9d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@ubuntu:/home/geek09#

---

### Post by dvl300 on 2009-05-08
cant see my usb adaptor
gonna try that guide back in 5!

---

### Post by dvl300 on 2009-05-08
tried the guide still doeas not work!

---

### Post by dvl300 on 2009-05-08
please help

---

### Post by dvl300 on 2009-05-08
Solved!
Downloaded the 32 bit ISO version!
burned to disc and installed to my PC
Installed all the necessary packages for ndisgtk
then obviously installed ndisgtk, went into admin
then click on windows wireless driver then I
installed the inf and it works!

It would seem there's a problem with wubi? or the
amd 64 bit version!

---

