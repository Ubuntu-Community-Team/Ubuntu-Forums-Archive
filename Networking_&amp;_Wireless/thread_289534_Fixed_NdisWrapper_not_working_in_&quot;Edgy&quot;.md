---
title: "Fixed NdisWrapper not working in &quot;Edgy&quot;"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by -Chi.0 on 2006-10-31
What you will need to do is go into your Package Manager of you choice, and  type ***_ndis_*** in the seach box

**[Arrow key down]** [I]and make sure the following 4 packagers are installed.
[/I]
NdisWrapper-common 1.18 <-- **This is the 1 that was not installed, You must install this then reboot & all is good :p **

NdisWrapper-utils 1.1-5

NdisWrapper-utils-1.1 1.15

NdisWrapper-utils-1.8


:KS This is a Known issue for Edgy installs & up Grade. This seems to be the only fix right now. ](*,)

---

### Post by TrendyDark on 2006-10-31
Are you sure this works correctly? anyone test it yet. . .

I'm still using Dapper until I can find a working fix for ndiswrapper, which I depend on to access the internet.

---

### Post by Latinhacker31 on 2006-10-31
I just intstalled Ubuntu 6.10 and install the NDIS 1.8 with the other and when I run modprobe ndiswrapper to load my wpn111 wireless USB stick the computer freezes and I have to reboot. Guess I should have stayed on Ubuntu 6.0.6 which was working fine. Does anyone know away around this. I need to be able to get into the Internet with my wireless card.:-k

---

### Post by Jan Hrbacek on 2006-10-31
I have Ubuntu 6.10 on Latitude D820. Installed ndiswrapper included on CD (version 1.8) and win driver for wireless Dell 1490 Minicard. 

Instalation of ndiswrapper and of the driver was without any problem, however, performance is far from optimal. I get messages such as:

changing device from wlan0 to eth1
eth1: link is not ready

iwconfig detects wireless all the time, however ifconfig shows it sometimes and sometimes not...

iwlist eth1 scanning doesn't find anything, however wpa_supplicant at least finds some networks when scanning. cannot really try to connect as they are password protected and I do not know the password...

---

### Post by nyinge on 2006-10-31
> changing device from wlan0 to eth1
Is it Edgy or ndiswrapper changing the device to eth1 deliberately?  Not that it's a bad thing, but I'm just wondering.  I didn't notice the change before though.

---

### Post by Jan Hrbacek on 2006-10-31
Sorry, I have found out that quiting from

sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dndiswrapper -dd 

using Ctrl+C, I actually cause to bring the wireless down.
Once I bring it up again, it is fine...

---

### Post by Stinger on 2006-10-31
> **-Chi.0 said:**
> What you will need to do is go into your Package Manager of you choice, and  type ***_ndis_*** in the seach box

**[Arrow key down]** [I]and make sure the following 4 packagers are installed.
[/I]
NdisWrapper-common 1.18 <-- **This is the 1 that was not installed, You must install this then reboot & all is good :p **

NdisWrapper-utils 1.1-5

NdisWrapper-utils-1.1 1.15

NdisWrapper-utils-1.8


:KS This is a Known issue for Edgy installs & up Grade. This seems to be the only fix right now. ](*,)

I only need NdisWrapper-common 1.18 and NdisWrapper-utils-1.8 to get my ASUS WL-138g working with ndiswrapper , you can read about it here
[Howto Install ASUS Wl-138g in edgy (ndiswrapper)]("http://www.ubuntuforums.org/showthread.php?t=288341&highlight=wl-138g").

---

### Post by -Chi.0 on 2006-10-31
> **-Chi.0 said:**
> What you will need to do is go into your Package Manager of you choice, and  type ***_ndis_*** in the seach box

**[Arrow key down]** [I]and make sure the following 4 packagers are installed.
[/I]
NdisWrapper-common 1.18 <-- **This is the 1 that was not installed, You must install this then reboot & all is good :p **

NdisWrapper-utils 1.1-5 <-- *you will only have these if you upgrade*

NdisWrapper-utils-1.1 1.15 <-- *you will only have these if you upgrade*

NdisWrapper-utils-1.8 <-- *you need this one 2*


:KS This is a Known issue for Edgy installs & up Grade. This seems to be the only fix right now. ](*,)

This is only a temp fix & is a known issue w/ Edgy & this is cased by the new Kernal. It has some thing wrong w/ DHCP & still being worked on. [-( 

B\c of this you must fix NdisWrapper & make shure you a using Wlan0 not Eth1. Then renew & Repeat or switch back to the Dapper kernel then all is good. I Will still look for the bug in the Kernal that is Prob.:confused: 

So right now I'm looking in the Kernels line by line to see if their are any conflicts. ](*,)

_***If you have any questions just keep on Replying & Subscribe Under Instant email notification***_

[I]
I hope this update helps[/I] \\:D/ =D>

---

### Post by mavr on 2006-11-01
i still can't modprobe ndiswrapper. I get an error.

---

### Post by -Chi.0 on 2006-11-01
> **mavr said:**
> i still can't modprobe ndiswrapper. I get an error.

This is b\c of the new Kernel it does not handle NdisWrapper correctly & does not fully support DHCP at this time. ](*,) 

This fix will only allow you to get on the net, Sorry still working for a Better fix at this time

---

### Post by WhiteStool on 2006-11-01
So does that mean I'm stuck with... *shudder* windows for now?

---

### Post by paul6 on 2006-11-01
Thanks topic creator, "sudo modprobe ndiswrapper" was giving me an error until I installed that extra package.

---

### Post by -Chi.0 on 2006-11-01
> **WhiteStool said:**
> So does that mean I'm stuck with... *shudder* windows for now?

Well no not for now right now their are 3 options

1.) Do the NdisWrapper update like I posted before & just deal. ](*,) 
2.) Do that update Edgy & use the Dapper Kernel.
3.) Just Keep using Dapper & don't do the upgrade.

My advise would be to Only use Windows if you @ work or @ your moms house & this is only b\c you don't have a Lappy w/ a install of Linux.

---

### Post by mavr on 2006-11-05
i had troubles, my ndiswrapper was working properly but i couldn't get my wlan usb light to blink. I followed the advice to reboot without the usb connected and then when i connected it all worked. Try it too people. It seems like ndiwsrapper didn't load properly at boot if the usb was connected.  Thanks to everybody for the help

---

### Post by Cesare250495 on 2006-11-15
ShuttleX g62 running P4 2.8Ghz (eth0 on board), 1Gb RAM, 2 SATA Disks, 1 Fwire disk (500Gb total), Wlan on D-Link DWL-G132.

I had the same problem with D-Link DWL-G132 USB wireless dongle.
Well, the problem is a conflict (during bootstrap and during modprobe ndiswrapper) with the IRQ assigned to eth0.
It seems they shared the same IRQ (17), and this is not good.
If you try "sudo modeprobe ndiswrapper" and you obtain a "segmentation error" or a "line 144" error on ndiswrapper.ok (kernel module), try do disconnect your eth0 and to turn it off with the administration tool.
Then redo "sudo modprobe ndiswrapper" and (after 2 days of hard work, reinstalling all around) all is going well.
Another issue exists during bootstrap. The system freezes on "network configuration". The solution (for now) is to disable eth0 card in the bios (mine is onboard) and use only Wlan on USB.

Hope this helps.

-- 
Cesare

---

### Post by ddo on 2006-11-16
> **Jan Hrbacek said:**
> I have Ubuntu 6.10 on Latitude D820. Installed ndiswrapper included on CD (version 1.8) and win driver for wireless Dell 1490 Minicard. 

Instalation of ndiswrapper and of the driver was without any problem, however, performance is far from optimal. I get messages such as:

changing device from wlan0 to eth1
eth1: link is not ready

iwconfig detects wireless all the time, however ifconfig shows it sometimes and sometimes not...

iwlist eth1 scanning doesn't find anything, however wpa_supplicant at least finds some networks when scanning. cannot really try to connect as they are password protected and I do not know the password...

> **Jan Hrbacek said:**
> I have Ubuntu 6.10 on Latitude D820. Installed ndiswrapper included on CD (version 1.8) and win driver for wireless Dell 1490 Minicard. 

Instalation of ndiswrapper and of the driver was without any problem, however, performance is far from optimal. I get messages such as:

changing device from wlan0 to eth1
eth1: link is not ready

iwconfig detects wireless all the time, however ifconfig shows it sometimes and sometimes not...

iwlist eth1 scanning doesn't find anything, however wpa_supplicant at least finds some networks when scanning. cannot really try to connect as they are password protected and I do not know the password...


Hi,
I am a newbie and I have the same D820 with Dell 1490 minicard with Ubuntu 6.10, but I have not been able to get it to work at all .
Can you please show me the steps.

Thanks in advance,

ddo

---

### Post by Papa-san on 2006-11-16
OK... So I am burning a new copy of Dapper, and waiting to hear of success!

(Thanks for all the hard work guys... Those of us who cannot tell the difference between a kernel and a POP server depend on you!) :)

EDIT: Just thought about it... my avatar needs work... I quit smoking last week.... lol

---

### Post by Jan Hrbacek on 2006-11-17
> **ddo said:**
> I am a newbie and I have the same D820 with Dell 1490 minicard with Ubuntu 6.10, but I have not been able to get it to work at all .
Can you please show me the steps.


I hope the HOWTO helps:
[http://www.ubuntuforums.org/showthread.php?t=301527](http://www.ubuntuforums.org/showthread.php?t=301527)

---

### Post by hayim on 2007-03-07
fixed!

OK, i had the same problem as [[COLOR="Blue"]this guy[/COLOR]]("http://ubuntuforums.org/showthread.php?t=279428"), namely i had **no wlan0** after the upgrade to Edgy. 

Following -Chi.0 i checked the installed packages and found (x-installed, o-not)

[B]x  ndisgtk                     1.18-1ubuntu2
o  ndiswrapper-common     1.18-1ubuntu2
o  ndiswrapper-source       1.18-1ubuntu2
x  ndiswrapper-utils           1.1-5
o  ndiswrapper-utils-1.1     1.1-5 
o  ndiswrapper-utils-1.8     1.18-1ubuntu2 [/B]

now as you can see, the GUI ndiswrapper app thats under System>Administration>Windows Wireless Drivers was installed (ndiskgtk), and the other,ndiswrapper-utils, is a **dummy package**!

So I installed common, and the two other utils (1.1 and 1.8), and i *removed* the ndisgtk and the dummy package, and after rebooting my wlan0 was back!

probably i dont need both the 1.1 and the 1.8 utils packages? And why did edgy give me the dummy package and the GUI but not the actual module!?

ps thx -Chi.0

---

### Post by -Chi.0 on 2007-03-07
> **hayim said:**
> fixed!

OK, i had the same problem as [[COLOR="Blue"]this guy[/COLOR]]("http://ubuntuforums.org/showthread.php?t=279428"), namely i had **no wlan0** after the upgrade to Edgy. 

Following -Chi.0 i checked the installed packages and found (x-installed, o-not)

[B]x  ndisgtk                     1.18-1ubuntu2
o  ndiswrapper-common     1.18-1ubuntu2
o  ndiswrapper-source       1.18-1ubuntu2
x  ndiswrapper-utils           1.1-5
o  ndiswrapper-utils-1.1     1.1-5 
o  ndiswrapper-utils-1.8     1.18-1ubuntu2 [/B]

now as you can see, the GUI ndiswrapper app thats under System>Administration>Windows Wireless Drivers was installed (ndiskgtk), and the other,ndiswrapper-utils, is a **dummy package**!

So I installed common, and the two other utils (1.1 and 1.8), and i *removed* the ndisgtk and the dummy package, and after rebooting my wlan0 was back!

probably i dont need both the 1.1 and the 1.8 utils packages? And why did edgy give me the dummy package and the GUI but not the actual module!?

ps thx -Chi.0

Topic Update!
This is still a prob w/ some setups & I can't find out why some Peeps get the dummy pakage & some don't. 

But if you want a nice & simple Graphical NdisWrapper App then use the one from Automatix Repos. The App is called "Windows Wireless Driver " & will show up under settings in you menu after install :)

This little App is nice but you still have to fix the packages :)

Good day all :guitar:

---

