---
title: "New Install: No Wireless"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by xvedejas on 2008-03-02
Sorry if this question has already been answered; I did go back and look at similar threads!

I just got Gutsy Gibbon installed on this machine, dual-boot, and the wireless internet isn't working. It recognizes my network, but it cannot connect. I typed this into the terminal:

lshw -C network

and I got this:

```
*-network DISABLED
description: Wireless Interface
product: RT2561/RT61 802.11g PCI
vendor: RaLink
physical id: a
bus info: pci@0000:01:0a.0
logical name: wmaster0
version: 00
serial: 00:18:f8:a8:98:b2
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g

```

Any help?

---

### Post by xvedejas on 2008-03-03
I seem to have removed the wireless network icon from the panel, how do I get it back?

Sorry, I'm new at this.

---

### Post by superprash2003 on 2008-03-03
type ifconfig in the terminal and post results here

---

### Post by ferdostar on 2008-03-03
> **xvedejas said:**
> I seem to have removed the wireless network icon from the panel, how do I get it back?

Sorry, I'm new at this.

Hi,
If you mean the default network manager icon, just add notification area to your panel.

---

### Post by Hightide on 2008-03-03
Hi

[Gilfs]("http://ubuntuforums.org/showthread.php?t=603154") guide may help

regards

:)

---

### Post by kevdog on 2008-03-03
You are using the rt61pci driver -- sometimes sketchy for a lot of people in gutsy.  I would probably compile the serial monkey rt61 driver and use that instead.  Do you need a link?

---

### Post by xvedejas on 2008-03-03
> **kevdog said:**
> You are using the rt61pci driver -- sometimes sketchy for a lot of people in gutsy.  I would probably compile the serial monkey rt61 driver and use that instead.  Do you need a link?

Okay, I found it. I'll try it now. I'll edit this post with my results.

EDIT: I'm not the best with linux, the readme wasn't enough for me to properly install it. Any help?

EDIT AGAIN: Here are the results of "ifconfig";

```
eth0      Link encap:Ethernet  HWaddr 00:50:8D:95:C6:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:50:8D:95:C6:76  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3648 (3.5 KB)  TX bytes:3648 (3.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:F8:A8:98:B2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-F8-A8-98-B2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by bmartin on 2008-03-03
Here are instructions for downloading and installing the driver recommended for most people. Open a terminal and copy/paste the following. I included a description of what the commands do. If you decide you want to use the rt61pci driver again, simple edit the blacklist-wifi file to say "rt61" (the new driver) instead of "rt61pci" (the old driver). Blacklisting a driver prevents it from being used when your computer starts up:

First, you need Ubuntu's tools for compiling drivers (and software in general)
```
sudo aptitude install build-essential linux-headers-$(uname -r)
```
Then, you need to obtain the code you're going to compile
```
mkdir ~/tmp
cd ~/tmp
wget http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz
tar xf rt61-cvs-daily.tar.gz
cd rt61-cvs-*/Module/
```
These commands compile and install the driver
```
make
sudo make install
```
This steps shouldn't be necessary, but I'd do it just in case
```
sudo cp rt2*.bin /lib/firmware/$(uname -r)/
```
Remove the old driver
```
sudo modprobe -r rt61pci
```
Load the new one
```
sudo modprobe rt61
```
Make sure the old driver doesn't get used when you reboot
```
echo "blacklist rt61pci" | sudo tee /etc/modprobe/blacklist-wifi
```
Make sure the new driver is always loaded when you start your computer
```
echo "rt61" | sudo tee -a /etc/modules
```

The unfortunate thing about drivers like this one is that you have to reinstall them each time your OS is upgraded (or, more accurately, whenever your kernel is upgraded... there are normally 2 kernels per release of Ubuntu, AFAIK). If you always use the same kernel (not recommended by me personally), you'll never have to recompile the driver.

---

### Post by pj5739 on 2008-03-03
> **Hightide said:**
> Hi

[Gilfs]("http://ubuntuforums.org/showthread.php?t=603154") guide may help

regards

:)
Thank you so much for Gilfs guide!  This saved me a ton of time.  I have no way of connecting at high speed via wired connection as my network card got fried a few years ago.  My only connection is really via wireless and this guide helped me set it up.  Thanks a million!  (In case you were wondering, I have a usb device I can plug my LAN cable into to get a connection, but it's slower than dial-up.  No lie.)  Peace!

---

### Post by xvedejas on 2008-03-03
I got errors with "make":

```


make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/user1/Desktop/rt61-1.1.0-b2/Module/rtmp_main.o
/home/user1/Desktop/rt61-1.1.0-b2/Module/rtmp_main.c: In function &#8216;RT61_open&#8217;:
/home/user1/Desktop/rt61-1.1.0-b2/Module/rtmp_main.c:405: warning: &#8216;deprecated_irq_flag&#8217; is deprecated (declared at include/linux/interrupt.h:66)
/home/user1/Desktop/rt61-1.1.0-b2/Module/rtmp_main.c: In function &#8216;rt61_init_module&#8217;:
/home/user1/Desktop/rt61-1.1.0-b2/Module/rtmp_main.c:1044: warning: implicit declaration of function &#8216;pci_module_init&#8217;
  CC [M]  /home/user1/Desktop/rt61-1.1.0-b2/Module/mlme.o
/home/user1/Desktop/rt61-1.1.0-b2/Module/mlme.c: In function &#8216;MlmeEnqueueForRecv&#8217;:
/home/user1/Desktop/rt61-1.1.0-b2/Module/mlme.c:3297: warning: format &#8216;%ld&#8217; expects type &#8216;long int&#8217;, but argument 2 has type &#8216;size_t&#8217;
  CC [M]  /home/user1/Desktop/rt61-1.1.0-b2/Module/connect.o
  CC [M]  /home/user1/Desktop/rt61-1.1.0-b2/Module/sync.o
  CC [M]  /home/user1/Desktop/rt61-1.1.0-b2/Module/assoc.o
  CC [M]  /home/user1/Desktop/rt61-1.1.0-b2/Module/auth.o
  CC [M]  /home/user1/Desktop/rt61-1.1.0-b2/Module/auth_rsp.o
  CC [M]  /home/user1/Desktop/rt61-1.1.0-b2/Module/rtmp_data.o
/home/user1/Desktop/rt61-1.1.0-b2/Module/rtmp_data.c: In function &#8216;RTMPHandleRxDoneInterrupt&#8217;:
/home/user1/Desktop/rt61-1.1.0-b2/Module/rtmp_data.c:477: error: &#8216;struct sk_buff&#8217; has no member named &#8216;mac&#8217;
/home/user1/Desktop/rt61-1.1.0-b2/Module/rtmp_data.c: In function &#8216;RTMPCheckDHCPFrame&#8217;:
/home/user1/Desktop/rt61-1.1.0-b2/Module/rtmp_data.c:4318: warning: unused variable &#8216;dest_port&#8217;
/home/user1/Desktop/rt61-1.1.0-b2/Module/rtmp_data.c:4317: warning: unused variable &#8216;is_udp&#8217;
/home/user1/Desktop/rt61-1.1.0-b2/Module/rtmp_data.c:4316: warning: unused variable &#8216;is_ipv4&#8217;
/home/user1/Desktop/rt61-1.1.0-b2/Module/rtmp_data.c:4315: warning: unused variable &#8216;is_ip&#8217;
make[2]: *** [/home/user1/Desktop/rt61-1.1.0-b2/Module/rtmp_data.o] Error 1
make[1]: *** [_module_/home/user1/Desktop/rt61-1.1.0-b2/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
rt61.ko failed to build!
make: *** [module] Error 1

```

What did I do wrong?

EDIT: I've been running Ubuntu as a virtual machine for the past few months, and I've really come to respect it. That's why I'm so anxious to get the real deal going!

---

### Post by xvedejas on 2008-03-04
Hmm, I think I might have downloaded the wrong file. I'll try again with the one you seem to be referencing in your post.

---

### Post by xvedejas on 2008-03-04
Okay, this is what it says now...

```


user1@user1-desktop:~/Desktop/rt61-cvs/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'
*** Module rt61.ko built successfully
user1@user1-desktop:~/Desktop/rt61-cvs/Module$ sudo make install
[sudo] password for user1:
*** Install module in /lib/modules/2.6.22-14-generic/extra ...
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  INSTALL /home/user1/Desktop/rt61-cvs/Module/rt61.ko
  DEPMOD  2.6.22-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
/sbin/depmod -a
*** Update /etc/modprobe.d/ralink alias for wlan*
*** Install firmware in /lib/firmware ...
*** Check old config ...


```

---

### Post by xvedejas on 2008-03-04
Okay, I found out how to fix this error using "strip --strip-unneeded", but I still can't connect to the internet. Before at least it showed signal strength of my network. Now it only shows my network and whenever I try to connect it freeze ubuntu so that when I try to open an application it drops it before it opens...


If it weren't for things like this I probably would not use windows.

---

### Post by xvedejas on 2008-03-05
Come on, guys! Don't give up! I'm determined to get this working. I think I'll search google a bit more; I see if I make any progress...

---

### Post by bmartin on 2008-03-05
There's a wireless program designed specifically for RT chipsets that would likely solve the problems you're having. Unfortunately, I forget the name of it, and I imagine it has to be compiled from source. If only I could remember the name...

---

### Post by xvedejas on 2008-03-05
Please try to remember it! I'm not quitting until this problem is solved.

---

### Post by xvedejas on 2008-03-05
Is there any chance at least that this will be fixed in 8.04?  :confused: I'm willing to wait a month if it can be fixed.

---

### Post by xvedejas on 2008-03-06
Anyone?

If I can't fix it and 8.04 doesn't fix it I might decide to buy a new wireless card...

---

### Post by xvedejas on 2008-03-06
Apparently 8.04 as of yet does not fix my problem; I ran the latest alpha as a live cd and nothing changed.

---

### Post by xvedejas on 2008-03-08
Is there no way to fix this? If I can't find out how to fix it by now, Ubuntu isn't as ready for human beings as its motto implies...

---

### Post by xvedejas on 2008-03-09
Nobody? Anybody? Pffft.

**At least could someone refer me to somewhere where they* would* know how to fix this?**

---

### Post by kevdog on 2008-03-09
You've followed this guide as a reference (its for rt73 so just use your head -- you want rt61 -- same steps, different file -- the most complete guide I know about!): [http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

---

### Post by xvedejas on 2008-03-09
This guide doesn't work; the command that's "sudo iwconfig wlan0 key [key]" or something similar doesn't work. It says the key I input is invalid. And somehow this made my computer when booting into vista recognize a wireless network that doesn't exist! How does this do that?? I'm thoroughly confused.

:confused:

---

### Post by Hightide on 2008-03-09
> **xvedejas said:**
> 
product: RT2561/RT61 802.11g PCI
[/CODE]

Any help?

Hi

as you are using the rt61 driver, have a look at this [how to]("http://ubuntuforums.org/showthread.php?t=626246&highlight=serial+monkey")


regards

:)

---

### Post by xvedejas on 2008-03-09
Sorry, no such luck. Loading the driver effectively seems to do nothing, and adding drivers to the blacklist does two things; the strength bars for the networks go away, and the notification icon never lights up any of the two lights. Before, it would light up the first one regardless of what password you gave it, but would never connect.

---

### Post by xvedejas on 2008-03-10
Someone suggested I use ndiswrapper; how do I?

---

### Post by Hightide on 2008-03-10
HI

Try kevdog's very good [tutorial]("http://ubuntuforums.org/showthread.php?t=574501")

regards
:)

---

### Post by xvedejas on 2008-03-10
Okay, I think we're getting closer...

But it still didn't work. Everything seemed to go fine, though...



My wireless is "wmaster0" instead of "wlan0" like it says it should be; is this a problem?

---

### Post by xvedejas on 2008-03-11
Anybody?

Please don't give up!

---

### Post by xvedejas on 2008-03-12
If ubuntu won't work with my wireless card, is there any distro that might? From what I've seen and tried I like ubuntu fair enough, but if I can't get this problem working, I'll have to try for something else. I wanted Linux for human beings, I got this? Sorry, but patience running out.

---

### Post by bmartin on 2008-03-12
Hmmm... many distros might do the trick. You could give PCLinuxOS a spin... it'll ask for your NDIS driver immediately (make sure you have it handy!!). The thing I don't like about PCLOS is how slow the apt/RPM combination works; apt/DEB in Ubuntu is MUCH faster.

Another one that might work is Sabayon. I personally think that Sabayon misrepresents itself as a Gentoo distro (since it's not trivial to "emerge world"), but it's pretty good about hardware detection.

My choice, if I were setting up my computer for personal use and wanted everything to work smoothly, would be to run the Ubuntu Gutsy Gibbon live CD and get the wireless working from that by following a guide designed for installing the serialmonkey drivers. After you get that working, install a fresh copy of Ubuntu and repeat those steps to set up the wireless again.

Ubuntu makes Flash/Java/codecs a cinch. Some other distros do, too, but they're few and far between.

[Here's a guide]("http://ubuntuforums.org/showthread.php?t=296822") for setting up the RT61 driver. [Here's]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61") another one.

---

### Post by xvedejas on 2008-03-12
> My choice, if I were setting up my computer for personal use and wanted everything to work smoothly, would be to run the Ubuntu Gutsy Gibbon live CD and get the wireless working from that by following a guide designed for installing the serialmonkey drivers. After you get that working, install a fresh copy of Ubuntu and repeat those steps to set up the wireless again.

Sort of what I've been trying to do, thanks anyways.

I still want to use Ubuntu, but I guess some other distro can keep me busy for now. Does sabayon have apt or any of that?

---

### Post by bmartin on 2008-03-12
Sabayon uses Portage, like Gentoo does. The command to run Portage is **emerge**. Sabayon has amazing hardware detection and drivers, so I wouldn't be surprised if all of your hardware worked OOTB. They're also not a "free" distribution (last I checked, in the GNU sense of the word), so you might have nifty programs installed by default (which some would call "bloat"). Sabayon tries to provide a lot of things by default that most people will want.

I don't understand why all of these wireless devices don't work OOTB. Most chipsets have pretty good support via some driver, except Broadcom and a couple others.

---

### Post by xvedejas on 2008-03-12
Alright, I'm downloaded Sabayon (it's really slow though... 10 minutes and only 15% done...)


> I don't understand why all of these wireless devices don't work OOTB. Most chipsets have pretty good support via some driver, except Broadcom and a couple others.

I sure hope this is fixed in Hardy at least... I was looking forward to it...

---

### Post by xvedejas on 2008-03-13
Great, I have the** same exact problem **with sabayon.


Please get this fixed by 8.04, someone!

---

### Post by rustybronco on 2008-03-13
> **xvedejas said:**
> This guide doesn't work; the command that's **"sudo iwconfig wlan0 key [key]" or something similar doesn't work. [b]It says the key I input is invalid.** And somehow this made my computer when booting into vista recognize a wireless network that doesn't exist! How does this do that?? I'm thoroughly confused.

:confused:[http://ubuntuforums.org/showpost.php?p=4480500&postcount=22](http://ubuntuforums.org/showpost.php?p=4480500&postcount=22)
> Configure the interface.
Code:

sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid YOUR_NETWORK_NAME_HERE
sudo iwconfig wlan0 key YOUR_WEP_KEY_HERE_OR_"off"_FOR_NO_KEY
sudo dhclient wlan0

Note that you must insert your network essid where it says YOUR_NETWORK_NAME_HERE 

**********and your WEP **key** where it says********
YOUR_WEP_KEY_HERE_OR_"off"_FOR_NO_KEY
**did you put in your wep key properly? **

Type "off" instead if you don't have a WEP key to secure your network. All this should be typed without quotation marks.>  **It says the key I input is invalid.**...

---

### Post by xvedejas on 2008-03-14
Sorry, I should have been more specific. It said;

```
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "password".
```

---

### Post by xvedejas on 2008-03-14
Answers?

---

### Post by xvedejas on 2008-03-16
This is becoming way too annoying.

---

