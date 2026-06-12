---
title: "3com 3C589C Etherlink III"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by jayvee on 2007-03-13
Hello,

First off, let me warn you that I'm completely new at Ubuntu (and linux in general).

My situation:
I have a Toshiba Satellite Pro 430CDS which I would like to use as a test-webserver. Console-only is the only option because of limited hard-drive space. The network card I'm using is the 3com 3C589C Etherlink III.

[LIST]
[*]I've tried installing with the server-cd, didn't work because it was "compiled for x686" or something like that. There was a workaround which for me only brought more problems.
[*]I then installed the "alternate cd". Because of the low available memory, the installer automatically went into "low memory mode" or something like that. Because of this, at some point I had to select optional modules to load. I selected all those that had something to do with NIC and NIC-PCMCIA. During the network setup, the light on the card went on and my router confirmed it had given an IP to the ubuntu-laptop. Hooray, connection! 
[*]Well, "connection" doesn't mean I get to the net. For some reason, the router doesn't distribute the DNS servers, I have to set these manually. Since I can't do that at this point in the installation, I expect the installer to be unable to access the web. But the card seems to work because the light on the card and on my router went on, and it got an IP. So I'm hopeful, once Ubuntu is actually installed I'll be able to set the DNS servers manually and I'll have conntection.
[*]Alas! The installation finishes and boots succesfully (as opposed to what happened with the server-cd), but the network card remains dead... No lights come on...
[*]Alright, Ubuntu has the ability to work with the card. I know that for a fact, since it worked during install. However, now that Ubuntu has been installed, no lights come on automatically.
[/LIST]

[This page]("http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS") claims the card should work (with 3c589_cs driver). I have no idea if that driver is installed at this point or how to find out.

Well... Any help would be greatly appreciated (but please remember I'm new to this, so if you want me to try things please specify the commands I need to type in).

Thank you in advance!

---

### Post by chili555 on 2007-03-13
Console only! Cool. All the techno geek zombies here cut their teeth at the console.

First, is the module inserted? Issue the command lsmod | grep 3c589. That means, roughly, list all the inserted modules but pipe | the list through another command: grep, which means look for a pattern, in this case 3c589.

Next, is the interface alive and just waiting for your command. Issue the command ifconfig -a. That will show all the interfaces, active on your system. Ignore lo. You may see one like this: ```
eth0      Link encap:Ethernet  HWaddr 00:D0:59:84:60:FB  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

That shows I have an ethernet interface all ready to go. So issue the command sudo dhclient eth0 (or whatever your relevent interface is.) You will have to give your password. That means, roughly, as superuser, ask the device on the other end of the wire if it will issue an IP address to us. If part of the reply is:```
bound to 192.168.1.117 -- renewal in 39405 seconds.
``` then you are connected.

Next, let's see if the router gave us DNS servers. Issue the command sudo nano /etc/resolv.conf. If you see: ```
nameserver 123.xxx.yyy.zzz
nameserver 124.xxx.yyy.zzz
```or similar, you are good. There are abbreviated instructions at the bottom to explain how to edit, save and exit. If no nameservers are listed, you can enter them. Save and exit.

Post back if you need more help.

---

### Post by jayvee on 2007-03-13
Thanks for helping! 
No luck though...

[LIST]
[*]lsmod | grep 3c589 returns nothing.
[*]ifconfig -a returns lo and sit0, no eth0
[/LIST]

In my first post, I forgot to mention ubuntu version: it's 6.06 LTS (dapper drake).

---

### Post by chili555 on 2007-03-13
Let's insert it:```
sudo insmod 3c589_cs
``` Then repeat the steps above.

---

### Post by jayvee on 2007-03-13
[LIST]
[*]sudo insmod 3c589_cs
insmod: can't read '3c589_cs': No such file or directory
[*]sudo insmod 3c589
insmod: can't read '3c589': No such file or directory
[/LIST]

I wonder where the installer got it from (or whatever the installer used).

---

### Post by chili555 on 2007-03-13
Let's try a few things. First, do sudo updatedb (takes a while) and then locate 3c589. On my laptop, I get, in part: ```
/lib/modules/2.6.17-10-generic/kernel/drivers/net/pcmcia/3c589_cs.ko
/lib/modules/2.6.17-11-generic/kernel/drivers/net/pcmcia/3c589_cs.ko
/lib/modules/2.6.20-5-generic/kernel/drivers/net/pcmcia/3c589_cs.ko
/lib/modules/2.6.20-9-386/kernel/drivers/net/pcmcia/3c589_cs.ko
``` 
You should see similar.

Let's try: ```
sudo depmod -a
sudo modprobe 3c589_cs
``` The cursor will pop back to a prompt if it works. If not, then let's try: ```
sudo modprobe /lib/modules/2.6.17-11-generic/kernel/drivers/net/pcmcia/3c589_cs.ko
```Make sure you modprobe the version that matches your running kernel, which you can find with the command:```
uname -r
```

I shall be consulting a professional spiritual guide. Good luck.

---

### Post by jayvee on 2007-03-13
[LIST=1]
[*]sudo updatedb
I return to prompt.
[*]With "locate 3c589" I'm supposing you mean "lsmod | grep 3c589"?
It returns :
3c589_cs       14216      0
pcmcia           40508      1      3c589_cs
[*]sudo depmod -a 
Takes a while to complete, then returns me to prompt.
[*]sudo modprobe 3c589_cs
Cursur returns to prompt. No network-card lights flash on though... 
"ifconfig -a" returns no eth0.
[*]uname -r
returns "2.6.15-26-386"
[*]sudo modprobe /lib/modules/2.6.15-26-386/kernel/drivers/net/pcmcia/3c589_cs.ko
FATAL: Module ... not found
[/LIST]

I hope you still see possibilities :)

---

### Post by Mr. C. on 2007-03-13
I see that you have kernel 2.6.15-26-386.  Was this kernel an Ubuntu distribution?  I recall a 2.6.11 and a 2.6..17, but not 2.6.15.

This driver has been in a kernel for quite some time, so i'm wondering.

Use the locate command as mentioned, and even find if you need

```
locate 3c589
find /lib/modules -name "3c589*" -ls
```

MrC

---

### Post by chili555 on 2007-03-13
Ahh! I see that my spiritual consultations have borne results!

Previously, lsmod did not show 3c589_cs, but now it does: ```
It returns :
3c589_cs 14216 0
pcmcia 40508 1 3c589_cs
```Previously, we were unable to successfully load our module, but now we are: ```
sudo modprobe 3c589_cs
Cursur returns to prompt.
```Praise be to Linus!

Let's see if we can get eth0 to show up. Let's sudo nano /etc/network/interfaces and add these lines: ```
auto eth0
iface eth0 inet dhcp
``` Also, let's sudo nano /etc/modules to add this line: ```
alias eth0 3c589_cs
``` Then let's restart networking: ```
sudo /etc/init.d/networking restart
``` and see what transpires.

---

### Post by jayvee on 2007-03-13
I'm sorry, I didn't know "locate" was a command, I thought he just meant the verb.

Okay then, "locate 3c589" returns:
/lib/modules/2.6.15-26-386/kernel/drivers/net/pcmcia/3c589_cs.ko

However, 
sudo modprobe /lib/modules/2.6.15-26-386/kernel/drivers/net/pcmcia/3c589_cs.ko
FATAL: Module ... not found

:confused:

I installed from the "PC (Intel x86) alternate install CD" which I downloaded from the ubuntu website: [http://ubuntu.mirrors.skynet.be/pub/ubuntu.com/releases/6.06/](http://ubuntu.mirrors.skynet.be/pub/ubuntu.com/releases/6.06/)
So it should be an official kernel, I think.

---

### Post by chili555 on 2007-03-13
Our posts crossed in the mail. See above.

---

### Post by Mr. C. on 2007-03-13
Ok, thanks for bearing with my ignorance on that kernel version.

I think Chili has this well in hand.

MrC

---

### Post by jayvee on 2007-03-13
I rebooted the machine since last try, so I repeated the following steps:
[LIST=1]
[*]sudo updatedb
[*]sudo depmod -a
[*]lsmod | grep 3c589
returns nothing
[*]sudo modprobe 3c589_cs
[*]lsmod | grep 3c589
It returns :
3c589_cs 14216 0
pcmcia 40508 1 3c589_cs
[*]sudo nano /etc/network/interfaces
sudo: nano: command not found
[*]sudo vi /etc/network/interfaces
It loads the file. The lines you told me to add are already there.
[*]sudo vi /etc/modules
It has some comment and then:
lp
psmouse
under these, I add: alias eth0 3c589_cs
[*]sudo /etc/init.d/networking restart
returns:
> * Reconfiguring network interfaces...
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DCHP](http://www.isc.org/products/DCHP)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
[/LIST]

Obviously, not working yet. Any other ideas?

---

### Post by Mr. C. on 2007-03-13
Curious, I ask, do you have your wireless powered off by any chance?  Many laptops come with a function key or dedicated key to disable the wireless card.  If it's off, it won't be found.

MrC

---

### Post by jayvee on 2007-03-13
It's not wireless... You can see a (dodgy) picture of it here: [http://support.3com.com/infodeli/tools/nic/3c589c/09-0770-000.pdf](http://support.3com.com/infodeli/tools/nic/3c589c/09-0770-000.pdf)

So no, it's not turned off. I didn't change anything to the hardware since installing ubuntu, at which time it did work (during the install, that is).

---

### Post by Mr. C. on 2007-03-13
Sorry, stupid typo on my part.  Yes, I meant PCMCIA card.  Does it appear in your dmesg output at all as detected?

---

### Post by jayvee on 2007-03-13
I don't see any mention of PCMCIA anywhere in the output of dmesg.

---

### Post by Mr. C. on 2007-03-13
Something is telling me this card and this driver do not match.

I would like to see all the output from dmesg before and after:

modprobe 3c589_cs

would that be possible for you to do ?

MrC

---

### Post by jayvee on 2007-03-13
I don't really see how, except typing it all over...
Or digital pictures and some cut-and-pastwork. Is there an other way? 

I don't have network, I do have a floppy but no other computer to put the floppy in...

---

### Post by chili555 on 2007-03-13
Since you have a terminal only, you will see dozens of lines of text flash by, too fast to read, if you just do dmesg. You can slowly read through them if you do: ```
dmesg | less
``` Look for any entries about 3c589 and whether or not if there are complaints from the kernel about the insertion of the module. You might also try: ```
dmesg | grep 3c589
dmesg | grep eth0
```

Try these for us, too: ```
sudo ifconfig eth0 up
sudo dhclient eth0
```

---

### Post by jayvee on 2007-03-13
I was desperate enough to go for the digital camera solution. 

I rebooted, dmesg to be seen [here]("http://files.jayvee.be/before.png"), sudo modprobe 3c589_cs, dmesg again which you can admire [here]("http://files.jayvee.be/after.png"). Hope you can get something out of it. 

"dmesg | grep 3c589" returned to prompt
"dmesg | grep eth0" returned to prompt
"sudo ifconfig eth0 up" returned "eth0: ERROR while getting interface flags: No such device"
"sudo dhclient eth0" returned 
> Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DCHP](http://www.isc.org/products/DCHP)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

Keep trying, somethings gotta work sometime, right ;)?

---

### Post by jayvee on 2007-03-14
*bump*

---

### Post by jayvee on 2007-03-14
*bump*

---

### Post by jayvee on 2007-03-14
Some more info. While booting, it shows the following messages:
(...)
* Loading hardware drivers...
* Starting PCMCIA services...
* PCMCIA not present
* Loading manual drivers...
(...)

I hope someone out there knows what to do, I sure don't.

---

### Post by chili555 on 2007-03-14
You might try downloading and installing [http://mirrors.kernel.org/ubuntu/pool/main/p/pcmciautils/pcmciautils_012-1ubuntu4_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/p/pcmciautils/pcmciautils_012-1ubuntu4_i386.deb)

```
sudo dpkg -i pcmciautils   <---press TAB, it should fill in the blanks
```

You can move it over from a USB drive or CDROM.

---

### Post by jayvee on 2007-03-14
Hi all,

Chili: I'll try your option if the following doesn't make the solution clear to anyone.

I was thinking: it worked during install, so perhaps it'll work from the CD? 

[LIST=1][*]I altered the DNS-file (necessary because the router doesn't do DNS right, it needs to be set manually on all computers attached to it):
sudo vi /etc/resolv.conf
[*]I shut down and booted from the CD, option "Rescue a broken system".
[*]It goes into "Low memory mode", makes me do country and keyboard settings, 
[*]Then goes on to detect hardware. At a certain point in this, it says "Starting PC Card Services". As soon as that disappears, the light on my network card goes on (but not on the router!).
[*]Now I get to select extra "installer components to load" (with the low memory and all). First, I select none and continue.
[*]It loads additional components. I didn't select any, I swear, but it loads stuff anyway. No nic or PCMCIA as far as I can see.
[*]Detecting Network Hardware, during which at a certain point it again states to be starting PC card services.
[*]An error: No Ethernet card was detected. It asks if I intend to use FireWire Ethernet. No FireWire on this laptop, so I select No.
[*]Another error: "A driver for your hardware is not available. You may need to load drivers from a driver floppy. If you have such a floppy available now, put it in the drive before continuing. Load missing drivers from a driver floppy?"
I once again select No.
[*]Error (with a red background, very spooky): Ethernet card not found. I select continue.
[*]Error: No network interfaces detected. I continue, have to set hostname and proxy, it starts detecting hardware again. Then I get to go to a shell, but what's the use, no connection (although the light went on on the network card).
[/LIST]

I boot from the CD again, and this time I do something different: I do select extra installer components to load (step 5 above).
[LIST=1]
[*]There are a number of components having to do with NIC:
- nic-firmware-2.6.15-26-386-di: External firmware for NIC drivers
- nic-modules-2.6.15-26-386-di: Common NIC drivers
- nic-pcmcia-modules-2.6.15-26-386-di: Common PCMCIA NIC drivers
- nic-restricted-firmware-2.6.15-26-386-di: Restricted external firmware (... might be more but the rest of the line is outside of the screen)
- nic-restricted-modules-2.6.15-26-386-di: Restricted drivers for NIC (... might be more but the rest of the line is outside of the screen)
- nic-shared-modules-2.6.15-26-386-di: Shared NIC drivers
- nic-usb-modules-2.6.15-26-386-di: USB NIC drivers
[*]I selected only nic-pcmcia-modules and continue. It loads additional components, I notice it also loads nic-modules and nic-shared-modules.
[*]It says something about network configuration with DHCP, but it goes rather fast. No errors. The corresponding light on my router flashes on. The router shows me:
> 03/14/2007  17:44:08 sending ACK to 192.168.1.7
03/14/2007  17:44:06 sending OFFER to 192.168.1.7
[*]I select hostname and proxy-server, it does "Detecting disks and all other hardware".
[*]I open a shell on the hard drive:
> sh-3.1# ping google.com
PING google.com (64.233.167.99) 56(84) bytes of data.
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=1 ttl=242 time = 114 ms
(...)
5 packets transmitted, 5 received, 0% packet loss, (...)
[/LIST]

So. Any ideas?

---

### Post by chili555 on 2007-03-14
Please try my suggestion and let me know if any dependencies are needed or other packages are suggested. I will find them for you.

---

### Post by jayvee on 2007-03-15
Is there a way to download that package from command line? That would be easiest then I think. 
Supposing, of course, that it will really "install" if I execute a shell on the hard drive after booting from the CD so that I have internet connection.

I do believe I saw pcmciautils flashing by during installation of base packages though...

---

### Post by denbeiren on 2007-04-14
I have the exact same problem on a toshiba 430 cdt,.. let me know if you have any luck!!

---

### Post by jayvee on 2007-04-14
Sorry, never found an answer. For use as a webserver, it worked to boot up using the CD, going to recovery and then opening a console on the installed version (on the hard drive). Since it goes through half the install-proces every time you do that, it's rather slow. But as I said, if you want to use it as a webserver, then you won't be rebooting every day so that shouldn't be too much of a problem.

I've stopped working on the problem. Even after getting the network card to connect (using the CD), setting up the server with console only just wasn't... Tutorialed enough.

So I went back to good old Win98 (oy say what you want, at least it works). I now use another computer as webserver, but I think you could make the old thing work by installing apache, php and mySQL on it manually.

---

### Post by gimle on 2007-07-24
Same kind of problem appearing on Toshiba Satellite Pro 4200, and 16-bit pcmcia card 3com Fast Ethernet (3c574-tx), I use the Xubuntu because of low memory on this laptop .. 

Anyway, I did all the steps (excluding the dpkg, which i haven't tried yet) replacing the module 3c509 for module 3c574_cs (which is supposed to be correct one.. maybe, i hope) and got the same results.. Curiously enough, I also have the card detected at install from the xubuntu 7.0.4 alternate install cd. (at the stage when it says "starting pccard services") It does not detect when installing from the live cd, and it fails to detect when booting into the system for the first time, too. At install the card works correctly. It was able to retrieve an address with dhcp and even download language files and patches from the internet. 

PCMCIA does not show up at all after boot, but I can do modprobe 3c574_sc without errors, 3c574_cs loads the pcmcia modules as well. However, eth0 does not show up and networking restart fails. I have added the module to /etc/modules. dmesg does not show anything related to pcmcia, 3c574 or eth0.

lspci doesn't list the cardbus controller either..

I'm setting this install for laptop use, so the cd booting is not an option here .. Please respond, there's clearly something one can do, since the card works so nicely on install!

---

### Post by gimle on 2007-07-24
I found the pcmciautils package from /var/cache/apt/archives/ and dpkg -i proceeded without errors. But still no luck, not at reboot either. No eth0!

---

### Post by gimle on 2007-07-24
Ah, and one more thing. I have also tried to boot with a different pcmcia network card. It also doesn't get detected at boot. How to get the cardbus controller initialized? Might this be the problem?

---

### Post by lfr on 2007-11-04
Hi All, I am having a very similar problem with a 3com 3c509b Etherlink III.

This thread has given me the most love up till now.

When I work through these instructions I can get the machine to recognize an eth0, which it hadn't previously.

However it gets stuck on DHCPDISCOVER, thus it never binds to a server and never connects.

I'll start a new thread with more details too.

---

### Post by alliterationArtiste on 2008-03-23
Somewhat late in the day but even though I have yet to fix this I may be able to shed some light. The 3c589 comes with a transceiver that provides a connection to 10baseT and 10base2. My money is on the fact that the thing defaults to 10base2 and somewhere there is a switch to move the transceiver to 10baseT but I can't work out how to do that. Closest I have come is a mod to /etc/pcmcia/network.conf (from memory) If I find the answer, will post it here.

---

