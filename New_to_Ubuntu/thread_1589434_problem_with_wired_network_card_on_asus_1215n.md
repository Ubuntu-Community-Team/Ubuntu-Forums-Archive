---
title: "problem with wired network card on asus 1215n"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by Fabio166 on 2010-10-06
Hello everybody,

I bought the eee pc 1215n and installed ubuntu on it. I first installed Ubuntu 10.04 and, since the network card was not working, I installed the driver for the atheros from this link:
[http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) ([AR81Family-linux-v1.0.1.13.tar.gz]("http://partner.atheros.com/Download.aspx?id=151"))
It worked.
Then, since there were other problems with bluetooth, webcam, microphone and graphic card, I upgraded to Ubuntu 10.10. 
I didn't have to install anything else, and I got all the devices working. The problem is that after a few minutes the connection (wired) falls and there is no way I can re-establish it unless I reboot the system. Then it works, but only for a few minutes, and then again it falls.

Any suggestion about this?

I also tried to re-compile the atheros driver, but I get the following message:

fabio@fabio-laptop:~/AR81Family-linux-v1.0.1.13$ make
make -C ./src 
make[1]: Entering directory `/home/fabio/AR81Family-linux-v1.0.1.13/src'
Makefile:105: *** Linux kernel source not configured - missing autoconf.h.  Stop.
make[1]: Leaving directory `/home/fabio/AR81Family-linux-v1.0.1.13/src'
make: *** [all] Error 2

Thank you in advance for any reply.

---

### Post by bprins on 2010-10-06
might not have been the best choice the upgrade to a non official release if 10.4 didn't work properly, but ok, what done is done I guess.

if your network device "stops" just out of the blue, there is a chance some error message pops up in your log files (messages / kern.log, etc). Have a look and see if you can find what went wrong.

Isn't there a repository package that you can install iso compiling from source?

The error message tells you that something is missing from your kernel source. Which kernel are you running? 2.6.35-22? If not, try to upgrade to that kernel. It's the latest stable kernel in maverick.

---

### Post by Fabio166 on 2010-10-07
My kernel version is 2.6.35-22-generic.
I took a look in my log files but I couldn't find anything when the connection stops. However, when I unplug e plug the cable again I get these messages from syslog:

NetworkManager[881]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
 NetworkManager[881]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
 NetworkManager[881]: <info> (eth0): now managed
 NetworkManager[881]: <info> (eth0): device state change: 1 -> 2 (reason 2)
 NetworkManager[881]: <info> (eth0): bringing up device.
 NetworkManager[881]: <info> (eth0): preparing device.
 NetworkManager[881]: <info> (eth0): deactivating device (reason: 2).
 kernel: [ 1333.811229] atl1c 0000:01:00.0: irq 46 for MSI/MSI-X
 kernel: [ 1333.811903] ADDRCONF(NETDEV_UP): eth0: link is not ready

Anyway, what do you mean by "a repository package that you can install iso compiling from source" ?

Oh, another thing: my wireless device is indicated as eth1 instead of ath0, wlan0 or something like that... It seems to be a bit strange to me, but I'm not sure...

---

### Post by Fabio166 on 2010-10-07
I tried to reset the eth0 device with the commands:

sudo ifconfig eth0 down
sudo ifconfig eth0 up

and syslog says:

kernel: [ 1708.703915] atl1c 0000:01:00.0: irq 46 for MSI/MSI-X
kernel: [ 1708.704698] ADDRCONF(NETDEV_UP): eth0: link is not ready
AptDaemon: INFO: Quiting due to inactivity
AptDaemon: INFO: Shutdown was requested


I'm quite lost.....

---

### Post by Snake231088 on 2010-10-16
I have the same problem on Aspire 5745G with ar8151 gigabit ethernet card.
Some help?

---

### Post by Fabio166 on 2010-10-28
I fixed it by upgrading the kernel to the 2.6.36 version!
Not sure what it was, but it's working now...

---

### Post by loup87 on 2010-11-03
> **Fabio166 said:**
> I fixed it by upgrading the kernel to the 2.6.36 version!
Not sure what it was, but it's working now...

Just a quick question, since I have the same problem. Is it still working well after 5 days? :)

---

### Post by Snake231088 on 2010-11-15
Work with 2.6.36.
Thanks.

---

