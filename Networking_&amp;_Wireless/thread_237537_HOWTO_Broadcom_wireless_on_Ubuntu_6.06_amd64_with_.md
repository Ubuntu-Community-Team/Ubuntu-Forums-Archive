---
title: "HOWTO: Broadcom wireless on Ubuntu 6.06 amd64 with wpa_supplicant (Acer Aspire 5021)"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by finite9 on 2006-08-16
Hi!

This is primarily written for:

Ubuntu 6.06 amd64
native Linux bcm43xx driver included in kernel 2.6.15-25
Acer Aspire 5021WLMi laptop using Broadcom 54g adapter
WPA networks

But with little modifications it shouldn't matter that it's for an Acer laptop and i'm not really sure if the architecture makes any difference whatsoever.  I apologise if's a little rough around the edges, i'm new to Linux and it's taken me many months of forum trawling to get this working, and I just added to my guide as I went along--most of the threads on the forums deal with only GUI apps or ndiswrapper solution or WEP connectivity, but I never found a guide for native driver with WPA.  Hope someone finds it useful!

This guide is written to be able to get wireless networking running in the core of the Linux system, i.e. with /etc/init.d/networking.  It is not written for NetworkManager, WiFiRadar or any other GUI tools, as they all seem to have 'issues' of one kind or another (nm-applet completely breaks the function of /etc/init.d/networking and uses it's own code to get everything working which is not very good if other things rely on /etc/init.d/networking).  The guide is aimed at home users who have one network and never need to connect to other networks...I do n ot have scripts that can handle roaming, but these can be found in other threads/wiki.  It's easy to change netwoks using Terminal if you only do it every once in a while, but this guide would not be suitable as it stands for people who roam a lot.

No doubt the GUI apps will improve over time, but until they become the defacto, it's best to stick with basic networking.

Use in-built Dapper Drake bcm43xx driver with bcm43xx-fwcutter and the freely available wl_apsta.o driver from the bcm43xx team.  This is  limited to 36Mbit rates as of kernel revision 2.6.15-25. See the Ubuntu wiki for Broadcom driver.  This method is preffered over ndiswrapper, and is probably going to be developed very rapidly over the next few months.

To be able to use the in-built broadcom driver in Dapper with reverse engineered Windows driver:

[http://drinus.net/airport/wl_apsta.o](http://drinus.net/airport/wl_apsta.o)

-- howto broadcom driver supplied with Dapper:

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom)

blacklist ndiswrapper even if ndiswrapper-utils is not installed.

echo 'blacklist ndiswrapper' | sudo tee -a /etc/modprobe.d/blacklist

Install the wpa_supplicant and firmware cutter (need universe repository)

sudo apt-get install wpasupplicant bcm43xx-fwcutter

run firmware cutter with driver file

sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` ~/Desktop/wl_apsta.o

install acer_acpi ([http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html](http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html) ) with tarball from home directory

make
sudo make install
depmod -a			#checks kernel module dependencies
modprobe acer_acpi	#but we will do this with a script

clean up /etc/network/interfaces so that only eth0/eth1 are enabled

Add pre-up and post-down scripts (call them something appropriate) (customised to modprobe things and echo enabled to acer_acpi file)

pre-up script (place in /etc/network):

modprobe bcm43xx
modprobe acer_acpi
chmod 777 /proc/acpi/acer/wireless
echo “enabled: 1” > /proc/acpi/acer/wireless
iwconfig eth1 ap any
iwconfig eth1 rate 36M

post-down script:

echo “enabled: 0” > /proc/acpi/acer/wireless
modprobe -r acer_acpi
modprobe -r bcm43xx

These 2 files should be 754 permissions owned as root:root.

Now to setup wpa_supplicant...

#add config to /etc/wpa_supplicant.conf using...
#this will add a hashed version of the passphrase to the config #file
wpa_passphrase <NetworkESSID> <text_passphrase> | sudo tee -a /etc/wpa_supplicant.conf

Note that you need to remove the non-hashed, commented-out pasphrase as that is auto-generated above the hashed passphrase.

Add the following options to the .conf file and comment them out...

#used if AP uses a hidden SSID
scan_ssid=1

proto=WPA
key_mgmt=WPA-PSK
Pairwise=TKIP

Now enable wpa_supplicant to start automatically (not 100% sure if this is needed as I can set it to ENABLED=0 and it still works, and besides this, the line that starts wpa here is duplicated in interfaces as a pre-up)...

sudo gedit /etc/default/wpasupplicant

Add the following and save the file:
ENABLED=1
OPTIONS="-ieth1 -c/etc/wpa_supplicant.conf -Dwext -w"

This ensures that when /etc/network/interfaces is started on boot, calling eth1 will automatically send a call to wpa_supplicant, and the -w switch will wait until wpa_supplicant has finished before starting the eth1 interface.

Edit /etc/network/interfaces so that eth1 looks like this:

auto eth1
iface eth1 inet dhcp
pre-up /etc/network/wireless-up
#pre-up sleep 3  # not sure if needed
pre-up wpa_supplicant -Bw -ieth1 -c/etc/wpa_supplicant.conf -Dwext -w
#pre-up sleep 5  # not sure if needed
post-down killall -q wpa_supplicant
post-down /etc/network/wireless-down

wext is used as the driver because it is native wireless extensions in the linux kernel and -Bw puts process in the background.

restart interface or networking—this will now enable scanning and connecting to WEP/WPA and unencrypted Aps.

Sudo /etc/init.d/networking restart

Now you can test the interface:

iwlist eth1 scan

To connect to an unencrypted AP:

sudo iwconfig eth1 essid '<ESSID name>'
sudo dhclient eth1

END.

---

### Post by cemptor on 2006-08-17
Does this work with the BCM4318 Rev 02 chipset? on 64 bit Linux?

---

### Post by finomeno on 2006-08-17
Thanks a lot! =D>  Worked for my Asus A6K too (I skipped the Acer ACPI part though ;) ).

---

### Post by finite9 on 2006-08-18
> **cemptor said:**
> Does this work with the BCM4318 Rev 02 chipset? on 64 bit Linux?

Hi Cemptor!

Yeah, there have been some posts I've read that the bcm43xx driver doesn't work with rev 02 chipset from Broadcom, but the first I heard about it was 2 days ago, and I do not know which revision I have, but I definitely have a Broadcom 4318 AirForceOne 54g adapter, and my Acer Aspire 5021WLMi is less than 1 year old, so you would have thought the adapter was quite recent, but I honestly don't know!  The only thing I can recommend is to try it and see if it works!

One other thing regarding the acer_acpi...this is used to 'turn on' the wireless adapter as it is turned off by default in the BIOS (cannot be changed) and the Windows driver has the ability to turn it on.  Obviously, if you don't have an Acer laptop, you can skip this step, but if you have another laptop with Broadcom, then it may require a similar hack to turn on the adapter.  I was unable to scan for APs using iwlist eth1 scan until I had installed acer_acpi.  It gave the error: No scan results.

---

### Post by cemptor on 2006-09-10
Thanks for the help!

I'm trying to do this on a desktop, and managed to detect the card. After extracting the firmware, the Gnome networking GUI allows me to activate the card. Edited the wpa_supplicant as you said, and /etc/network/interfaces too. Can attach the right essid too, and scanning shows up my router.

The only thing that doesn't happen is getting connected.

I wonder if I need to do something similar to what you did for your laptop.

Any ideas?

I have the Broadcom 4318 (rev 02) chipset on my US Robotics 5417 PCI desktop adapter.

---

### Post by sidefx on 2006-09-15
> **finite9 said:**
> 

[http://drinus.net/airport/wl_apsta.o](http://drinus.net/airport/wl_apsta.o)



This timesout for me at the moment, anybody have another source for this?

---

