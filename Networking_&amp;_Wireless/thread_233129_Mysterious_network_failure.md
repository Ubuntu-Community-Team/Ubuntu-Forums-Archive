---
title: "Mysterious network failure"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by caspar_wrede on 2006-08-09
I have a fileserver which I apt-get upgraded from breezy to dapper. It has never given me problems of any kind.

Yesterday there was a power failure and the server can now not get its network connection up again. The machine had been running for several months with one or two apt-get dist-upgrade kernel updates, but i did not reboot it.

1) Hardware failure is not the problem: when I boot with knoppix it can get into the internet.

2) DHCP is not the problem: see above.

3) lspci tells me that the ethernet card is recognised. The output is identical to the output under knoppix.

4) When I do ifup eth0, there is no error message of any kind not even with verbose mode (-v).

5) With a GUI I can see eth0 in the network settings, whenever I click on enable, nothing happens. 

6) I am at my wits end

7) PLEASE HELP

8) I like lists

---

### Post by halfvolle melk on 2006-08-09
1) So you're running the updated kernel for the first time?

2) Try booting into an older kernel.

3) This may show if it's a kernel problem.

4) From what I gather you like lists.

5) I hope you like the way this post is formatted.

---

### Post by caspar_wrede on 2006-08-10
Nice list!

I have tried booting into an older kernel. It didn't help

---

### Post by halfvolle melk on 2006-08-10
Hmm, not even the recovery mode one?

edit: Can you ping and stuff like that?
In some cases networking breaks in Dapper where it worked on Breezy

---

### Post by caspar_wrede on 2006-08-10
1) This is not the first time that I have run the dapper kernel. It worked before.

2) I can't ping anything, not even the router (192.168.0.1). I can only ping "lo"

3) When I enter ifconfig, "lo" is the only thing I see.

---

### Post by RedBoot on 2006-08-10
This may be lame advice, but have you tried reinserting the card? I had a similar situation last week with a machine that had two NICs. One day, Ubuntu 'saw' only one of them. I moved it to another PCI slot, rebooted and all was well. I know this doesn't jive with the Knoppix system working. But after a lightning hit, it might have some effect.

---

### Post by caspar_wrede on 2006-08-10
The network card is on the main board (cheap computer, you see). Another interesting thing is that I tried inserting a network card, which was recognised (by Ubuntu as well as knoppix), yet wouldn't work under ubuntu either! How about that? I assume there is some corrupted startup script lurking somewhere, just how the deuce do I bloody find it?

Charles.

---

### Post by caspar_wrede on 2006-08-11
Any ideas, any one?

---

### Post by jjkola on 2006-08-11
I have same kind of problem although after upgrading from breezy to dapper I lost network connectivity. If I switched back to earliel kernel network started to work again.

There seems to be a few bugs in kernel 2.6.15 related to networking.

[http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.15.1](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.15.1)
[http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.15.5](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.15.5)

Especially one bug which was mentioned in 2.6.15.5 changelog is quite severe and which could cause network link not going up. So I think kernel should be updated to 2.6.15.5 version as soon as possible, or even some newer version (2.6.16, 2.6.17, etc).

---

### Post by caspar_wrede on 2006-08-12
It does not appear to have anything to do with the kernel. Regardless of which kernel I boot, including the old breezy ones, networking refuses to work.

Somebody please spare me from having to do a reinstall. Or is there such a thing as a non-destructive install?

---

### Post by drtvasudevan on 2006-08-12
sure!
if you have your home partition separate just reinstall the /partition dont format the home partition.

---

### Post by caspar_wrede on 2006-08-13
Well, unfortunately I don't have a separate home parition and it's too late to do anything about it now.

Any ideas, anyone??? There must be some way of seeing what goes wrong when I do ```
sudo ifup eth0
```. It "works" in that there are no failure messages, but the interface is not brought up, and there is no network activity that would point to a DHCP handshake. The interface is also not listed when I then do ```
 ifconfig 
``` Help!

---

### Post by caspar_wrede on 2006-08-14
Somebody? Anybody? Help!

---

### Post by jorgerivera on 2006-08-14
Hi!

No ideas, sorry, but I've got the same problem but in a laptop.
However, I was trying to solve a problem with the wlan0 interface when the eth0 died. 
I was messing around with ndiswrapper. I think we should check that.

Good luck!

Jorge.

---

### Post by jorgerivera on 2006-08-14
Hi again!

I'm running a kernel version that made the eth0 work fine. It is 2.6.15-19-386. You tried this, already, don't you?
You tried all your possible kernels?
Is every kernel in your computer included in GRUB menu?

Jorge.

---

### Post by anindya_m on 2006-08-15
Hi,

You can try to see if you can bring up the network "by hand" (I'm assuming you have a fixed IP). First make sure that eth0 is down by running ifconfig (you should see only lo). Suppose your network has the following config (substitute values for your configuration): ```
ip: 192.168.0.10
nettmask: 255.255.255.0
gateway: 192.168.0.1

```
As root run the following command:```
ifconfig eth0 down
route del default
ifconfig eth0 192.168.0.10 netmask 255.255.255.0
route add default gw 192.168.0.1
```
Now try to ping the gateway (192.168.0.1). Do you get any response?

Anindya

---

### Post by caspar_wrede on 2006-08-15
Hello Jorge,

Thanks for your help -- it didn't work.

Hello Anindya,

Thanks for your help -- IT WORKED!!!!!!!

If I could I would crown you emperor of all Ubuntu-land! Thank you very much. You have saved me a huge amount of trouble.

Once last point. ifup eth0 by itself still doesn't work. Is there any way I can fix this?

Caspar

---

### Post by drtvasudevan on 2006-08-16
seems there is a bug that does not allow the changes to be retained.
it has been reported.
till such atime it is fixed.........

---

