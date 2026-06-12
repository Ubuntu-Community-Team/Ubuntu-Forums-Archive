---
title: "1000baseT/Full (Gigabit) mode is supported but not advertised"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by aldeby on 2007-09-14
ethtool eth0 shows me this:

```
 sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
**                                1000baseT/Full **
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
```

as you see 1000baseT mode is indeed supported (as it should be) BUT not advertised!

if I connect via cross cable this ethernet to another gigabit card the auto negotiation goes to 100baseT/full mode!! 
How can I get 1000baseT mode? 
How can I disable auto negotiation?
when I run 
```
sudo ethtool -s eth0 autoneg off
```
ethtool eth0 report doesn't change! and obviously issuing ```
sudo ethtool -s eth0 speed 1000
```
doesn't change either!

my card is a Realtek RTL8101E laptop integrated gigabit card.
Thank you!!!

---

### Post by noob12 on 2007-09-14
You can use the commands but  I've found you have to set it all simultaneously.  Try this:
```

sudo ethtool -s eth0 speed 1000 duplex full autoneg off

```

The other side has to be ready to run at 1000mbps too (either autonegotiating up or set to run that way).

ADDED:  If that works for you you can put it in a pre-up in your /etc/network/interfaces file.

---

### Post by noob12 on 2007-09-16
By the way what driver are you using? (**sudo lshw -C network** will tell you).  You may be able to give it an option to advertise 1000 if it isn't and it should.

---

### Post by aldeby on 2007-09-17
Noob12 thank you very much for your replies!
here is my lshw output:
```
*-network
                description: Ethernet interface
                product: RTL8101E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth0
                version: 01
                serial: 00:1b:24:74:c9:04
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair

```
As you see it states Gigabit support, nonetheless once more ethtool says
```
 Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes

```
I had a look on realtek website for a driver update, but there is stated linux drivers come embedded into the kernel. Maybe should be a matter of mis-configuration? 
I am sure I have changed nothing in /etc directory, furthermore yesterday I swithched from a Gutsy x86_64 to a Gutsy x86 because of some modem drivers were not available for amd64 platform, and the ethernet still connects at 100Mbps!
Oh, as a cable I use a cat5e crossed, tested for gigabit lan.

Actually this is not such a big problem for me at the moment, however I wonder if there is a config file where I can set the advertised speed. I just don't understand why if the nc supports 1000Mbps it advertises only 100Mbps!

---

### Post by netztier on 2007-09-17
> **aldeby said:**
> here is my lshw output:
```
*-network
                description: Ethernet interface
                product: RTL8101E PCI Express [COLOR="Red"]Fast Ethernet[/COLOR] controller
                ...
                [COLOR="Red"]capacity: 1GB/s[/COLOR]
                width: 64 bits
                clock: 33MHz
               ...

```



I wonder how "Fast Ethernet" and 1GB/s got mixed up like that? I guess that this is just some descriptive bit of ASCII buried somewhere in the NIC's registers that gets read during PCI(-E) probing. Or possibly something that didn't get updated in some PCI device table that matches a card's identification strings (probably some hex code) to a human-readable bit of text - on that case it'd be someting for the kernel developers, I suppose.

I've been thinking of another approach to a solution: Which module does the kernel use for this NIC? Check **modinfo <module name>** to see if it accepts any configuration parameters - or try to find it's documentation - possibly somewhere in the kernel docs/sources.

Be sure to try **mii-diag -vv eth0** and study it's output, too. I've seen cases where output from either ethtool or mii-diag did not represent what was actually going on - it turned out that some internal register on the card had fixed it to 10Mbit/s (that was with a 3com, it had to be "unlocked" with a special DOS-based tool by 3com).

You already used a direct connection from another box to that Realteck NIC, didn't you? Also try ** ethtool** and **mii-diag -vv** on this second box - like this, you should be able to find out what link capabilites the Realtek actually does advertise.

best regards

Marc

---

### Post by noob12 on 2007-09-17
Um.  According to Realtek, that's not a gigabit card.  It is a 10/100 card.

[http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&ProdID=19](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&ProdID=19)

If that's accurate, then try as you might you aren't going to get to 1000mbps, and there must be a bit set incorrectly in the driver capabilities, but it is at least advertising the right range.  That's a bug, but a less important case than the other way around.

---

### Post by aldeby on 2007-09-18
That is actually weird!

according to Realtek RTL8101E chipset is actually only Fast Ethernet (100Mbps) 

however HP,  my laptop vendor, declares in my model's datasheet there is a Gigabit 10/100/1000Mbps ethernet RJ-45 port!!

Linux Kernel in fact recognise 1000Mbps capability
```
 capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
```
and thus loads r8169 module which is **description:    RealTek RTL-8169 [COLOR="Red"]Gigabit Ethernet[/color] driver**

however ethtool says the gigabit capability is not advertised
```
Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
```

modinfo says:
```
filename:       /lib/modules/2.6.22-11-generic/kernel/drivers/net/r8169.ko
version:        2.2LK
license:        GPL
description:    RealTek RTL-8169 Gigabit Ethernet driver
author:         Realtek and the Linux r8169 crew <netdev@vger.kernel.org>
srcversion:     E76EC316B2C797C735E45F0
alias:          pci:v00001737d00001032sv*sd00000024bc*sc*i*
alias:          pci:v000016ECd00000116sv*sd*bc*sc*i*
alias:          pci:v00001259d0000C107sv*sd*bc*sc*i*
alias:          pci:v00001186d00004300sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008169sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008168sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008167sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008136sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008129sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.22-11-generic SMP mod_unload 586 
parm:           media:force phy operation. Deprecated by ethtool (8). (array of int)
parm:           rx_copybreak:Copy breakpoint for copy-only-tiny-frames (int)
parm:           use_dac:Enable PCI DAC. Unsafe on 32 bit PCI slot. (int)
parm:           debug:Debug verbosity level (0=none, ..., 16=all) (int)

```

I simply do not understand...

---

### Post by noob12 on 2007-09-18
Can you please post your entire **lspci -nn** output?  We'll see the device ids of what you have; maybe the descriptive string is wrong.

It's not unheard of to have a 10/100 device supported by a gigabit driver.  Some of the newer Intel 10/100 devices are also under support of the Intel e1000 driver; this kind of thing happens sometimes based more on the similarity between chipsets and the commonality of code required to drive them.

By the way, did my suggested specific ethtool command work for you or not?

---

### Post by aldeby on 2007-09-21
noob12, thank you very much for assisting me.
Typing ethtool command you suggested (sudo ethtool -s eth0 speed 1000 duplex full autoneg off) makes my eth0 freeze and the link drop.

I checked the other machine I was trying to connect to and ethtool actually says it supports and also advertises 1000baseT/Full so that one should not be the problem.

[B]here you can find the technical specifications of my laptop: it confirms it has a Gigabit 1000 ethernet
[http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c01069047&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN]("http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c01069047&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN")
[/B]

here is my **lspci -nn** output
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection [8086:4229] (rev 61)[B]
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)[/B]

---

### Post by elmagno on 2007-09-21
aldeby--

The driver that's loading, the r 8169, is not for your chip. I have a r8111/r8168B that Ubuntu loaded as r8169 (it's in the kernel).
Getting it out is not easy (blacklisting won't do it). But for me, it was very much worth it, as the r8169 driver was pitiful.

I'd try to get drivers from the Realtek site for your chip, excise the currently loading driver and see what happens.

---

### Post by What_now! on 2007-09-21
Hello. I too have a newly purchased HP pavilion, also with the RTL8101E chipset. I am having the same problem as the OP. I decided to purchase this laptop in part because of HP's and the retailer's claim that it is a gigabit ethernet laptop. Try as I might, in windows vista, XP, Debian, I could not get a gigabit connection to a gigabit switch. I looked at realtek's website, and found that their onboard gigabit chipset is in fact the RTL8111C not the RTL8101E. The device ID of the 8101 is 0x8136, whereas the id of the 8111 is 0x8368. 

I called an HP customer service rep who also swore up and down that it had gigabit ethernet, simply because that's what the specs said. I wanted to RMA the laptop back to HP, thinking that I simply got a defective one, but he claimed they did not do that and the he was the highest person I could talk to.

I returned the laptop to the retailer and exchanged it for the same model, the dv6589us. When I got home, lo and behold, I find the 8101 on it. Clearly my original purchase was not defective. I later discovered that the problem was more systemic than I had imagined.

I looked at the pin layouts of the 8101 and the 8111 on realtek's website. They are TWO completely different chipsets. Actually, what I mean to say, is that realteak uses the same microchip for these two chipsets, but there are some minor, but key differences in the wiring, and the type of resistors connected to each chipset that makes one 10/100 and the other gigabit. All of which takes place on the CAD machine of the Quanta engineer who wired the laptop and which I can do nothing about without my own laptop fab :).

I went to another retailer advertising a different model of pavilion, the dv6568se, as gigabit. I found the model on newegg.com also advertised as gigabit. I purchase the laptop and ... same thing RTL8101E. WTF! Suffice it to say I returned it that same day.  In the same store, I was looking at a Sony VAIO again advertised as gigabit. I look through the ipconfig result: "RTL8101E Fast Ethernet Adapter. Again. WTF!

Either someone at Quanta, the OEM manufacturer for both Sony and HP, as well as Dell and Gateway, ****** up big time and out & out lied to the ODMs about gigabit claims, or someone at the marketing depts of the ODMs got overzealous in their specs without actually verifying the laptops' capabilities.

Either way, I paid for gigabit, but I don't have gigabit. All I can hope is that there is that someone out there has some simple driver configuration that I overlooked, or some magic command I have to invoke to enable gigabit on my $1400 laptop, and tell me that this past week has only been a bad dream. If not, welcome to the global free market 21st century economy, where the American marketer doesn't know what the Taiwanese electrical engineer is doing.

---

### Post by netztier on 2007-09-22
> **What_now! said:**
> 
I went to another retailer advertising a different model of pavilion, the dv6568se, as gigabit. I found the model on newegg.com also advertised as gigabit. I purchase the laptop and ... same thing RTL8101E. WTF! Suffice it to say I returned it that same day.  In the same store, I was looking at a Sony VAIO again advertised as gigabit. I look through the ipconfig result: "RTL8101E Fast Ethernet Adapter. Again. WTF!


Now that comes close to a worthy submission to [http://worsethanfailure.com/](http://worsethanfailure.com/) .

And I'd go and ask HP to prove that the new laptop CAN do a Gigabit connection. You didn't get what was advertised and you paid for. They should prove that your newly purchased laptop (the device you are holding in your hands) actually is gibabit-capable. 

Too bad we don't use these laptops at the place where I work. Our HP Onsite Support Center's chief engineer would have some longish discussions with me :evil: On the other hand he's a really cool guy and very supportive and he'd have the contacts within HP to get some decent answers.

The more I think about this, the more upset I get. :mad: Feel like going out to the next shop just to buy one of these to see if they have the same problem and then go berzerk at HP's Customer helpline. *grrrr*


best regards

Marc

---

### Post by aldeby on 2007-09-22
What_now, thank you for the reply!

I looked at the technical specifications of your notebook and it seems exactly like mine, except for the 4Gb memory you have. Unfortunately I'm also stuck with this ethernet port.

Everywhere it is claimed that these models have indeed a Gigabit RJ-45 port but the chipset is undoubtedly an RTL8101E (both linux and windows recognise it as this). Windows recognizes it as a 10/100 ethernet port too.
Also on HP forum I found posts concerning this issue, no one managed to run with 1000baseT.
And finally on HP site, download drivers page is available for download a driver for "RTL8101E Fast Ethernet" card...

Thus I am going to think HP fooled us selling something it really is not supported.

As you did I checked on Realtek Website for the product design of both RTL8101 (fastethernet) and RTL8111 (gigabit) chipset and are compatible, changes are really minor. However I am going to think that maybe this should be related to the fact that in my box ethtool says 1000baseT is supported, but not advertised. Maybe...

PS: I just want to point out that on HP website itself this laptop is advertised as having a *Network Card Integrated 10/100/1000 Gigabit Ethernet LAN (RJ-45 connector)*: [http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c01069047&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN]("http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c01069047&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN")

---

### Post by nkastner on 2007-09-22
Hey guys, I just spent 10 hours trying to figure this out, I am so freaking mad right now, I found this forum, and made me a little better, but here it goes, I purchased a dv6500t cto, first of all what a pain in the *** to get xp working, smooth :) second this damn gigabit realtek, this is bs, hp better make this negotiate at gigabit like advertised, I am really confused device manager shows it as a realtek 8101, but yet if you turn on network boot in bios, then F12 to boot. pause the screen check it out low bios level says RTL8111B Gigabit controller, so wtf? why does it show up as 8101? hmmm., ok so now time to load 8111b drivers and force gigabit, hahha guess what! doesnt work! wtf? I am farely pissed, hp needs to fix this. damn ok I am going to stop, but please guys lets all call hp and bitch!

---

### Post by nkastner on 2007-09-22
Oh, also can you guys post do you have 8111b's?

---

### Post by aldeby on 2007-09-22
Got it!
Thank you nkastner, I followed your instructions and my computer BIOS actually reports having a```
Realtek RTL8111B/8168B Gigabit Ethernet Controller v2.03 (060516)
```what was yours like?
so... it is all a matter of linux and windows kernels not correctly recognizing the controller...
Is it out there a linux kernel module specifically crafted for this kinda controller? I'll have a look on google and keep you update.

---

### Post by elmagno on 2007-09-22
First, I'm reposting this:

The driver that's loading, the r 8169, is not for your chip. I have a r8111/r8168B that Ubuntu loaded as r8169 (it's in the kernel).
Getting it out is not easy (blacklisting won't do it). But for me, it was very much worth it, as the r8169 driver was pitiful.

I'd try to get drivers from the Realtek site for your chip, excise the currently loading driver and see what happens.

Second, I'm adding this:

Try compiling the 8.003.0o driver from [www.realtek.com.tw](www.realtek.com.tw)

But the r8169 will still trump that driver unless you completely remove the r8169.ko module.

---

### Post by aldeby on 2007-09-22
elmagno, r8169 module is supplied with the kernel, so it is not me that made the choice to load it, 
however building and loading Realtek official drivers **r8168** and then removing (also deleting) the r8169 module does not make the job! 

while **lsmod |grep r8168** states the driver has been loaded correctly,
in fact no eth*n* appears me when asking **ifconfig -a**, nor with **ifconfig eth0 up**. rebooting and doing an lsmod -a does not solve the problem either. 

elmagno, have you succeed in running with this ethernet with r8168 module? have you succeed in running it at 1000baseT ?

I'm looking forward to reading your reply

---

### Post by elmagno on 2007-09-22
aldeby,

In your post you say " the r8169 module is supplied with the kernel," which is exactly what I said. Then you say, "so it is not me that made the choice to load it. "  Is  this some sort of veiled accusation?

FYI, yes I'm using the 8168 on three machines. They are running  11.7MBps through NFS. They advertise 1000Mbps, but I'm running through a 10/100 router.

Why isn't it working for you? Two things stand out, among many possible issues. First, my computers are desktops and the implementation of this chipset may be different than on your machine. Second, there may have been a problem when you removed the built in driver, perhaps when you recompiled module dependencies.  Good luck.

---

### Post by aldeby on 2007-09-22
elmagno, I'm sorry for that. There was no irritation against you.
It indeed is a good thing if you managed to make your cards up and running with this driver.

Unfortunately I still have some issues with those modules: [r8169 keeps loading even if I deleted rt8169.ko > fixed this by executing depmod -a again] , however still the main problem is that if I remove this module via **sudo modprobe -r r8169** and then load the other one via **sudo modprobe r8168** I cannot bring up eth0 via **sudo ifconfig eht0 up**, nor see it via** sudo ifconfig -a**.

I am curious to know about anyone else experience, in particular that of owners of HP Pavilion laptops. 

here is the link where you all can download the drivers from: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2")

---

### Post by elmagno on 2007-09-22
aldeby--

Here are some useful tips from member Stormbringer:

*****************
Now, let's find out if r8169 is loaded as well...

# lsmod | grep r8169

If it is loaded then there's the chance that r8169 has grabbed the NIC ... however, you can force r1000 to be used by a small "hack".

# sudo mv /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko ~/
This will move the r8169 kernel module into your home directory.

# sudo depmod -a
Rebuild the kernel module dependencies.

# sudo mv /boot/initrd.img-`uname-r` /boot/initrd.img-`uname -r`.ubuntu
make a backup of the original initrd.

# sudo mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`
Create a new initrd WITHOUT the r8169 module

# sudo gedit /etc/modules

Add "r1000" (without the quotes) at the end of the file.

Save the file.

Upon reboot you are using r1000 for sure as there's no more r8169.

I'm sure the same goal may be accomplished by blacklisting r8169 somewhere in the config of hotplug --- haven't worked myself into this yet.

Now try and see if you see any improvements ...



--- Undoing the changes:

# sudo gedit /etc/modules
Remove the "r1000" line and save the file

# sudo mv /boot/initrd.img-`uname -r`.ubuntu /boot/initrd.img-`uname -r`
Restore the original initrd

# sudo mv /lib/modules/`uname -r`/kernel/drivers/net/r1000.ko ~/
Move the r1000 module to your home directory

# sudo mv ~/r8169.ko /lib/modules/`uname -r`/kernel/drivers/net/
Move the r8169 module back to where it belongs.

# sudo depmod -a
Rebuild the module dependencies.

Reboot.
***************

Not exactly what you need, but maybe close enough. I know you have performed at least some of these steps, if not all of them. Additionally, this procedure is extra safe. Just figure out where you need to jump in (considering what you have already done), and give it a try.

When you get to the point of modifying /etc/modules, you will add "r8168" without the quotes. (Stormbringer's example says "r1000.")

Good luck

---

### Post by nkastner on 2007-09-22
So, you guys seem very on top of this :) how can we fix this in windows as well? I have tried forcing the 8111b/8168 driver on the card, then went into properties and forced link speed to 1gigabit and still nothing? what is going on here someone call hp yet on this? thanks alot guys!

> **aldeby said:**
> Got it!
Thank you nkastner, I followed your instructions and my computer BIOS actually reports having a```
Realtek RTL8111B/8168B Gigabit Ethernet Controller v2.03 (060516)
```what was yours like?
so... it is all a matter of linux and windows kernels not correctly recognizing the controller...
Is it out there a linux kernel module specifically crafted for this kinda controller? I'll have a look on google and keep you update.

---

### Post by nkastner on 2007-09-23
Any luck guys, I can't figure this out. please :)

---

### Post by What_now! on 2007-09-24
In my opinion, the only reason that  the r8169 driver shows 1000 mbps as supported, is because that specific driver supports it, and not because the device supports it. I have concluded that YOU CAN'T get 1000mbps using any HP Pavilion using the santa rosa chipset, if the device ID of the LAN chipset is 0x8136. If you read my earlier post, the device ID of the realtek pci-e GIGABIT chipset is 0x8168, which the pavilion does not have.

Just by looking at the driver on HP's website you know it is 10/100, not gigabit. The driver is specifically called RTL8101E FAST ETHERNET driver.

I have found that the same driver supports the 0x8169 gigabit chipset, but again,  it does not mean that the chipset on the pavilion is gigabit. Indeed, I used realtek's 0x8168 gigabit driver for linux (which again is the "cousin" gigabit version of the 8101e chipset), but changed the device id to 0x8136 . Guess what happened, ..., nothing. The driver loaded, but it did not enable the NIC, there wasn't even an activity ligh on it.

Probably the confusion arose somewhere in HP's marketing/documentation dept. More than likely HP saw that the MoBo revision for the 10/100 laptop was a few cents cheaper than the gigabit version, but somehow HP decided that they had the same capabilities, because the driver was the same. Big F-up on HP's part. All they see is the $$$.

The pavilion would have been a great laptop if it indeed had gigabit, maybe even on par with a MacBook in both design and capabilities. But the simple fact that it was advertised as gigabit but only had 10/100 ruined it for me. The deception; the fact that the HP rep I spoke to was adamant about it's gigabit support; the price point, it was too much. 

I am now going to purchase an ASUS F3SC-B1 which has more features than the pavilion, INCLUDING GIGABIT, for $300 less.

---

### Post by nkastner on 2007-09-25
So you returned yours? why does it say Realtek RTL8111B/8168B Gigabit Ethernet Controller v2.03 (060516) if you try to boot from nic? I don't get this like you I was told up and down it had gigabit before I ordered it.

> **What_now! said:**
> In my opinion, the only reason that  the r8169 driver shows 1000 mbps as supported, is because that specific driver supports it, and not because the device supports it. I have concluded that YOU CAN'T get 1000mbps using any HP Pavilion using the santa rosa chipset, if the device ID of the LAN chipset is 0x8136. If you read my earlier post, the device ID of the realtek pci-e GIGABIT chipset is 0x8168, which the pavilion does not have.

Just by looking at the driver on HP's website you know it is 10/100, not gigabit. The driver is specifically called RTL8101E FAST ETHERNET driver.

I have found that the same driver supports the 0x8169 gigabit chipset, but again,  it does not mean that the chipset on the pavilion is gigabit. Indeed, I used realtek's 0x8168 gigabit driver for linux (which again is the "cousin" gigabit version of the 8101e chipset), but changed the device id to 0x8136 . Guess what happened, ..., nothing. The driver loaded, but it did not enable the NIC, there wasn't even an activity ligh on it.

Probably the confusion arose somewhere in HP's marketing/documentation dept. More than likely HP saw that the MoBo revision for the 10/100 laptop was a few cents cheaper than the gigabit version, but somehow HP decided that they had the same capabilities, because the driver was the same. Big F-up on HP's part. All they see is the $$$.

The pavilion would have been a great laptop if it indeed had gigabit, maybe even on par with a MacBook in both design and capabilities. But the simple fact that it was advertised as gigabit but only had 10/100 ruined it for me. The deception; the fact that the HP rep I spoke to was adamant about it's gigabit support; the price point, it was too much. 

I am now going to purchase an ASUS F3SC-B1 which has more features than the pavilion, INCLUDING GIGABIT, for $300 less.

---

### Post by What_now! on 2007-09-25
Hi, I also followed the steps in a previous post and looked at the NIC boot information. As I recall it said something like PXE boot 'FOR' RTL8111C. In my understanding, it did not say that this was the chipset that it detected, but that it was the chipset that the boot program was written for. Which further contributed to my suspicion that someone from HP goofed when ordering the MoBos for the laptop, and ordered, for whatever reason, the one with the 10/100 NIC and not the gigabit NIC. In other words, to put it simply, it is my firm belief that the electronics of the onboard NIC do not support gigabit Ethernet, based on all of the information I've seen including the microchip pin configuration for the RTL8111C and the RTL8101E. If you are really peeved about this, I would return the laptop while I still had a chance, or  at least call HP. Another tip, in the future if you want to be certain that a laptop has gigabit NIC, purchase one that say 'Centrino Pro', as to qualify for the label, a laptop has to have an intel gigabit onboard NIC.


Lobby Desk - HP Bldg 3  (650) 857-1501 - Main number.
Ask for the Personal Systems Group as they are the ones that make the Pavilion.

---

### Post by aldeby on 2007-09-26
Yes, I also think that BIOS actually writes down that beacuse it was supposed to find that chip, whereas both Linux and Window$ just probe for the available network device and its name.

Please keep this thread updated if you manage to know some more news concerning this issue from the HP helpdesk. 

I'm just curious to see what are they going to do in order to fix this mess...

---

### Post by aldeby on 2007-11-01
Any updates?

By the way have a look at Bug #159417 I filed at launchpad [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/159417](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/159417)

There is an issue with driver r8169 which slows down this sucking RTL8101E chipset, manually installing r8101 driver highly increases the ethernet performance (i.e. transfer speeds).

However since HP sold us a Fast Etherent device and not a Gigabit one transfer rates never exceed 100Mbps :-(

---

### Post by mickrussom on 2007-11-27
> **aldeby said:**
> if I connect via cross cable this ethernet to another gigabit card the auto negotiation goes to 100baseT/full mode!! 


I've always found that a crossover will always automatically downgrade 1000 to 100. Try with a straight through. 

See:

[http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

[http://en.wikipedia.org/wiki/Gigabit_Ethernet](http://en.wikipedia.org/wiki/Gigabit_Ethernet)

[http://pinouts.ru/NetworkCables/1Gbcrossover.shtml](http://pinouts.ru/NetworkCables/1Gbcrossover.shtml)

All three places say gigabit crossover is not needed. Because a classic crossover only crosses two of the pairs, you will be downgraded as gigabit uses all four pairs (4 *250MHz)

---

