---
title: "Network going in and out on 6.06 LTS Server"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by dboot on 2008-01-14
Hello,

I just setup my second Ubuntu 6.06 LTS server with some success. After configuring it on the network with a static IP (along with the netmask, gw, and subnet provided by my ISP), the server is online. I installed SSH and had no trouble working on the server remotely through putty. I even setup a LAMP server for a website. After several minutes of being idle, however, the server was unreachable. I setup a monitor and keyboard on the server again and checked that none of the network config files had been changed realizing that the server is back on the network. This has happened consistently over the past few days.

It seems like the server only stays on the network when I'm using it. After it drops off the network, I have to log into it from a terminal and only after a few minutes of using it will it get back on the network. I literally failed to ping a different server, attempted to update which hung for a second then worked, and then I could ping the same server after that.

I edited /etc/network/interfaces to the appropriate (so I think) static IP, netmask, network, broadcast, and gateway.

Any ideas would be appreciated!

---

### Post by dboot on 2008-01-15
I still can't figure out why the server drops off the network ever few minutes. I'm going to make a cron job to ping another server (or update itself) every 5 minutes to attempt to keep it online.

Any ideas?

---

### Post by dboot on 2008-01-16
Well, the cronjob didn't work the way I had hoped. The server still drops off the network.

crontab -e -> 5 * * * * /bin/ping -c 5 [www.google.com](www.google.com)

](*,)

---

### Post by dboot on 2008-01-16
After re-installing Ubuntu and manually setting the network (/etc/network/interfaces), the server can ping the router after consistently failing 3 times (after it drops off the network at random intervals). After managing to ping the router, however, it cannot recognize hostnames: $ping [www.google.com](www.google.com) -> ping: unknown host [www.google.com](www.google.com). Does that mean my DNS records are wrong?

---

### Post by dboot on 2008-01-17
After editing /etc/hosts properly, my DNS records are correct.

For now, the best way to keep the server online is to ping another server every 10 minutes and not to stop: ping -i 600 [www.google.com](www.google.com). There's gotta be a better way to keep the server on the network...

---

### Post by dboot on 2008-01-22
It seems like my NIC is going to sleep. Is it possible for the 6.06 drivers to put my NIC to sleep? I've installed Ubuntu on the computer before without any trouble but never 6.06 server edition.

I've updated it to 6.06.02.

---

### Post by dboot on 2008-01-28
What's the network driver for Ubuntu Server 6.06.02 LTS? How can I find out? I've installed several different versions of Ubuntu desktop that hasn't had any trouble with the network on this computer.

---

### Post by Whiffle on 2008-01-28
The network driver depends on the network card.   Which card do you have? (lspci should tell you)

Have you ruled out the possibility of a hardware failure?  I know of a built in network card that does exactly what you're describing, it seems to be broken.

EDIT: Now that you say it, I'm pretty sure ubuntu server nad ubuntu desktop use a different kernel, which deals directly with your network driver issue.  You might try installing a different kernel (maybe from the desktop version), and see what happens.

---

### Post by dboot on 2008-01-28
I'm pretty sure it's a driver issue since the card is basically going into hibernation when there is no network traffic.

Is it possible to install a new network driver without installing a new kernel?

---

### Post by Whiffle on 2008-01-28
It may be, depending on the hardware.  Drivers are hardware specific so you'll have to find an updated driver for your hardware and compile it against the kernel that you have in order for it to work.

---

### Post by dboot on 2008-01-28
Ouch. I think I'd rather wait until the next ubuntu server LTS version is released with an updated kernel. For now I'll continuously ping the default gateway...

Thanks for your help, Whiffle!

---

### Post by Whiffle on 2008-01-28
I would give using apt-get to install a different kernel a try, its not terribly difficult.

---

### Post by dboot on 2008-01-30
What kernel version should I upgrade to?

---

### Post by Whiffle on 2008-01-30
I would try whichever generic i386 kernel is available in apt.

---

