---
title: "edgy wireless netgear wpn111 ndiswrapper problems...  please may i have some guidance"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by axio720 on 2007-01-25
hello all,
   i am a fairly new user of ubuntu.  i really enjoy learning about it though.  i recently got a netgear wireless router and wpn111 usb adapter.  i have been trying to install the adapter for over a week.  i have trolled the forums looking for answers and have probably been given everything except step one.  i can not install ndiswrapper to save my life. i have been through numerous forums and site trying to help me. yet i have not found anything to help install when there is no ethernet connection on the laptop.  
by the way here are some of my specs
ibm thinkpad r40 
60gb hard drive
256 memory
ethernet port has been bad for a few years.
dual boot xp pro and edgy


the 'make distclean' went through what looked fine.  after that there were errors in the 'make' and the 'make install'.  i really have been trying but it seems that no one installs without internet connection.  i know i'm a noob but please help.

also let me know if there is more info needed by you all in order to lead me down the path of righteousness.

---

### Post by Floppyjoe on 2007-01-25
You can use the Ubuntu Install CD to install ndiswrapper on edgy. 
Goto System/Administration/Synaptic Package Manager.
Click on Edit/Add CD-Rom. Then click reload and search for ndiswrapper.

---

### Post by axio720 on 2007-01-25
thank you so much for the help.  now all i need to do i find out how to install this netgear wpn111 usb adapter.  so...  any takers???
not sure where to even start??

thanks

nathan

---

### Post by Floppyjoe on 2007-01-25
You need to take the Windows driver disk and get the driver files off there and put them onto your Ubuntu system somewhere. There should be a driver.inf, a driver.sys and possibly a driver.bin file that you need to copy to your computer. I would put these in my home folder. Then you need to open up a terminal by selecting Applications/Accessories/Terminal.

Then enter the following command to install the driver.
```
sudo ndiswrapper -i driver.inf
```
Where driver=the name of the driver you copied earlier.

Then enter:
```
ndiswrapper -l
```
To see if the driver and hardware show up properly.
You should see something like this:
> Installed drivers:
drivername                driver installed,  hardware present

Then enter the command:
```
ndiswrapper -m
```
to save the module into the .conf file

I would also add the word "ndiswrapper" without the quotes to the end of the file /etc/modules.
```
sudo gedit /etc/modules
```
and add the word ndiswrapper. Then save this file.

Next I would try:
```
sudo modprobe ndiswrapper
```
this loads the ndiswrapper driver.

Next enter the following to see what your wireless interface is called:
```
iwconfig
```

Then you need to edit your /etc/network/interfaces file.
```
sudo gedit /etc/network/interfaces
```

You should add something like this to your network interface:
> wireless-essid YourRouterEssid
wireless-mode managed
wireless-channel 7
to get a file that may look something like this:
> 
auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid YourRouterEssid
wireless-mode managed
wireless-channel 7


Where the wireless-channel is the channel that your router is set to. Save this file.

This is assuming you don't have encryption or mac filtering turned on in your router settings.
Enter the following to connect to your router:The wlan0 could be different depending upon what your interface is called:
```
sudo dhclient wlan0
```

Edit: You may need to reboot the computer for these configs to be properly set.
This should get you connected to your router. If you have any problems post the results of iwconfig and the /etc/network/interfaces file here.

---

### Post by axio720 on 2007-01-25
here are all the responses to your instructions

it looked like it worked alright until iwconfig had no extensions...  but i really dont know what that means anyways.

here:

axio@Lightness:~$ sudo ndiswrapper -i netwpn11.inf
netwpn11 is already installed. Use -e to remove it
axio@Lightness:~$ sudo ndiswrapper -l
Installed drivers:
netwpn11                driver installed, hardware present 
axio@Lightness:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

axio@Lightness:~$ sudo gedit /etc/modules


AFTER ADDING IT LOOKS LIKE THIS:	

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
ndiswrapper

	END

axio@Lightness:~$ sudo modprobe ndiswrapper 
axio@Lightness:~$ iwconfig 
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

axio@Lightness:~$ sudo gedit /etc/network/interfaces

AFTER ADDING IT LOOKS LIKE THIS:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid AXIO
wireless-mode managed
wireless-channel 6

	END

axio@Lightness:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
axio@Lightness:~$

---

### Post by Floppyjoe on 2007-01-25
Yes it seemed to work alright until the iwconfig command showed no wireless extensions.
Please make sure your wired ethernet Lan card is disabled and or the cable is not connected to your computer when you boot up.

Post output of:
> ifconfig
 and 
> iwconfig
The above is just to find out the name of the wireless interface whether it is wlan0 or eth1 or some other designation.
and
```
lsusb
```
and the relevant part of:
```
lshw
```
Could you please post the results of the command:
```
lsmod
```

There may be a conflict with a native driver that needs to be blacklisted.

---

### Post by axio720 on 2007-01-26
here you go again.  again thanks for the help.  i appriciate it alot.

axio@Lightness:~$ sudo ifconfig
Password:
eth0      Link encap:Ethernet  HWaddr 00:06:1B:D8:49:59  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1284 (1.2 KiB)  TX bytes:1284 (1.2 KiB)

axio@Lightness:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.

axio@Lightness:~$ sudo lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
axio@Lightness:~$ sudo lsmod
Module                  Size  Used by
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
nvram                  10376  1 
uinput                 10368  1 
radeon                118816  2 
drm                    74644  3 radeon
speedstep_lib           5764  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
ibm_acpi               28672  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
nls_utf8                3200  1 
ntfs                  112116  1 
nls_iso8859_1           5248  1 
nls_cp437               6912  1 
vfat                   14720  1 
fat                    56348  1 vfat
ndiswrapper           200724  0 
sbp2                   24584  0 
scsi_mod              144648  1 sbp2
lp                     12964  0 
af_packet              24584  2 
pcmcia                 40380  0 
joydev                 11200  0 
tsdev                   9152  0 
psmouse                41352  0 
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
irtty_sir              10112  0 
sir_dev                18308  1 irtty_sir
nsc_ircc               25100  0 
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
evdev                  11392  3 
e100                   38020  0 
mii                     6912  1 e100
serio_raw               8452  0 
irda                  214332  3 irtty_sir,sir_dev,nsc_ircc
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
crc_ccitt               3200  1 irda
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
pcspkr                  4352  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
intel_agp              26012  1 
agpgart                34888  2 drm,intel_agp
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142728  1 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  4 ndiswrapper,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  5 
piix                   11780  1 
generic                 5764  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability
axio@Lightness:~$

---

### Post by Floppyjoe on 2007-01-26
I'm afraid for the time being you may have me stumped here. I can't see why your Usb device is not showing up under iwconfig or lsusb. If your driver is loaded and hardware is present one would think it would show up. One possibility might be that you may need to delete your ndiswrapper driver and reinstall it:

This command lists the old driver:
```
ndiswrapper -l
```

This command deletes the old driver.
```
sudo ndiswrapper -e drivername
```
Then this command installs the driver with the newer ndiswrapper utils.
```
sudo ndiswrapper-1.8 -i driver.inf
```
Then reboot if you don't get an error with this last command

Otherwise I am stumped here. Does anybody else have some ideas?

---

### Post by axio720 on 2007-01-26
that worked but nothing in iwconfig or lsusb after the reboot
also i do get something else in lsusb if i plug the usb adapter in.  you previous instructions told me not to so i hadnt done that since.

any other ideas anyone????

thanks

nathan

---

### Post by Floppyjoe on 2007-01-26
The Usb adapter must be plugged in for this to work properly.:)
I meant earlier that your ethernet cable must not be plugged in and the ethernet card(HardWired) connection must be disabled in System/Administration/Networking.

---

### Post by axio720 on 2007-01-26
i did that and it still won't work.  same as you. i have no clue.  please..  if anyone can help me would appriciate it.  

thanks,

nathan

---

### Post by axio720 on 2007-01-26
is the anyone else out there to help???

nathan

---

### Post by Floppyjoe on 2007-01-26
What is the result of iwconfig and lsusb when the usb adapter is plugged in?

---

### Post by axio720 on 2007-01-27
here
axio@Lightness: $ iwconfig
lo        no wireless extensions.

irda0   no wireless extensions.

eth0    no wireless extensions.

sit0     no wireless extensions.


axio@Lightness: $ lsusb
Bus 004 Device 002: ID 1385:5f01
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

anything else you can think of???

---

### Post by axio720 on 2007-01-27
can anyone help???

---

### Post by hggdh on 2007-01-27
You have not posted the output of 'ndiswrapper -l' -- per what you show in output, the wpn111 does not seem to be recognised -- at least so far.

The PCI id matches with what you have shown in the 'lsusb' output, so the dongle was attached at this point in time.

Now...

1. what does 'ndiswrapper -l' output?

2. what does ndiswrapper say about the dongle when you connect it? Run 'dmesg | grep ndis' and post the output.

Also, the ndiswrapper wiki post this about the wpn111 (see [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N):](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N):)

> Card: Netgear WPN111 108Mbps RangeMAX USB (with super G/MIMO)

    * Chipset: Atheros USB
    * pciid: 1358:5f01
    * Driver: Windows XP driver available on the Netgear CD: netwpn11.inf + wpn111.sys + ar5523.bin
    * Other: Install both wpn11 and athfmwdl drivers. 

---

### Post by axio720 on 2007-01-27
axio@Lightness:$ sudo ndiswrapper -l
Password:
Installed drivers:
netwpn11                      driver installed
axio@Lightness:$sudo dmesg | grep ndis
[17179604.048000] ndiswrapper version 1.34 loaded (preempt=no,smp=yes)
[17179604.076000] usbcore: registered new driver ndiswrapper
axio720@Lightness:$

also i dont have my driver cd long story 
also i dont have the athfmwdl drivers.

i appriciate it

thanks,

nathan

---

### Post by hggdh on 2007-01-27
You are welcome.

The correct response for the 'ndiswrapper -l ' would be 'driver present, hardware present'. So... your driver is indeed not up.

You can grab the driver from NetGear itself, at [http://kbserver.netgear.com/products/WPN111.asp](http://kbserver.netgear.com/products/WPN111.asp)

Then... you will have to run cabextract on the .exe file, and then unshield on the .cab files.

This is about as far as I can go, since I do not have the thingy myself.

---

### Post by axio720 on 2007-01-27
it says hardware present sorry i didnt copy that right.
my linux laptop doesnt wont have internet until wireless works because i dont have a functioning ethernet or modem

---

### Post by Floppyjoe on 2007-01-27
> **hggdh said:**
> You are welcome.

The correct response for the 'ndiswrapper -l ' would be 'driver present, hardware present'. So... your driver is indeed not up.

You can grab the driver from NetGear itself, at [http://kbserver.netgear.com/products/WPN111.asp](http://kbserver.netgear.com/products/WPN111.asp)

Then... you will have to run cabextract on the .exe file, and then unshield on the .cab files.

This is about as far as I can go, since I do not have the thingy myself.
How do you do this cabextract thing? I tried to change the extension to .zip and then use acrhive manager to open it but no luck. when I enter "cabextract wpn111_1_1.exe" I get:
bash: cabextract: command not found.

any suggestions?

---

### Post by hggdh on 2007-01-27
Sorry.

sudo apt-get install cabextract unshield

This will install both utilities.

---

### Post by axio720 on 2007-01-27
thank you but i don't believe i need to do that process.  i didn't know if you saw that i said that i mistyped and that hardware was present.  so i am back to were i was b4.  i don't mean to sound impatient (even though i am) i just have been so frustrated with this and now i believe part of the problem is i don't have the athfmwdl.inf to install also.  and i don't know any other place to get it other than from the install disc.  you see two days after i installed the WPN111 on my windows partition i seemed to have misplaced the install discs.  for the router and the adapter.  so i have no way to upgrade the firmware or have access to that inf file.

sorry about the rant.
nathan

P.S. any aptget command won't work because the laptop has no connection without wireless. unless i was in xp.

---

### Post by Floppyjoe on 2007-01-27
So does there need to be 2 drivers installed for this to work then?
> 
Card: Netgear WPN111 108Mbps RangeMAX USB (with super G/MIMO)

* Chipset: Atheros USB
* pciid: 1358:5f01
* Driver: Windows XP driver available on the Netgear CD: netwpn11.inf + wpn111.sys + ar5523.bin
* Other: Install both wpn11 and athfmwdl drivers.

Or do just these three files need to be present during the install?

---

### Post by Floppyjoe on 2007-01-27
Can you tell me the name of all the files you had present when you installed the driver?
I attached a file on the previous post with some of the driver files listed on that page for ndiswrapper compatibility.

---

### Post by axio720 on 2007-01-28
wpn111.sys, ar5523.bin, and netwpn11.inf
like i said... the ndiswrapper site said i needed the athfmwdl.inf file which i believe is the firmware driver.  so i don't know where to get it.  i looked all over the netgear site and can't find it.  also to restate that i havent been able to find the install cd's for weeks now.

thanks for the help

---

### Post by phossal on 2007-01-28
I've read this thread from the beginning. If you don't mind, would you please paste the output to the following again (without the *mistypes*)? 
```
ndiswrapper -v
```
 
and:
```
ndiswrapper -l
```

---

### Post by Floppyjoe on 2007-01-28
I found another post for a different device where the user went into windows and searched for the files athfmwdl.inf and athfmwdl.sys on his system then copied them to his Ubuntu via Cd or Usb flash drive. I searched through the whole driver package and could not find these files but perhaps they are created during the installation of the drivers in Windows.

---

### Post by axio720 on 2007-01-28
axio720@Lightness:$ sudo ndiswrapper -v
Password:
utils Error: no version specified!
driver version:          1.34
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
axio720@Lightness:$ sudo ndiswrapper -l
Installed drivers:
netwpn11                         driver installed
axio720@Lightness:$

Floppyjoe
thanks, i will try yopur suggestion.
thanks
nathan

---

### Post by phossal on 2007-01-28
Did you run the following after installing the .inf driver? 

For example, after issuing sudo -i driver.inf, did you do the following:
```
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```

Also, have you referred to this thread: [wpn111]("http://ubuntuforums.org/showthread.php?t=103229&highlight=wpn111"). It seems to make it obvious which files are required? It appears a lot of people have had this trouble. Also, not the experience the user had who was dual-booting with Windows, which was causing conflict.

---

### Post by axio720 on 2007-01-31
sorry i had to take a little break from trying to figure this out.  my brain still feels fried so not much help it did.  

yes i tried all of those suggestions and checked out all those walkthrough type things.  Another reason its been a few days.  nothing seems to work.  i just wonder if i should just give up and come back in a few weeks or months to see if someone has figured it out.

all i really need is that athfmwdl.inf driver.  if i install that with the netwpn11.inf driver then i believe it should work.  i also read about a athwpn11.inf  which could be something similar the the other ath driver.  if anyone can help.... please please please.  i would be so happy to get this working so i can ditch most of my XP side.

thanks,
nathan

p.s. floppy i searched my xp side over and over and couldnt find anything like it.  sorry

---

### Post by phossal on 2007-01-31
I've helped a few people install Netgear products successfully. Not just my own, but completely different devices. I am willing to walk through the steps with you, but I admit upfront that I don't have a quick fix. Are you willing to continue trying?

---

### Post by axio720 on 2007-01-31
phossal,
    yes definately.
FYI i pretty much am doing this in my free time which maybe at lunch or midnight.  what i am saying is that I understand it may take a while to do it and i am willing to put the time in.  it just may not be all at once.  again thank you for your help.  i hope some day to assist others in the ways i have been assisted.

thanks,
nathan

---

### Post by phossal on 2007-01-31
All right, I have a couple of questions, because I see the process below has been messy. It appears you upgraded ndiswrapper. 

Does the following command show that you're using version 1.34 or better?
```
ndiswrapper -v
```

Does the following command show that your hardware *is installed*: ie "hardware present"
```
ndiswrapper -l
```

Can you connect to the internet (using some other connection) from the computer you're trying to install this on?

Can you *easily* cut and paste the output from the terminal so that I can see it? (or can you post images of the bash window?)

Finally, some suggestions:

- I recommend *not* configuring /etc/network/interfaces until you have a connection set up.
- Getting the hardware to work is a 2-part process. Part 1 means the device is recognized and using the correct drivers. Part 2 is establishing a connection to the router. To accomplish part 1, nothing is needed but ndiswrapper and iwconfig (sometimes dmesg). We don't configure /etc/network/interfaces, use ifconfig, etc. Avoid "network manager"

---

### Post by axio720 on 2007-01-31
-v gave this output

utils Error: no version specified!
driver version:          1.34
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1

-l gave this output

installed drivers:
netwpn11               driver installed, hardware present

i did this before pluging in the adapter and it did not say hardware present. duh.
so ipluged it in and got it.  does it matter if i plug it in after the boot up??
should i do it over again with it plug in before boot??

No I actually can not connect tothe interrnet unless I am using the Windows XP boot with the wireless adapter.

I have to email a document of the cut part from the terminal to myself.  I actually am using my work laptop to use the internet.  I only turn the other one one when I am trying to fix the wireless.  The computer i am using right now is an Apple PowerBook G4.  I would love to use internet off of the other one but the NIC is bad, damaged in Afghanistan.  So I am lost there.  So what I have been doing is downloading anything in need on my Mac and either putting it on a usb or emailing it to myself.  By the way I also have a dual boot desktop with XP and Ubuntu Edgy on it.  It is hardwire to the router.  But maybe i could trouble shoot with it??? Let me know what you think. 

Thanks,

Nathan

---

### Post by axio720 on 2007-02-02
is anyone out there????

---

### Post by Floppyjoe on 2007-02-02
Did you try to run the driver installer on a Windows system and search for the parts that you need?Then transfer them to your Ubuntu system?

---

### Post by axio720 on 2007-02-02
i did and it didn't work.  i even simplified the search to include any file with ath in it and none matched. 
thanks though
nathan

---

### Post by Floppyjoe on 2007-02-02
I read another post where someone had Windows load the firmware into a different type of USB adapter then unplug it from the computer. Then he booted up Linux and inserted the adapter after it was loaded up. I doubt this will work but it might be worth a try.

---

### Post by axio720 on 2007-02-03
just thought I would let yall know I found my netgear cd's and searched them for the the driver i thought i needed. and i couldnt find it.  anyhelp or suggestions

---

### Post by ollesbrorsa on 2007-02-04
Finally got my usb wpn111 working (on ubuntu 6.10).

Here's a short run down of the steps I took:

Made sure to uninstall ndiswrapper following the ndiswrapper wiki:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall)

Followed this excellent howto:

[http://ubuntuforums.org/showthread.php?t=347889](http://ubuntuforums.org/showthread.php?t=347889)

substituting version 1.35 for 1.37 from this page:

[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

So now I have ndiswrapper 1.37 installed.

I then proceeded to download the newest drivers (wpn111_1_1.exe) from:

[http://kbserver.netgear.com/release_notes/d102794.asp](http://kbserver.netgear.com/release_notes/d102794.asp)

Then in the same directory as wpn111_1_1.exe:

```
cabextract wpn111_1_1.exe
```

Extracted files get dumped in to directoy **Disk1**. You need files contained in file **data1.cab**.

```
unshield -d tempdir x data1.cab
``` (dumping files to dir **tempdir** to avoid excessive clutter, remember to create said dir first...)

Now, the only files I needed to get it working were contained in **tempdir/ntDRV**. Once I got to this point I just followed the "Command line instructions" from here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

As soon as I had done ```
sudo modprobe ndiswrapper
``` the blue led on the wpn111 adapter started flashing. The big bonus was that the network-manager applet that was running picked up the new network interface and all I had to do was choose my AP. I am using dhcp and wpa as well.

Good luck!

/ollesbrorsa

---

### Post by Xierxes on 2007-02-27
Hi all, 

I know that this thread has been inactive for a while, but I thought that I let you know that I followed the instructions in ollesbrorsa's post and got my WPN111 up and running almost straight away. I was having some trouble to begin with, and then when browsing [ _phossal's threads _]("http://phossal.com/thread?view=702216933") it occurred to me that rebooting the machine might help :) .  I also completed steps 6-8 in that that thread and was pleased to see the flashing blue light during startup!  As a newbie, I found the instructions clear and concise and extremely helpful - it seems that support  forums have lost that snobbish edge that stopped me using Linux during the 90's! - pleasing to have a response other than RTFM noob!  I don't think that I will be going back anytime real soon,

Cheers, from a happy convert
Rob

---

### Post by phossal on 2007-02-27
> **Xierxes said:**
> RTFM noob!
lol Rob, I'm going to add that. ;) Regards!

---

### Post by popeyeray on 2007-03-16
I did everything over and then just unplugged the etho (cable), opened a new browser window and found even though it appeared that I wasn't connected due to the connection icons having a red icon next to them, I actually was connected. But now the big question is whether i'll be automatically connected when I reboot without the cable connected. I'll post back and let you know.

---

### Post by popeyeray on 2007-03-16
NO, I was not automatically connected, I tried running a startup script using 
#!/bin/sh
dhclient wlan0

saved it as myscript then

sudo cp myscript /etc/init.d

sudo chmod +x /etc/init.d/myscript



 sudo update-rc.d myscript start 51 S .



(Do not forget the dot: . )



This didn't work, I also tried to add myscript under the "sessions" startup options, NO GO.

The only thing that works right now is to run myscript this way

sudo -s
password
then ./myscript

this outputs
There is already a pid file /var/run/dhclient.pid with pid 7046
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:6c:e1:18:c2
Sending on   LPF/wlan0/00:14:6c:e1:18:c2
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.9 -- renewal in 274642 seconds.

So it's a start.

---

