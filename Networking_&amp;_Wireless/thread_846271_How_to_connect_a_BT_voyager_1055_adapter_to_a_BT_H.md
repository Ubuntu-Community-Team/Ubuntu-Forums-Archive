---
title: "How to connect a BT voyager 1055 adapter to a BT Home Hub"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by nathanmarck on 2008-07-01
Ok hello and welcome to the world of ubuntu and wireless.

You have taken a very deep and painful path.
Luckily i`m here.

Setting up the dongle

```
Step 1 - Dowloaded and installed latest Bt voyager drivers from BT's website on my windows box. Once installed I went into program files/BT VOYAGER/ folder and copied all over to my ubuntu box, well the driver ones.



Step 2 - Make sure your Voyager 1055 device is connected to your ubuntu box. Installed latest ndiswrapper-1.9 from hardy's repos.





Step -3 - In terminal – type following once you are in folder where you copied the BT voyager files to.

Code:



sudo ndiswrapper -i bcmrndis.inf



don't worry if you get invalid error. just carry on!



Step -4 - Run

Code:



ndiswrapper -l






Step -5 - copy files over

Code:



sudo cp -v  usb8023.sys RNDISMP.sys /etc/ndiswrapper/bcmrndis/


(sometimes not needed)


Step -6 - Run again

Code:



ndiswrapper -l



and then

Code:



sudo modprobe ndiswrapper



Step -7 - create new file -

Code:



sudo gedit /etc/udev/rules.d/99-custom.rules



Step -8 - copy paste the following:

#START**

BUS=="usb",

SYSFS{idProduct}=="0715",

SYSFS{idVendor}=="1690",

RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"

#END**





then save and exit







Unplug your adapter and plug it back. Everything works hopefully for you as well.



```

And now the part i spent most of my time on

Association of the BT Home Hub (connecting)

```

Step 1.Get your Bt Home Hubs 10 digit wep key of the back of it and write it down.

Step 2.Go to your network manager or whatever you want to use (network manager advised)

Step 3.Select your BT Home Hub
it will be called BTHomeHub-xxxx
xxxx being a 4 digit id code not realy important just part of the ssid so you know witch one is yours

Step 4. Sellect the security type wich in this case is wep 64/128 bit hex
then in the key text box put in the key wich you wrote down in step 1

```
:guitar:
Congratulations you now have a working connection

If you have any porblems post here

---

### Post by RegUB on 2008-07-09
I've done all the ndiswrapper, modprobe, etc but the network settings only shows the wired (ethernet) connection. Here's a link to a previous posting I made which gives some more details - can you help ?
[http://ubuntuforums.org/showthread.php?t=800188](http://ubuntuforums.org/showthread.php?t=800188)

---

### Post by nathanmarck on 2008-07-10
> **RegUB said:**
> I've done all the ndiswrapper, modprobe, etc but the network settings only shows the wired (ethernet) connection. Here's a link to a previous posting I made which gives some more details - can you help ?
[http://ubuntuforums.org/showthread.php?t=800188](http://ubuntuforums.org/showthread.php?t=800188)
I have looked at your post and everything seems fine exept the device it not connecting to the PC propperly.
Try unpluging it the plugin it back in

---

### Post by geezerone on 2008-07-27
I have successfully and relatively painfully installed the BT Voyager 1055 in Gutsy.

BT Voyager 1055 [_**.inf windows driver**_]("http://cid-3cb347fa8fced718.skydrive.live.com/self.aspx/BT%20Voyager%201055%20inf%20driver%20for%20linux/bcmrndis.inf") for linux use with ndiswrapper.

Install *ndisgtk* from Synaptic package manager. This will install ndiswrapper and front-end GUI which can be found: *System > Administration > Windows Wireless Drivers*.

Browse to the downloaded .inf file and click *install*. Plug in the device and reboot.

You will need to add the wireless key (I am using WPA2 with DHCP) and then should work.

HTH :)

---

### Post by RegUB on 2008-07-29
Still no joy I'm afraid. I've already installed that version of bcnrmdis manually. ndisgtk confirms this - it also says "Hardware present : Yes" but when I go into Network Settings it still doesn't show any wireless connection.

---

### Post by geezerone on 2008-07-30
I know this is a bit of a nightmare to get working and didn't work for long unfortunately??? Moved to Hardy Heron after this and no joy. I have googled and the device uses the Broadcom 4320 chipset. 


Edit: see below

---

### Post by geezerone on 2008-07-30
Ok, well I am currently working on the BT Voyager 1055 USB wireless adapter on Hardy Heron and did it the following way.

Firstly, go to **[THIS]("http://linuxwireless.org/en/users/Download#Buildingandinstalling") **link and download the latest dated tarball ([http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/))

I have stored the compat-wireless driver file which worked for me [[COLOR=Purple]**_HERE_**[/COLOR]]("http://cid-3cb347fa8fced718.skydrive.live.com/self.aspx/compat-wireless-2008-07-30.tar.bz2"). (using kernel 2.6.24-16)

Then follow the instructions which are (copied from the site) and type what is in bold and red to help:

**Extract**: 
Extract the contents of the package: 

**[COLOR=Red]tar jxvf compat-wireless-$[/COLOR]***(date -I)***[COLOR=Red].tar.bz2  [COLOR=Black](use tab key to help complete the line automatically)[/COLOR][/COLOR]**[B]

Build[/B]: 
Build the latest Linux wireless subsystem: 

[B][COLOR=Red]cd compat-wireless-$(date -I)

make[/COLOR][/B][B]

Install[/B]: 
We use the updates/ directory so your distribution's drivers are left intact. 

[COLOR=Red]**sudo make install**[/COLOR][B]

(Uninstall[/B]: 
This nukes our changes to updates/ so you can go back to using your distribution's supported drivers.   sudo make uninstall)


**Unload**: 
Since you might be replacing your old mac80211 drivers you should first try to unload all existing mac80211 and related drivers. Note also that broadcom, zydas, and atheros devices have old legacy drivers which you need to be sure are removed first. We provide a mechanism to unload all old and legacy drivers first so you should run to be sure: 

[B][COLOR=Red]sudo make unload

[/COLOR][/B]**Load**: 
If you know what module you need you can simply load the module using modprobe. If you simply are not sure you can use: 

[COLOR=Red]**sudo make load**[/COLOR]

Note that this will run *make unload* first, just in case you forgot. This unloads your old wireless subsystem drivers and loads the new shiny ones. For example if [ipw3945]("http://linuxwireless.org/en/users/Drivers/ipw3945") and its proprietary daemon are found it'll be stopped and the module unloaded and then [iwl3945]("http://linuxwireless.org/en/users/Drivers/iwl3945") will be loaded. If you are simply upgrading a [mac80211]("http://linuxwireless.org/en/developers/Documentation/mac80211") driver this will unload the old one and the old [mac80211]("http://linuxwireless.org/en/developers/Documentation/mac80211") drivers and load the new ones. 


_This worked without a reboot and hopefully will work for others too._

Good luck!

---

### Post by RegUB on 2008-08-03
This failed at the first hurdle - when I ran the first 'make' command I got the message -

config.mk:30: *** "ERROR: There is a bug with compat-wireless on 2.6.22. Remove me if you want to fix me". Stop.

The README file says this is for 2.6.22 and above, though the config.mk seems to expect 2.6.23 or above. uname -r gives my kernel version as 2.6.22-14-generic. 

I'm not sure what to do here - is it suggesting I just delete that condition from config.mk and run the make again?

Incidentally, config.mk is using the "kernelversion" command, which doesn't exist on my installation. I presume this would cause the above message even if I was on 2.6.23. I googled "kernelversion" and found the below script, but this only outputs "2.6" which would also fail the test in config.mk. Is the below the correct version of "kernelversion" - if not where do I get it from?

pick1() {
    eval 'echo $'"$pick_index"
}
pick() {
    OLD_IFS=IFS
    local delimiter="$1"
    shift
    pick_index="$1"
    shift
    IFS=" "$delimiter
    pick1 $*
    IFS=$OLD_IFS
    unset pick_index
}

version=$(uname -r)
echo `pick . 1 $version`.`pick . 2 $version`

---

### Post by geezerone on 2008-08-03
I used 2.6.24-16 kernel. Would you be in a postion to try and update your kernel? You could try one of the older packages from earlier in the year but I haven't tested to see if these work and maybe a way forward if you don't want to upgrade the kernel.

---

### Post by RegUB on 2008-09-03
Been away so only just picked this up again. I've upgraded my kernel to 2.6.24-16 and the make now runs OK - however when I get to the final 'make load' step it hangs on a 'modprobe at76_usb' command. I can't even kill this command as root. Output below

Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
Loading usb8xxx...
Loading p54pci...
Loading p54usb...
Loading adm8211...
Loading zd1211rw...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwl4965...
Loading rtl8180...
Loading rtl8187...
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2x00pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt2400pci (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2400pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rt2500pci...
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2x00pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt2500pci (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2500pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rt61pci...
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2x00pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt61pci (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt61pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rt2500usb...
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00usb (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2x00usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt2500usb (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2500usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rt73usb...
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00usb (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2x00usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt73usb (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt73usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rndis_wlan...
./scripts/load.sh: line 13: 24680 Segmentation fault      modprobe $i
Loading at76_usb...


This is where it hangs. Any further advice?

---

### Post by RegUB on 2008-09-17
Well, despite the error reported in my last post, I now have a working wireless connection! I didn't bother checking after the apparent failure, but tonight realised that a wlan0 interface is now present! - so the correct component must have been loaded before the failure. All I had to do was configure the connection with the SSID & IP address and all works fine.
Thanks for the help.

---

### Post by geezerone on 2008-09-18
Glad to have helped someone with this nightmare of a device! :)

All the best!

---

### Post by dbarnard on 2008-09-28
> **geezerone said:**
> Ok, well I am currently working on the BT Voyager 1055 USB wireless adapter on Hardy Heron and did it the following way.

Firstly, go to **[THIS]("http://linuxwireless.org/en/users/Download#Buildingandinstalling") **link and download the latest dated tarball ([http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/))

I have stored the compat-wireless driver file which worked for me [[COLOR=Purple]**_HERE_**[/COLOR]]("http://cid-3cb347fa8fced718.skydrive.live.com/self.aspx/compat-wireless-2008-07-30.tar.bz2"). (using kernel 2.6.24-16)

Then follow the instructions which are (copied from the site) and type what is in bold and red to help:

**Extract**: 
Extract the contents of the package: 

**[COLOR=Red]tar jxvf compat-wireless-$[/COLOR]***(date -I)***[COLOR=Red].tar.bz2  [COLOR=Black](use tab key to help complete the line automatically)[/COLOR][/COLOR]**[B]

Build[/B]: 
Build the latest Linux wireless subsystem: 

[B][COLOR=Red]cd compat-wireless-$(date -I)

make[/COLOR][/B][B]

Install[/B]: 
We use the updates/ directory so your distribution's drivers are left intact. 

[COLOR=Red]**sudo make install**[/COLOR][B]

(Uninstall[/B]: 
This nukes our changes to updates/ so you can go back to using your distribution's supported drivers.   sudo make uninstall)


**Unload**: 
Since you might be replacing your old mac80211 drivers you should first try to unload all existing mac80211 and related drivers. Note also that broadcom, zydas, and atheros devices have old legacy drivers which you need to be sure are removed first. We provide a mechanism to unload all old and legacy drivers first so you should run to be sure: 

[B][COLOR=Red]sudo make unload

[/COLOR][/B]**Load**: 
If you know what module you need you can simply load the module using modprobe. If you simply are not sure you can use: 

[COLOR=Red]**sudo make load**[/COLOR]

Note that this will run *make unload* first, just in case you forgot. This unloads your old wireless subsystem drivers and loads the new shiny ones. For example if [ipw3945]("http://linuxwireless.org/en/users/Drivers/ipw3945") and its proprietary daemon are found it'll be stopped and the module unloaded and then [iwl3945]("http://linuxwireless.org/en/users/Drivers/iwl3945") will be loaded. If you are simply upgrading a [mac80211]("http://linuxwireless.org/en/developers/Documentation/mac80211") driver this will unload the old one and the old [mac80211]("http://linuxwireless.org/en/developers/Documentation/mac80211") drivers and load the new ones. 


_This worked without a reboot and hopefully will work for others too._

Good luck!
Thank you - this worked a treat. HOWEVER, when I rebooted my machine, it didnt re load - sorry - I'm very new to Linux. What do I need to do to make it load on start-up?

Ta. D

---

### Post by geezerone on 2008-09-28
Did you get it to work before rebooting? What is seen from network manager (do you see wireless networks)

Try typing: ```
sudo /etc/init.d/networking restart
``` at a terminal and see if this works.

---

### Post by coubury on 2008-10-07
BT Voyager 1055
I followed this quide

Quote:
Step 1

Using the file manager in Ubuntu I mounted my windows xp drive and navigated to the above folder. Select the relevant driver files (for the BT Voyager 1055 they are usb8023.sys, RNDISMP.sys and bcmrndis.inf) and copy them to the Ubuntu desktop.

Step 2

Install the latest version of ndiswrapper. I used the Synaptics package manager, searched the cd for packages and selected ndisgtk which also installed the other two ndiswrapper files however you can use the command line – sudo apt-get install ndisgtk

Step 3

In Terminal type “cd Desktop” which will move you to the desktop directory and type

sudo ndiswrapper –i bcmrndis.inf (you will be asked for your user password and you should get an error message which states it will create the file anyway – just ignore and carry on with next steps).

This will copy the bcmrndis.inf to the ndiswrapper folder.

Step 4

Type:

sudo cp –v usb8023.sys RNDISMP.sys /etc/ndiswrapper/bcmrndis/

This will copy the sys files to the ndiswrapper folder.

Extra step if you are using this guide to install a different wireless adaptor otherwise skip to next step:

Type:

lsusb //Note: Is lowercase L

This will bring up a list of all the attached devices for your usb ports. Locate you wireless device in the list and you will see a set of numbers next to it – for BT it was 1690:0715. Make a note of these two numbers.

Step 5

You must now create the hardware configuration file by typing:

sudo gedit /etc/udev/rules.d/99-custom.rules

This will open the text editor for GNOME (KDE users replace gedit with kate) with a blank page. Copy the attached text and save and exit the text editor.

#START**
BUS=="usb",
SYSFS{idProduct}=="0715",
SYSFS{idVendor}=="1690",
RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
#END**

Please note the single and double quotes on the RUN line which need to be included or your configuration file will not work. If you are installing a different adapter you will need to substitute the two SYSFS numbers above with the ones for your card (see extra step above). After running lsusb BT Voyager shows as 1690:0715 with the first 4 numbers being the idVendor and the second set being the id Product

Step 6

Check the installation by typing:

sudo ndiswrapper –l //Note: Is lowercase L

You should see a message stating Driver: installed and Device: present. This means you have successfully setup the wireless adaptor (if you don't see Device: present unplug your adapter, plug back in and run the above command).

Type:

sudo depmod –a
sudo modprobe ndiswrapper

On the top toolbar, at the right hand side (near the date and time), there will be a icon of a terminal. Left click here and you should see the wireless networks in your area. Click on the network you wish to associate to. If you have security setup up on your router you should be presented with a window to enter your security key.

I had some difficulty with this as I could not connect to my router when security was enabled (even though the router and wireless dongle both support all the current encryption methods) so I had to disable my security through the router and change the mac address table so that only my adapter's mac address can connect to the router. I know this is not the safest of options as mac address spoofing is quite simple to do but it will do for now until I get chance to conduct further tests on the security.

In order to connect to your network each time you boot type:

sudo gedit /etc/modules

And add ndiswrapper to the list that appears in the editor, save and close.

Everything seemed to go ok

when i type sudo ndiswrapper –l

It says my driver is installed

But when i plug my by voyager adapter in nothing comes up. Ubuntu doesn't recognise it.

when i goto the toolbar near the clock and try and look for wirless connection it only shows an option for my wired connection.

---

### Post by geezerone on 2008-10-11
I never found ndiswrapper to work well with this device. Have you tried the solution I posted?

---

### Post by alanqqqq on 2008-11-13
As a Ubuntu novice I have been struggling for a while to get wireless to work. I tried the ndiswrapper method under both 8.04 and 8.10 unsuccessfully. Yesterday I tried the method suggested by geezerone but still without success. Then I read a suggestion that wicd should also be installed. I installed that and success!!! I now have working WPA2 between a BT Voyager 1055 wireless adapter and BT Voyager 2110 router.

---

### Post by geezerone on 2008-11-13
Glad you got it sorted. 

The driver is the problem and the **[Compat Wireless link]("http://linuxwireless.org/en/users/Download#Buildingandinstalling")** will show how to do that. 

WICD or NetworkManager should both work but sometimes one or other (or both!) don't work. I have manually configured my network configuration and edited the */etc/rc.local* file to restart network interfaces on boot-up.

---

### Post by Scott O'Nanski on 2008-11-27
I've got the Linux Wireless drivers working, and the wireless network is present, but I every time I reboot I have to;

```
sudo make load
```

Anyway of circumventing this?

---

### Post by geezerone on 2008-11-27
Did you follow my instructions above and esp ```
sudo make unload
``` as you still have the old (non-working) drivers installed and this is taking precedence over the working ones?

---

### Post by Scott O'Nanski on 2008-11-28
> **geezerone said:**
> Did you follow my instructions above and esp ```
sudo make unload
``` as you still have the old (non-working) drivers installed and this is taking precedence over the working ones?

Ah, I was too sure what was being communicated with "unload"... I'll give it a another shot, and report back.

Thanks for your help.

---

