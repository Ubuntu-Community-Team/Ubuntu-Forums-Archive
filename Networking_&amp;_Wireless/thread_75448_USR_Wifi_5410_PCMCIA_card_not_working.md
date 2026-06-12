---
title: "USR Wifi 5410 PCMCIA card not working"
date: 2005-10-13
forum: Networking &amp; Wireless
---

### Post by tirant on 2005-10-13
The installation detects is as a:

wlan0: Texas Ins. ACX 111 54Mbps Wireless Interface.

But it doesn't work. It doesn't find any AP, it can't connect if specify all the settings, etc...

BTW, where can i set the encription lenght (64, 128, 256bits?)

---

### Post by tirant on 2005-10-16
anyone??

---

### Post by breakthestate on 2005-10-16
Please paste the results from typing "iwconfig" in the terminal.

---

### Post by Robo on 2005-10-28
I am having the same issue, with the same card.  Here are the results ofthe iwconfig:

```

lo        no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"USR8054"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

eth0      no wireless extensions.

```

TIA

---

### Post by ckempo on 2005-11-18
I can't get mine working either - using either the opensource driver and guide at 

"http://houseofcraig.net/acx100_howto.php" 

nor NDISwrapper. 

Has ANYONE got this card working in Linux (I'm trying to connect to a USR9106 Access Point if it makes any difference) ?

---

### Post by Roberto Rosselli on 2005-11-29
I have exactly the same setup (USR 5410 + USR 9106) and exactly the same problems, the funny thing is that I bought this card because it was marked as "Work out of the box" on the Ubuntu Wiki!!! :confused: :confused: :( :( 

Anybody managed to have it work under Ubuntu Breezy?

Ciao!

---

### Post by lazerdave on 2006-01-13
Have any of you gotten it working yet, or given up and gone with a different solution?  If the latter, what did you go with?

---

### Post by ckempo on 2006-01-14
I went with NDISWrapper and got it working (eventually) using some Linksys drivers... can't remember where I got them from though, sorry! A quick Google should help.  WPA Access worked but only if I broadcast my SSID (which I don't usually have enabled on the access point).

I've wiped my partitions since and installed Dapper Flight 2, but haven't attempted to get this set up again, though am watching Network Manager closely as a means to cut down on the wpa_supplicant conf file changes, etc etc.

---

### Post by lazerdave on 2006-01-31
I got it working!  All it took was breaking my drive, reinstalling Ubuntu from scratch.  During installation, I was asked for the SSID I wanted and (when it couldn't get an IP via DHCP) manually assigned an IP and hey, presto!  It worked.

Clearly this isn't a solution for everyone and in the end it didn't teach me anything new, but at least now it's up and surfing.

Thought this might help the next person reading that this card works out of the box.

---

### Post by Roberto Rosselli on 2006-02-08
Fact is, I also re-installed Ubuntu Breezy, and managed to configure the card all right using network-admin, but it doesn't work because it doesn't "see" my wireless access point!!! Under Windows the signal strength is marked as "Excellent", how comes it is invisible under Ubuntu? Perhaps I didn't install some software?

Roberto

---

### Post by lazerdave on 2006-02-13
[QUOTE=Roberto Rosselli]Fact is, I also re-installed Ubuntu Breezy, and managed to configure the card all right using network-admin, but it doesn't work because it doesn't "see" my wireless access point!!!
[/QUOTE]

Hmm, yes.  After trying it on another machine I'm having the same problem as you now.  Everything looks ok on the configuration side but it won't actually connect and obtain an IP.

A quick test showed me that all may not be lost, though.  When I turned WEP off on my router, I was able to connect and surf at lightning speed.  Turn WEP back on and BLAMMO no more IP.

Is the built-in driver with Breezy out of date and we just need to find a new one or are we S.O.L. for the time being?

---

### Post by Roberto Rosselli on 2006-02-15
Well, WEP is off by default in my setup, and I still get no connection to the router. I don't know about the driver, perhaps we should ask on the Dapper dev mailing list? I doubt we'll see an update in breezy backports.

One more thing I'd like to know is *who* marked this card as "works out of the box" and *what* the guy did to have it working: human sacrifices to obscure deities of ethereal connections perhaps? ;)

Ciao!

---

### Post by lazerdave on 2006-02-15
One thing's for sure, I'd like to offer them up to those same obscure deities.  ;-)

Seriously, I'm almost ready to bail on this card and go with a different one if I can get absolute confirmation it'll work.  The left side of my brain keeps telling me to stick with this and learn all I can, but it seems that everyone's mileage varies with this particular device.

NDISWrapper changed nothing for me.  I'd try Driverloader if I wasn't deathly opposed to paying for Linux software and/or if I'd seen absolute proof it worked.

I'm curious which Linksys driver our friend earlier in the thread used.  Might be worth a shot.

---

### Post by Roberto Rosselli on 2006-02-15
I tried the latest Dapper alpha Live CD and there was a slight improvement: the wireless network is detected! Unfortunately that's it, still no sign of a successful DHCP connection, no IP address set for the card. Perhaps using NetworkManager or WifiRadar for Dapper could get the thing to work.

For the moment being, I've reached an almost satisfactory compromise though: I use Freenx under Windows to connect to my desktop box: in fullscreen mode it's almost like the real thing! ;)

Ciao

---

### Post by tirant on 2006-03-07
Here trying the card on 6.04, and nothing is working.

```

wlan0     IEEE 802.11b+/g+  ESSID:"STAA9332D"  Nickname:"acx v0.3.21"
          Mode:Managed  Channel:1  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The only hint i have right now is this. i will try to change the firmware:

```

[4296111.818000] acx: firmware 'Rev 2.3.1.31' does not work well with this driver
[4296111.818000] acx: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 (Radia), EEPROM version 0x05, uploaded firmware 'Rev 2.3.1.31' (0x03010101)
[4296111.818000] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 19 and Linux 2.6.15-17-386

```

---

### Post by tirant on 2006-03-07
OK, GOT IT WORKING! :)

As I thought, all i had to do is upload the correct firmware :-)

All you have to do is make a symbolic link for the correct firmware, and rename the old one:

/lib/firmware/2.6.15-17-386/acx/default


```

lrwxrwxrwx  1 root root   19 2006-03-07 23:16 tiacx100 -> ../1.9.8.b/tiacx100
lrwxrwxrwx  1 root root   22 2006-03-07 23:16 tiacx100r0D -> ../1.9.8.b/tiacx100r0D
lrwxrwxrwx  1 root root   22 2006-03-07 23:16 tiacx100r11 -> ../1.9.8.b/tiacx100r11
lrwxrwxrwx  1 root root   22 2006-03-07 23:16 tiacx100r15 -> ../1.9.8.b/tiacx100r15
lrwxrwxrwx  1 root root   20 2006-03-07 23:16 tiacx100usb -> ../1.0.9/tiacx100usb
lrwxrwxrwx  1 root root   23 2006-03-08 00:25 tiacx111c16 -> ../1.2.0.30/tiacx111c16
lrwxrwxrwx  1 root root   23 2006-03-07 23:16 tiacx111c16.old -> ../2.3.1.31/tiacx111c16
lrwxrwxrwx  1 root root   23 2006-03-07 23:16 tiacx111c17 -> ../2.3.1.31/tiacx111c17
lrwxrwxrwx  1 root root   23 2006-03-07 23:16 tiacx111c19 -> ../2.3.1.31/tiacx111c19

```

---

### Post by Roberto Rosselli on 2006-03-16
Hi tirant,
could you give me some more details? where do you download the correct firmware from? is it a standard Ubuntu package?

Thanks in advance.

---

### Post by tirant on 2006-03-25
No, you don't need to download anything. The correct firmware is already there:

Look: you have to make a symbolic link:

tiacx111c16 should be pointing to ../1.2.0.30/tiacx111c16

The old and incorrect tiacx111c16 (now renamed tiacx111c16.old) was pointing to ../2.3.1.31/tiacx111c16

Off course, you need to do it as 'root' or using sudo.

```

lrwxrwxrwx  1 root root   23 2006-03-08 00:25 tiacx111c16 -> ../1.2.0.30/tiacx111c16
lrwxrwxrwx  1 root root   23 2006-03-07 23:16 tiacx111c16.old -> ../2.3.1.31/tiacx111c16

```

---

### Post by lazerdave on 2006-03-25
This seems very promising.  What's the actual code to make that link?

Please forgive me, I'm still trying to learn.  

Many thanks in advance!

---

### Post by fuxoft on 2006-03-25
[QUOTE=lazerdave]This seems very promising.  What's the actual code to make that link?

Please forgive me, I'm still trying to learn.  

Many thanks in advance![/QUOTE]

Just do this:

```
cd /lib/firmware/2.6.15-19-386/acx/
sudo mv tiacx111c16 tiacx111c16.old
sudo ln -s ../1.2.0.30/tiacx111c16 tiacx111c16
sudo rmmod acx
sudo modprobe acx

```

If there is no "2.6.15-19-386" directory, just use the highest number there is

---

### Post by tirant on 2006-03-26
[QUOTE=fuxoft]
If there is no "2.6.15-19-386" directory, just use the highest number there is[/QUOTE]

Better use:

$ uname -r

That will tell you what kernel version are you using, and the one you need to correct.

---

### Post by Roberto Rosselli on 2006-03-31
tirant, many thanks for your tips, I'll try as soon as I'm back at home :)

Ciao

---

### Post by tirant on 2006-04-03
BTW, there'res a bug filled

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34068](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34068)

---

### Post by superchar42 on 2006-04-03
[QUOTE=fuxoft]```
cd /lib/firmware/2.6.15-19-386/acx/
sudo mv tiacx111c16 tiacx111c16.old
sudo ln -s ../1.2.0.30/tiacx111c16 tiacx111c16
sudo rmmod acx
sudo modprobe acx

```
[/QUOTE]
Should I create the directory if it doesn't exist? ...
sorry, it was /lib/hotplug/firmware for me. Maybe for others, as well.

---

### Post by ckempo on 2006-04-06
The people saying this is working.... does that mean WPA support? It doesn't seem to for me, unless I'm doing something wrong.

---

### Post by neu on 2006-04-16
My Linksys WPC54G v2 works with this fix as well.

---

### Post by durableapostle on 2006-06-05
Ditto.  My WPC54G v2 works with this fix as well.  Good stuff! =D>

---

### Post by ckempo on 2006-06-05
OK, so am I the only person who doesn't have functioning WPA then? Or are all the people saying it works referring to WEP and open networks?

---

### Post by Billhead on 2006-06-06
No, I can't get WPA working (yet) either.

---

### Post by ronche on 2006-06-08
Hello, i'm brand-new to ubuntu and can't get my WPC54G v2 working.  Some have written that this fix works for this card, but I get the following error: "cannot stat 'tiacx111c16': No such file or directory" Any ideas?  Thanks for any help.

---

### Post by Billhead on 2006-06-08
In a terminal window, run uname -r, which will tell you which kernel you are using, then do the following
```

cd /lib/firmware/<kernel>/acx/default/
sudo mv tiacx111c16 tiacx111c16.old
sudo ln -s ../1.2.0.30/tiacx111c16 tiacx111c16
sudo rmmod acx
sudo modprobe acx

```
Replace <kernel> with what gets outputted when you run uname -r.

---

### Post by underpressure116 on 2006-07-03
I'm having the same problem with my Linksys WPC54G.  I followed those instructions exactly and when I try to mv the file to tiacxlllc16.old it says "mv: cannot stat 'tiacxlllc16': No such file or directory."  Did i screw something up?

PS:Sorry for the bump. :D

EDIT:REALLY sorry.  Realized those aren't lower-case "L"s but they're ones.  Really sorry about the bump, I'm just really stressing out.  Thanks.

UPDATE:Well, I did all of this and now when I try to open wlassistant it says, "No usable wireless devices found.  Wireless Assistant will now quit."  And when I run iwconfig, wlan0 (what my wireless card was) doesn't show up anymore.  It also doesn't show up in Network Settings.  Does anyone know what I screwed up?

---

### Post by Billhead on 2006-07-04
Are you sure you ran all of the commands?
Try putting your card in and see what dmesg tells you.

---

### Post by Grellin on 2006-07-04
I am confused. I don't have that directory on my system. I have lib of course but the firmware dont exist. Am I missing something here?

---

### Post by Grellin on 2006-07-04
Never mind. I guess I am using an old version of Ubuntu. Downloading the latest and well see how it goes.

---

### Post by Grellin on 2006-07-04
Ok, updated to 6.06 and used the fix listed above and my WPC54G v2 is working great with WEP. Thanks.

---

### Post by wingl on 2006-09-28
I had the same problem but i found this site: [http://www.linuxextremist.com/?p=4](http://www.linuxextremist.com/?p=4)
It works for my Dapper Drake but i'm not sure about others.

It tells you to type in the terminal:
sudo gedit /etc/modprobe.d/options
Enter your password
Copy and paste this on the bottom:
options acx firmware_ver=1.2.1.34
Save and reboot
Then configure it with System > Administration > Networking

Sorry i'm new to the forums so i don't know how to do those groovy code boxes.

By the way i'm using Xubuntu so i changed it to:
sudo mousepad /etc/modprobe.d/options
If your using Kubuntu, change mousepad to your text editor.

---

### Post by buzo on 2006-10-21
> **fuxoft said:**
> 
```
cd /lib/firmware/2.6.15-19-386/acx/

```


The above line should be:

```
cd /lib/firmware/<your_version>/acx/default

```

where <your_version> is the output of the command "uname -r".

Thanks to Fuxoft for the code snippet.

---

### Post by B0yCk on 2006-11-11
i have a same card (usr 5410)..i installed all kind of drivers from producer site and nothing..after i install the driver and restart..the litle red computer icon that appears says that ''No card found''...and i can't open the Configuration utility ... help me if u know what's the problem...

---

### Post by richardjennings on 2007-02-12
I have just managed to get my USR 5410 pcmcia card working with Ubunto /2.6.17/ kernel.

I am extremely new to Linux, this was my first goal :)

After reading and trying many things, this is what worked for me.

First I installed Ndiswrapper 1.37

Then following the Ndiswrapper instructions in the Install file, I loaded Ndis with a driver set i downloaded from [http://www.linuxant.com/driverloader/ndis_drivers/usr11gv40q.zip](http://www.linuxant.com/driverloader/ndis_drivers/usr11gv40q.zip) 

The driver zip contained usr11g.inf , tiacx111.bin and usr11g.sys files.


After Modprobe Ndiswrapper, i found that although the usr5410 card now had a red led lit, it still did not work. 

After a while i stumbled across a firmware .rpm package. I installed this with sudo aptitude install <file> and my wifi card started working.

This is the firmware package i used: 
Fedora 5 ftp.freshrpms.net/pub/freshrpms/fedora/linux/5/acx111-firmware/acx111-firmware-1.2.1.34-1.noarch.rpm


I havnt yet tried rebooting since I have got it working, but i get the feeling that I am going to have to type modprobe ndiswrapper every time i reboot to enable the connection. Is there any config file I can add this command to??? P.s appologies for the extreme Newb-Ness ;)

---

### Post by safirr on 2007-03-17
> **Billhead said:**
> In a terminal window, run uname -r, which will tell you which kernel you are using, then do the following
```

cd /lib/firmware/<kernel>/acx/default/
sudo mv tiacx111c16 tiacx111c16.old
sudo ln -s ../1.2.0.30/tiacx111c16 tiacx111c16
sudo rmmod acx
sudo modprobe acx

```
Replace <kernel> with what gets outputted when you run uname -r.

I tried this solution . .  now even the red LED on the card does not lit. On dmesg i get this error messages . .
root@saflap:/lib/firmware/2.6.15-28-386/acx/default# dmesg | tail [17192353.576000] pccard: CardBus card inserted into slot 0
[17192353.576000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[17192353.576000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17192353.576000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[17192353.576000] acx: found ACX111-based wireless network card at 0000:03:00.0, irq:11, phymem1:0x26020000, phymem2:0x26000000, mem1:0xd0b14000, mem1_size:8192, mem2:0xd0b80000, mem2_size:131072
[17192353.592000] acx: firmware image 'acx/default/tiacx111c16' was not provided. Check your hotplug scripts
[17192353.600000] acx: firmware image 'acx/default/tiacx111' was not provided. Check your hotplug scripts
[17192353.600000] acx: reset_dev() FAILED
[17192353.600000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[17192353.616000] acx_pci: probe of 0000:03:00.0 failed with error -5

please help !!!!

---

