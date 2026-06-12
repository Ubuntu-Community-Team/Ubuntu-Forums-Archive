---
title: "Problem with Qualcomm Atheros AR8121/AR8113/AR8114 ethernet controller"
date: 2018-03-17
forum: Networking &amp; Wireless
---

### Post by jbhtexas on 2018-03-17
Hello!

I am having the slow speed problem with an onboard Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet controller wired connection and Ubuntu 16.04 LTS 64-bit, as described in this bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1453391](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1453391) 

As described at the end of the bug report, the problem still seems to be present in 16.04 LTS 64-bit.  In my case, the controller will only connect at 10 Mb/s.  The controller will connect at 100 or 1000 Mb/s when running Windows.  

The ATL1E driver is getting loaded. In the Ubuntu 16.04 manuals,
[http://manpages.ubuntu.com/manpages/xenial/man4/ale.4freebsd.html](http://manpages.ubuntu.com/manpages/xenial/man4/ale.4freebsd.html)

there is an "ale" driver mentioned for this network controller.  However, I haven't been able to find anything further about how to use this driver.  It doesn't seem to be loaded in my setup.  Does anyone have any hints or suggestions on where to find this driver and how to use it with 16.04 LTS?

Also, any hints or suggestion on how to get this controller to connect at a speed higher than 10 MB/s using the existing driver would be greatly appreciated. I tried the command "ifconfig media 100baseTX", but I get an error that the option is not supported.

Thanks!

---

