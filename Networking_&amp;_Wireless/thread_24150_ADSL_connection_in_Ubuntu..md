---
title: "ADSL connection in Ubuntu."
date: 2005-04-05
forum: Networking &amp; Wireless
---

### Post by Sitsuj on 2005-04-05
Could You tell me how to connect to the internet via ADSL modem? The modem is connected to PC by USB device (Sagem F@st 800). I would like to mention, that I have completely NO idea, how to install drivers, configure nework etc, so please, explain everything STEP-BY-STEP. Thank You.

---

### Post by kadissie on 2005-04-06
Having never connected via ADSL modem, it's kind of odd that I'm replying to this.  However, I'm setting up a friend's connection on Friday and so the following are general comments which I will take with me....
* You should not have to install drivers.
* Ubuntu being as user-friendly as it is, you are not going to have to do to much configuration and hopefully nothing that can't be done through graphical interfaces.  However, in my description below I'm going to take you to the command-line (right-click on your desktop and choose "Open terminal") to check how things are going.

So, the procedure should be
1. Plug the USB modem into your computer.
2. Wait a few seconds for the device to be registered, then at the command-line type "lsusb".  This lists the usb devices on your system, and should include something about your Sagem 800 modem.  If it's not there, tell us about it on the forum (include the output of the "lsusb" and "lsmod" commands).
3. Now fire up the graphical network configurator: go to System -> Administration -> Network (I think those are the right meny entries, I'm not on Ubuntu right now).  You'll need to type in your password.
4. Ubuntu may already have an entry for your usb modem device, in which case all you need to do is configure it with your username and password by clicking on the edit button.
5. If you've got this far, click on the "Activate" button and see if it all works!  If it doesn't, tell us about any error messages and include the output of the command "ifconfig -a".

R.

---

### Post by Corn on 2005-04-28
i did what you suggested and it doesn't work

> marek@ubuntu:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 1110:9021 Analog Devices Canada, Ltd (Allied Telesyn)
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 03f0:0604 Hewlett-Packard DeskJet 840c
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
marek@ubuntu:~$ lsmod
Module                  Size  Used by
af_packet              20744  2
eagle_usb             120512  0
ppp_async              10752  0
ppp_generic            27668  1 ppp_async
slhc                    7040  1 ppp_generic
crc_ccitt               2176  1 ppp_async
ipv6                  229504  6
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
usblp                  12032  0
snd_via82xx            25248  2
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
i2c_viapro              7436  0
i2c_core               21264  1 i2c_viapro
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  5 eagle_usb,usblp,ehci_hcd,uhci_hcd
sata_via                8196  0
libata                 44548  1 sata_via
scsi_mod              119936  1 libata
sk98lin               149216  0
pci_hotplug            30512  0
via_agp                 9216  1
agpgart                31784  1 via_agp
analog                 10784  0
gameport                4608  2 snd_via82xx,analog
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   12928  1
fat                    37792  1 vfat
md                     43856  0
evdev                   9088  0
tsdev                   7488  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
via82cxxx              12956  1
ide_disk               18176  4
ide_core              118988  4 ide_cd,ide_generic,via82cxxx,ide_disk
unix                   26164  848
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
marek@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:AC:DD:9B
          inet6 addr: fe80::20c:6eff:feac:dd9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Memory:e5800000-0

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:900 errors:0 dropped:0 overruns:0 frame:0
          TX packets:900 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:80330 (78.4 KiB)  TX bytes:80330 (78.4 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


---

### Post by Craig Gilman on 2005-05-07
I have the same usb modem and I'm also trying to work out how to get onto the net with ubuntu using it! 

I'm using it on my windoze laptop at the moment to send this and it's fine...

There is an installation CD with my modem that has linux drivers on it.. says its for mandrake, fedora and suse - there's a debian folder on the disk.. I assume that following the instructions in the pdfs here should work... 

Problem - I need "gcc" to be installed...  something about a c compiler?

I'm a complete novice here too so I don't know how to get this installed. Ideally i need to download on the laptop - save on a disk and stick it in my ubuntu box.. then continue the process and hope it works... that's assuming that my box is recognising usb!

I heard that usb and linux are bad bedfellows... 

after all that I need to know how to get on the net using the thing! 



Any Linux Gurus please HELP!!!!

---

### Post by timmy_ on 2005-05-23
Hi!
I just got Linux Ubuntu, and i have an problem to connect to the internet.
My internet device is: Marvell Yukon 88E8001/8003/8010 PCI Gigabit Ethernet Controller. Could someone help how i just get connected to the internet with ubuntu?? ive got 4/1mb internet ](*,) 
PLEASE someone HELP me!!

---

### Post by coolclassic on 2005-06-08
Hi 
I have just finnished installing kubuntu and I am attempting to get my sagem 800fast modem working as well. I heave used the drivers from: [http://dev.eagle-usb.org/wakka.php?wiki=TestEagleUs](http://dev.eagle-usb.org/wakka.php?wiki=TestEagleUs) . I will let you know how I got on or you might be there first, let me know.

---

### Post by cwaldbieser on 2005-06-08
Connecting to the Internet with DSL can either be very simple, or very difficult.  Most of the difficulties will either boil down to something nutty your ISP is doing, or your choice of hardware.  The actual configuration of the software is really easy.

Things usually are at the simplest when the hardware you are using is some kind of (wired) ethernet card that is in one of your computer's PCI slots.  (Cards that go in these slots look like electronic circuit boards that are installed inside the computer case-- only a strip of metal with various connectors is usually exposed on the back of the case.  For example, the jack on an ethernet card).  Also, it helps if your ISP provides you with the relevant connection information in addition to their home-brew software for connecting.

If you have a USB network adapter or a wireless adapter, then the situation gets more dicey, simply because there are more things that can go wrong.  This is *not* specific to Ubuntu or Linux in general.  In fact, when I first tried to set up my DSL connection, it was on WinXP home edition, and just about everything that could go wrong, went wrong.  After spending about a half hour talking to a very patient technical support person, everything was set up.  Once I had the right settings, setting up the connection for my Ubuntu machine was a breeze.

OK, for the first step, I recommend that anybody new to DSL in general take a few minutes to understand how the whole thing is supposed to work.  Basically, your broadband signal is going to ride on top of your normal phone line signal.  In order for this to work, the DSL provider probably gave you a couple of filters, and a DSL modem.

The filters I have resemble rectangular hunks of plastic with a phone jack on one end and a little phone cord on the other.  This plugs in between your hand set and the wall jack.  The purpose is this piece of hardware is to keep signals from the handset from interfering with the broadband signals and visa versa.

There are many models of DSL modem.  Mine looks like a rectangular piece of plastic with 4 status lights on it (USB, Ethernet, DSL, and power).  You either plug the modem into your computer using an ethernet card or a USB port.  The corresponding light lights up if the connection is made.  Your modem may or may not have both type of connectors.  The DSL light turns on and stays solid once the modem does its magic handshake with the ISP's end of things.  The power light is self explanatory.  The Ethernet or USB light is the one that will blink as information travels acrss your modem.

If you have a home network, your DSL modem should plug into your home router instead of your computer.  If you only have one PC, it plugs directly into the modem.

With my ISP and modem, there was some kind of configuration that the software was supposed to do to set up the modem.  Unfortunately and fortunately, the software failed to work.  This was unfortunate because I could not connect-- but it was fortunate because I got to learn a little bit about how to configure the modem.

Like many modern routers, the modem is configured by pointing a web browser at a mini-webserver built inside the modem.  The web pages you see will let you configure the modem, which usually means entering a password the ISP gave you somewhere.  Since the modems and ISPs are potentially all different, there is not a lot of help I can give you there.

The configuration software my ISP provided only ran on Windows or Mac, so it was necessary for me to use a Windows system until the modem was configured.  Once I had the settings entered, I was able to switch over to my Ubuntu box without a hitch.  Networking support in Linux is absurdly simple.  You can configure via one of several GUIs.  In Gnome, I believe it is System -> Administration -> Networking.  In KDE, you can go to the control center and choose Internet and Networking.  To be honest, I use the command line, because there is just one command that does pretty much all the work, ifconfig.  Of course, on booting into Ubuntu, those settings were pretty much auto-detected and handled for me, but I will go over ifconfig basics for the curious.

If you type

$ ifconfig -a

You will get a list of all of your network interfaces, including lo (the loopback interface).  If you have an ethernet card, you will probably see it as something like eth0.  If you want to deactivate an interface:

$ sudo ifconfig eth0 down

turns off my ethernet card.  If I want to assign it an IP address and bring it back up:

$ sudo ifconfig eth0 192.168.0.2 netmask 255.255.0.0 up

The 192.168.0.2 is the IP address of my Ubuntu machine on my local network.  The netmask is a little tricky to explain.  Basically, you put a 255 for every part of your internal LAN address that is the same for all the PCs on your LAN.  You use 0s for the parts that change.  The up tells the interface to turn itself on.

One other command that is occasionally useful is route.  If for some reason you need to set up your networking manually, you may have to set up a default route to your DSL modem.  For more details:

$ man route
$ man ifconfig

For wireless devices, things get a little bit more hairy.  I have had some limited success in this area, but still have some occasional trouble with my wireless adapters under Ubuntu.

---

