---
title: "[SOLVED] won't recognize network card"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by kdeeds on 2009-01-03
[FONT="Arial"]I installed ubuntu on a pc with a windows which had become so corrupt, it wouldn't complete a bootup. 

Ubuntu works great so far in every respect, **except** that it won't recognize the network card. 

The machine had an onboard network adapter, which it wouldn't recognize, but I wasn't sure if it worked. 

I installed a new linksys card, but it won't see that either.

I'd appreciate any help I can get on this one.[/FONT]

---

### Post by kdeeds on 2009-01-03
Help!
No one has any ideas?

---

### Post by handydan918 on 2009-01-03
> **kdeeds said:**
> Help!
No one has any ideas?

I have an idea.
Give us some information.
Try posting the output of ```
lspci | grep -i net
```
and ```
ifconfig
```

---

### Post by kdeeds on 2009-01-03
Here you go, sorry I didn't post this before, but I'm very new to linux and ubuntu, Haven't even used dos in nearly 15 years. I've been looking for some basic information on linux, but wanted to try to get this machine up and running asap.

Thanks for any help you can provide.




ken@ken-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e6:7f:66:bf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xc400 

eth1      Link encap:Ethernet  HWaddr 00:1e:e5:d6:ba:a0  
          inet6 addr: fe80::21e:e5ff:fed6:baa0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:6 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:33204 (33.2 KB)  TX bytes:1710 (1.7 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15316 (15.3 KB)  TX bytes:15316 (15.3 KB)






ken@ken-desktop:~$ lspci | grep -i net
01:00.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by kdeeds on 2009-01-04
No one has any ideas?

---

### Post by ibizatunes on 2009-01-04
what verrsion of ubuntu did you install, 8.04 or 8.10
8.10 has alot more wireless drivers

---

### Post by kdeeds on 2009-01-04
> **ibizatunes said:**
> what verrsion of ubuntu did you install, 8.04 or 8.10
8.10 has alot more wireless drivers


I installed ver 8.1, the network is wired.
Actually, the title may be misleading, I think the card is recognized, but I keep getting the message 'network disconnected'

---

### Post by albinootje on 2009-01-04
> **kdeeds said:**
> 
ken@ken-desktop:~$ lspci | grep -i net
01:00.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

There's two network cards.
Can you post the output of :
```

sudo lshw -c network
sudo dhclient
ifconfig -a
route -n
cat /etc/resolv.conf
dmesg

```
Please post the "dmesg" output as a .txt attachment here.
Additional Options -> Manage Attachments.

---

### Post by kdeeds on 2009-01-04
> **albinootje said:**
> There's two network cards.
Can you post the output of :
```

sudo lshw -c network
sudo dhclient
ifconfig -a
route -n
cat /etc/resolv.conf
dmesg

```
Please post the "dmesg" output as a .txt attachment here.
Additional Options -> Manage Attachments.

okay, here's the output. Thanks for the help.

---

### Post by albinootje on 2009-01-04
> **kdeeds said:**
> okay, here's the output. Thanks for the help.

Thanks.
You're behind a router or modem ?
Does that router/modem hand out ip-addresses via dhcp.
If so, are you connected on some other computer via the same router/modem setup ? 
Does that machine use dhcp as a client ?
Is Ubuntu the only OS installed on the machine with the two network cards ?

Was the output of dmesg zero ?
Can you post the output of :
```

df -h

```

---

### Post by kdeeds on 2009-01-04
> **albinootje said:**
> Thanks.
You're behind a router or modem ?
Does that router/modem hand out ip-addresses via dhcp.
If so, are you connected on some other computer via the same router/modem setup ? 
Does that machine use dhcp as a client ?
Is Ubuntu the only OS installed on the machine with the two network cards ?

Was the output of dmesg zero ?
Can you post the output of :
```

df -h

```

I'm on a cable modem, no router installed. 

The machine I'm using ubuntu on is only running ubuntu. 

I'm trying to get the output file from dmesg compressed to attach it, the file is too large to attach as a .txt file.

I apologize for thte time it takes to post, I'm working as I do this, and trying to learn this os at the same time.

---

### Post by kdeeds on 2009-01-04
this file didn't attach for some reason.

ken@ken-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              27G  2.1G   24G   9% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  100K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.7M  499M   1% /dev
tmpfs                 501M  168K  501M   1% /dev/shm
lrm                   501M  2.0M  499M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd0              21M   21M     0 100% /media/cdrom0
ken@ken-desktop:~$

---

### Post by kdeeds on 2009-01-04
dmesg zip file

---

### Post by kdeeds on 2009-01-04
bumped for help!

---

### Post by albinootje on 2009-01-04
> **kdeeds said:**
>  I apologize for thte time it takes to post, I'm working as I do this, and trying to learn this os at the same time.

No problem, I'm just back home myself.
I've looked at your dmesg output and I didn't see a sign of possible BIOS bugs, or irq conflicts.
But the question remains :
Do you have any other machine that connects to the internet via the cable modem ?
If so, does that one get an ip-address assigned and has internet ?

If is does, it is possible that we need to fake the MAC-address of one of your network cards in your Ubuntu machine.

---

### Post by kdeeds on 2009-01-04
> **albinootje said:**
> No problem, I'm just back home myself.
I've looked at your dmesg output and I didn't see a sign of possible BIOS bugs, or irq conflicts.
But the question remains :
Do you have any other machine that connects to the internet via the cable modem ?
If so, does that one get an ip-address assigned and has internet ?

If is does, it is possible that we need to fake the MAC-address of one of your network cards in your Ubuntu machine.



I just have the modem. I have a windows machine that I'm using to access this forum, but I physically disconnect to try the machine with ubuntu.
When I installed ubuntu, and when trying the new network card, I shut down, plugged in the cable, then boot up the computer.

---

### Post by albinootje on 2009-01-04
> **kdeeds said:**
> I just have the modem. I have a windows machine that I'm using to access this forum, but I physically disconnect to try the machine with ubuntu.
When I installed ubuntu, and when trying the new network card, I shut down, plugged in the cable, then boot up the computer.

OK. Did you have a cdrom do set up the internet connection for Windows ?
Did you need to fill in some username and password somewhere, or not at all ?

If not, let's try the MAC-address faking,
On the Windows machine do the following in a DOS-box :
```

ipconfig /all

```
Write the Mac-address down, or put it in a txt file on some usb-stick.

See here an example screenshot :
[http://lantoolbox.com/wp-content/uploads/2007/03/ipconfig-all-view-mac-address.png](http://lantoolbox.com/wp-content/uploads/2007/03/ipconfig-all-view-mac-address.png)

On the Ubuntu machine, do the following :
```

sudo ifconfig eth0 down hw ether 00:16:a2:a3:45:bc
sudo ifconfig eth1 down hw ether 00:16:a2:a3:45:bc
sudo dhclient

```
Where 00:16:a2:a3:45:bc should be the MAC-address you got from the ipconfig command on the Windows machine.

Please post the output of the commands in Ubuntu.

---

### Post by kdeeds on 2009-01-04
here's the ipconfig results

---

### Post by albinootje on 2009-01-04
> **kdeeds said:**
> here's the ipconfig results

OK. Thanks, please try this on the Ubuntu machine :
```

sudo ifconfig eth0 down hw ether 00:1A:A0:6B:EA:43
sudo ifconfig eth1 down hw ether 00:1A:A0:6B:EA:43
sudo dhclient
dmesg

```
And post all output.

---

### Post by kdeeds on 2009-01-05
Problem resolved, thank you.
Thanks to everyone who tried to help on this.
It turns out that the problem wasn't with the network card, but with the cable modem not requesting a new ip address when I switched computers. I wasn't aware that the cable modem doesn't request a new ip if you physically just change the cable from one machine to another.

---

### Post by newbee70 on 2009-01-05
> **kdeeds said:**
> Here you go, sorry I didn't post this before, but I'm very new to linux and ubuntu, Haven't even used dos in nearly 15 years. I've been looking for some basic information on linux, but wanted to try to get this machine up and running asap.

Thanks for any help you can provide.




Try this site for Linux information and a few manuals.

[http://tldp.org/](http://tldp.org/)

---

### Post by kdeeds on 2009-01-05
> **newbee70 said:**
> Try this site for Linux information and a few manuals.

[http://tldp.org/](http://tldp.org/)

got it, thanks!
There's a ton of info there... should be able to get through it in a few years!

---

