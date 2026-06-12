---
title: "wireless..."
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by naiya on 2006-11-03
basic info:
dell c610
new ubuntu user - breezy badger version.
i'm trying to install linksys wireless adapter wpc54gs. installing the driver is the issue.
i've tried everything i could find on the subject including: [http://www.kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php](http://www.kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php)
and i keep getting the same result: that it's an invalid driver. i've been working on this for a number of hours and i'm not finding any answers. it seems like everyone else is doing fine with those instructions but me. i wonder what's missing in the equation?

anyone got a fix? (in laywoman's terms, please)
](*,) 
naiya

---

### Post by naiya on 2006-11-03
sudo ndiswrapper -i 2802W.inf
cp: cannot stat '2802W.inf' : No such file or directory

but this file is on my desktop. it's the XP driver for the wireless adapter.... ?

---

### Post by squibT on 2006-11-03
sudo ndiswrapper -i ~/Desktop/Driver_Folder_if_it_is_in_one/2802W.inf

ndiswrapper -l see if working

---

### Post by naiya on 2006-11-03
okay i did that.
i got:

'2802W is already installed use -e to remove it'

then i typed: sudo ndiswrapper -l
'Installed ndis drivers:
2802w   invalid driver!'

---

### Post by squibT on 2006-11-03
Where did you get the drivers for your card...I have the same card and use the latest drivers from Linksys...

I may be wrong but I think you need to use LSBCMNDS (lateset) or bcmwl5...depending on the version number of your card...

Try lspci and post the results...

---

### Post by naiya on 2006-11-03
> **squibT said:**
> Where did you get the drivers for your card...I have the same card and use the latest drivers from Linksys...

I may be wrong but I think you need to use LSBCMNDS (lateset) or bcmwl5...depending on the version number of your card...

Try lspci and post the results...


The driver above was download from linksys website (the first version) i tried LSBCMNDS first - it's on the CD - to no avail either. I did not yet try the other one you mentioned 'bcmw15'... not sure where to find it.

lspci results:

0000:00:00.0 Host bridge: Intel Corp. 82830 830 Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82830 830 Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:02:01.0 CardBus bridge: Texas Instruments PCI1420
0000:02:01.1 CardBus bridge: Texas Instruments PCI1420
0000:07:00.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)

---

### Post by squibT on 2006-11-03
I am not familiar with the 2802W.inf driver for the wpc54gs PCMCIA wireless card...

At Linksys there are 3 downloads for this card:

WPC54GS V1, V1.1, V2 they are all speedbooster cards which is what you initially said you have. None of these downloads have the 2802w.inf driver...AFAIK.

Can you tell me if this wireless card is in fact a credit card type unit that slides into the side of your laptop? 

Can you look on the back of the card and see if it is named WPC54GS and is a Linksys card? Make sure it says GS at the end. See if there is a version number at the end of the name also...on back.

Download the drivers again from Linksys....on your desktop they should be named wpc54gs_driver_VersionNumberWhatever...get Version 2 if you don't know which to get.

You will open the Drivers folder...and copy the NT folder to your desktop.

Remove the old driver....

ndiswrapper -l <see drivers installed>

sudo ndiswrapper -e 2802W <remove the driver installed>

Reboot with card installed ...not absolutely necessary but Windows has a hold on me....

Installaton:
sudo ndiswrapper -i /location_of_your_wireless_driver/your_driver.inf
sudo ndiswrapper -l

(You should see: 

Your@laptop:~$ ndiswrapper -l
Installed drivers:
lsbcmnds                driver installed, hardware present )


Loading the new driver module:

        sudo depmod -a

        sudo modprobe ndiswrapper
        

Check for error messages:

        sudo tail /var/log/messages

Set ndiswrapper to load on startup 
	sudo ndiswrapper -m

Add module to list at end of file:
	gksudo gedit /etc/modules
				* Add the following module name to the list at end .... ndiswrapper

As a last step to get it going be sure to 'blacklist bcm43xx'
edit:

sudo /etc/modprobe.d/blacklist and add "blacklist bcm43xx" to the bottom without quotes.

Reboot....if you wish...

sudo /etc/init.d/networking restart 

after you log in if you don't have Internet access...but that is another configuration story...

---

### Post by naiya on 2006-11-04
By the way - thank you for help here... i'm most grateful.

> **squibT said:**
> 

Can you tell me if this wireless card is in fact a credit card type unit that slides into the side of your laptop? 

... see if it is named WPC54GS and is a Linksys card? Make sure it says GS at the end. 

Yes to all. it indeed says V2.

> **squibT said:**
> 
Download the drivers again from Linksys....on your desktop they should be named wpc54gs_driver_VersionNumberWhatever...

You will open the Drivers folder...and copy the NT folder to your desktop.

Remove the old driver....


done. all good. nothing installed. clean slate.

> **squibT said:**
> 
Reboot with card installed ...not absolutely necessary but Windows has a hold on me.... 

yeah. better to cross all the i's...

> **squibT said:**
> 
Installaton:
sudo ndiswrapper -i /location_of_your_wireless_driver/your_driver.inf
sudo ndiswrapper -l

(You should see: 

Your@laptop:~$ ndiswrapper -l
Installed drivers:
lsbcmnds                driver installed, hardware present )


nope. dang. same thing.

naiya@ubuntu-naiya:~$ sudo ndiswrapper -l
No drivers installed
naiya@ubuntu-naiya:~$ sudo ndiswrapper -i /Desktop/NT/LSBCMNDS.inf
Installing lsbcmnds
cp: cannot stat `/Desktop/NT/LSBCMNDS.inf': No such file or directory
naiya@ubuntu-naiya:~$ sudo ndiswrapper -l
Installed ndis drivers:
lsbcmnds        invalid driver!
naiya@ubuntu-naiya:~$

<scratches head> 
perhaps another driver is needed?

---

### Post by squibT on 2006-11-04
I have had the same error message on occasion. The driver works fine....really....same card here...

Installing lsbcmnds
cp: cannot stat `/Desktop/NT/LSBCMNDS.inf': No such file or directory shows it cannot find the driver to install it. Try this:

ndiswrapper -e lsbcmnds <again please>

Make sure all ndiswrapper packages are installed...check them all off in Synaptic Package Manager...reload/apply...then...

cd Desktop
cd NT
ls
bcmwl5.sys  LSBCMNDS.cat  LSBCMNDS.inf

sudo ndiswrapper -i LSBCMNDS.inf

ndiswrapper -l

...let me know what happens...;)

---

### Post by naiya on 2006-11-04
hooray!
driver present hardware present sanity present.

---

### Post by naiya on 2006-11-04
> **squibT said:**
> 
Add module to list at end of file:
	gksudo gedit /etc/modules
				* Add the following module name to the list at end .... ndiswrapper


(gedit:7822: GnomeUI-WARNING ** WHile connecting to session manager:
Authentication rejected, reason: None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by squibT on 2006-11-04
You are alive!


The error message when you use gksudo is ok as long as it opens the file so you can enter the text and save it...if it wont open try this....

Add module to the list at end of file:

sudo gedit /etc/modules
* Add the following module name to the list at end .... ndiswrapper

Post:

iwconfig

iwlist <eth1, wlan0 or whatever iwconfig says it is> scan

eg...iwlist wlan0 scan

---

### Post by naiya on 2006-11-04
that worked - i can't send the results yet due to an issue with a removeable drive i've been using to do that with.... but the blacklist thing - that's not seeming to work exactly.

---

### Post by naiya on 2006-11-04
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"belkin54g"
          Mode:Managed  Frequency:xxxxxxx
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-66 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

naiya@ubuntu-naiya:~$ iwlist wlano scan
wlano     Interface doesn't support scanning.

naiya@ubuntu-naiya:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: xxxxxxxx
                    ESSID:"belkin54g"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:xxxxxxx
                    Quality:0/100  Signal level:-83 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
          Cell 02 - Address: xxxxxxx
                    ESSID:xxxxxxx
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-88 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: xxxxxxx
                    ESSID:"belkin54g"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-60 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

### Post by squibT on 2006-11-04
Excellent...you are connected at your max speed 54 M as opposed to other configs connecting at 11 M....

Now would you like to connect to the Internet? Or have you got that all figured out already?

:D

---

### Post by naiya on 2006-11-04
> **squibT said:**
> Excellent...you are connected at your max speed 54 M as opposed to other configs connecting at 11 M....

Now would you like to connect to the Internet? Or have you got that all figured out already?

:D

lol, i'm connected! - sending this reply from my new beast. sweet!
MUCH GRATITUDE.

---

### Post by squibT on 2006-11-04
Enjoy....!!!!!!!!!!!!

Please don't use up all of the Internet....leave some for someone else...

Later,,,

squibt

---

