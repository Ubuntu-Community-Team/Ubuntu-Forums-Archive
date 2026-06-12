---
title: "Could someone please help me configure my internet connection?"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by ortaa23 on 2009-11-08
Hola

I have just taken the plunge and wiped xp, installed Ubuntu 9.10 in its place. Which is dandy except I can't work out why my wired internet connection won't work on the machine. 

Packard Bell Easynote AMD Sempron
D-Link G624T Router

Says Auto eth0 active when I plug the cable in but no go when I try to access a page.

Have tried the instructions here: [https://help.ubuntu.com/9.10/internet/C/connecting-wired.html](https://help.ubuntu.com/9.10/internet/C/connecting-wired.html) but to no avail.

Anyone have any suggestions as to what I could try next?

Adam

---

### Post by bacardiandwatermelon on 2009-11-08
can you connect to your router, or ping it for that matter? Normally wired connections work straight out of the box..

---

### Post by bacardiandwatermelon on 2009-11-08
[https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html)

---

### Post by ortaa23 on 2009-11-08
Thank you for replying, bacardi. 

I am able to access the router's settings. However, when I type 'iconfig eth0', into the terminal, 'command not found' is the response. And when I ping **82.211.81.158, **there is also no response. Any ideas?

---

### Post by Hetepeperfan on 2009-11-08
> **ortaa23 said:**
> Thank you for replying, bacardi. 

I am able to access the router's settings. However, when I type 'iconfig eth0', into the terminal, 'command not found' is the response. And when I ping **82.211.81.158, **there is also no response. Any ideas?


You should try ifconfig eth0 there is an 'f' missing in your command

---

### Post by bacardiandwatermelon on 2009-11-08
I think it should be ifconfig :-) I should have checked that ip address, it seams that address is old and ping requests are being dropped... try 91.189.94.156 instead which is [www.ubuntu.com](www.ubuntu.com)

---

### Post by mapes12 on 2009-11-08
> **ortaa23 said:**
> Thank you for replying, bacardi. 

I am able to access the router's settings. However, when I type 'iconfig eth0', into the terminal, 'command not found' is the response. And when I ping **82.211.81.158, **there is also no response. Any ideas?The address you have pinged is not a router private address. These are usually assigned using the DHCP service on your router and usually start 192.168.x.x

There are other private address ranges but class C (as quoted above) is generally the norm.

BTW the configuration interrogation command is ```
ifconfig
``` Try that and post back.

---

### Post by ortaa23 on 2009-11-08
Hello thanks for pointing that out.. as you can likely guess fiddling with computer guts is something I'm relatively new to.

Here's what results.

ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:40:d0:7e:24:ff  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe7e:24ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3916 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:834483 (834.4 KB)  TX bytes:464060 (464.0 KB)
          Interrupt:23 Base address:0xe100 

When I ping both the 91.189.94.156 address and my router's (192.168.1.1), the packets are successful (though with the latter varies between 0.69ms and 7.67 if that's at all significant...

---

### Post by bacardiandwatermelon on 2009-11-08
I've never been very good at diagnosing faults so bare with me.. Do you have any other desktops or laptops on the same network, can they get to the net aswell?

Does this this command in terminal work to update the repos?
```
sudo apt-get update
```

If this works then it might just be a problem with firefox.. In firefox goto edit->preferences->advanced->network->settings.. is it on no proxy?

---

### Post by ortaa23 on 2009-11-08
Well I am amazed that people are willing to help out people like me for free so my patience is not an issue...

Unfortunately typing in the command you suggest was not successful - unable to connect.

I have the laptop that I am using to post connected to the same network, Winxp. No problems with that.

The Firefox setting was on Automatic proxy config probably from when I was playing around with it earlier but no change after setting it to No proxy.

---

### Post by Norm24 on 2009-11-08
Probably a dumb question on my part but have you tried setting FF to "Use system proxy settings"?

I'm on a wired network and I've always had FF using that setting and have never had any connection issues.

---

### Post by ortaa23 on 2009-11-08
Norm, 

No difference when I change that and try to connect.

Is there such thing as a dumb question? Assumption is the mother of all fuckups, it seems.

---

### Post by bacardiandwatermelon on 2009-11-08
Hmm I'm stumped... I think you should run the following command and get the name of your network controller and do some googling.. Good luck :-)

```
lspci | grep Ethernet
```

---

### Post by ortaa23 on 2009-11-10
Right, thanks, so herein lies the problem:

[http://ubuntuforums.org/showthread.php?p=7207288](http://ubuntuforums.org/showthread.php?p=7207288)

And here are some bug reports:

[https://bugzilla.redhat.com/show_bug.cgi?id=377721](https://bugzilla.redhat.com/show_bug.cgi?id=377721)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291017](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291017)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267779](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267779)

What I forgot to mention before was that the connection worked without problems when I had Ubuntu 7.0.4 installed. 

Could someone please advise me as to what is worth trying, or, if futile, which Linux variant is known to be free from this problem?

Thanks,

Adam

---

### Post by ortaa23 on 2009-11-10
From the bottom bug report is this:

The revised explanation for why irqfixup works is that after resume the
firmware will use a default IRQ since it doesn't get reprogrammed by the
PCI sub-system, and will likely be different to the IRQ the driver is
expecting. irqfixup will match the two together.

So if adding irqfixup to my kernel is going to help, how the hell do I do that?

A.

---

### Post by ortaa23 on 2009-11-10
Ok, so I now know theoretically how one adds kernel parameters, having tried following the instructions here;

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

However, after pressing 'e' on the relevant O.S., I found no such line as
# kopt=root=/dev/sda1 ro [FONT=Verdana]
on the resulting screen, so I couldn't proceed with the instructions. Am I looking in the wrong place? And anyway, is this (trying to add irqfixup to the kernel) even the right thing to be doing?

Any help greatly appreciated.
[/FONT]

---

### Post by ortaa23 on 2009-11-11
Anybody at all...?

---

### Post by soapytheclown on 2009-11-11
that line is only there if you edit the menu.lst in the /boot/grub/ folder

at a guess id say you just hit e at grub2 list, and type irqfixup -if it works then go ahead and modify the menu.lst to make a permanent change to booting

if not I remember my brother had to turn acpi off on his machine and the grub option was acpi=off so you may have to type something like irqfixup=on ?

---

