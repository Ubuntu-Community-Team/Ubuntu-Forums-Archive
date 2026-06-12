---
title: "Upgraded to Edgy, Wireless wont work now"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by littlec on 2006-11-09
Hi,

I just upgraded from Dapper --> Edgy and now I'm unable to use my wireless internet.

I downloaded ndiswrapper manually, and did ndiswrapper -l .  Both hardware and drivers present still. 

I tried doing a sudo modprobe ndiswrapper
gave me fatal error that ndiswrapper.ko was not found (in my /lib kernel directory).  I suspect that's the problem and I need to create a symbolic link but don't know exactly how (ln -s ???).  Is that the problem?  I can't find a ndiswrapper.ko file.

So ndiswrapper is 'installed' i think?  but i don't see any wlan devices or any wireless devices. 

------TOTAL SIDEBAR-----
I tried going back to older kernels and those I think needed me to tweak the xorg.conf to include the nvidia drivers. (just want to focus on getting htings to work now)
So i was curious how linux work or the concept of 'kernels'.  I don't understand why my newer kernel works fine with X, while my older one wants me to point to vid card drivers even though it's loading from the same xorg.conf?

---------end sidebar-----  
Just wanna get internet working, I need it for school.


Any input would be greatly appreciated, thanks.

---

### Post by littlec on 2006-11-09
i know it's early but still bumping. i can't think of anythingggggggg. anybody pleaseeeee?

---

### Post by littlec on 2006-11-09
i did a depmod -a
out of blind hope

now sudo modprobe ndiswrapper 

says: no module present (ndiswrapper) 
something like that. i'm dual booting right now.

getting frustrated. no clue how to get this ndiswrapper.ko i think it's in the modules but i can't find a ndiswrapper modules

or something

anyone have any ideas? thanks

---

### Post by littlec on 2006-11-11
Ok, so I uninstalled ndiswrapper, manually compiled version 1.8.
Ndiswrapper.ko problem now gone
It said I had to reinstall my windows drivers to make it work.


So i reinstalled them, ndiswrapper -l shows the 2 drivers (same that i used before) are both INVALID?!

I took a look and came across i might possibly have ot use load_fw_ar5523  but for older versions of ndiswrapper (pre 1.7). 

My wireless usb card is Dlink DWL-G132 (A2)

What is wrong with my drivers that they are now saying invalid?

---

### Post by flosofl on 2006-11-11
I had to deal with this myself.  The problem is **all 4** ndiswrapper packages needed to be installed.  ](*,)  That's how I finally got it to work.

Uninstall your manually compiled kernel module ([FONT=Courier New]make uninstall[/FONT] should do it)

Install the following packages (I'm assuming i386):

ndiswrapper-common_1.18-1ubuntu2_all
ndiswrapper-utils_1.1-5_all
ndiswrapper-utils-1.1_1.1-5_i386
ndiswrapper-utils-1.8_1.18-1ubuntu2_i386

I'd also recommend:

ndisgtk_0.6-0ubuntu1_all
network-manager_0.6.3-2ubuntu6_i386
network-manager-gnome_0.6.3-2ubuntu6_i386

Hope this helps.

---

### Post by littlec on 2006-11-13
Thanks for the suggestion! will try it out this weekend when I have access to a wired connection.  Less frustrating without having to reboot every 2 minutes.

---

### Post by littlec on 2006-11-18
> **flosofl said:**
> I had to deal with this myself.  The problem is **all 4** ndiswrapper packages needed to be installed.  ](*,)  That's how I finally got it to work.

Uninstall your manually compiled kernel module ([FONT=Courier New]make uninstall[/FONT] should do it)

Install the following packages (I'm assuming i386):

ndiswrapper-common_1.18-1ubuntu2_all
ndiswrapper-utils_1.1-5_all
ndiswrapper-utils-1.1_1.1-5_i386
ndiswrapper-utils-1.8_1.18-1ubuntu2_i386

I'd also recommend:

ndisgtk_0.6-0ubuntu1_all
network-manager_0.6.3-2ubuntu6_i386
network-manager-gnome_0.6.3-2ubuntu6_i386

Hope this helps.

Ok, I now have access to a wired connection so this is a little bit easier.  I gave your suggestion a shot doing a make install them installing those 4 packages.  Still NO LUCk.  
Idont know where it's not working, hardware is detected and present...

This is getting soooooo frustrating, I just want things to work.  Who would've known 'upgrading' to edgy eft would just give me so many headaches.  Any suggestions anybody please please please?  I noticed sound is not working either but that's not even a priority atm.

---

### Post by littlec on 2006-11-22
I still can't get it working.  Uninstalled and re-installed several times.
DWL-G132 USB wireless.

~/Drivers$ ndiswrapper -l
Installed drivers:
athfmwdl                driver installed, hardware present 
neta5agu                driver installed, hardware present 
c@mookalakaikki:~/Drivers$ sudo depmod -a
c@mookalakaikki:~/Drivers$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

---------

My wireless card wont even light up, but it's detected in lsusb and in the ndiswrapper -l

Ideas?

---

### Post by IntuitiveNipple on 2006-11-22
I'm having other issues as a side-effect of trying to get WPA-PSK support for internal mini-PCI WaveLAN/IEEE adapters.

As part of this I read that support for the latest ndiswrapper versions was broken and to make it work you must use the versions in the repository.

To keep it simple I used Synaptics in the Gnome desktop to search for "ndiswrapper" and then let it install it for me, and I've had no problems.

This may not be causing your issue because I don't know what the Ubuntu/ndiswrapper 'bug' is supposed to be.

---

### Post by kalm on 2006-11-23
what kindof card is it? edgy has better hardware support over different wireless cards ( even my rt61 worked (not well still trouble with the connection hangs) out of the box ) so why don't you try installin' maybe some native drivers... 
Ndiswrapper should work if it all works on windows...
what interfaces does ifconfig give you? or ifconfig -a?
NetworkManager is the worst solution i hate it.. go to doing things manually..!

---

### Post by wmatlock on 2006-11-23
I fell your pain. I am building a Digital Video Recorder that I need wireless for and unluckily the wireless PCI card I installed needs ndiswrapper also. So I used my laptop to experiment with as I had another card for it that also required ndiswrapper. I have finally given up on Edgy for a while while I get my thoughts in order. I had it working for a while and then messed it up. I wish I could find that post I used again. I keep seeing messages that Network Manager and ndiswrapper in Edgy is broken and that you need to uninstall and reinstall both from source. I am going to take a break for a few days and then try again.

---

### Post by panty31772 on 2007-01-07
I dont know if this will help any  .. but ... i could not get the drivers to work under dapper .. now that i ugraded to edgy thoguh it all works ( havent tried actually connecting to a wireless network but all signs show the device to work 
i dowloaded the newest drivers form d-link's website , extracted to my home folder  ... used the kmenu/settings/windows wireless driver to install both .... then in terminal set ndiswrapper to use netAAGU as the device driver .... followed the steps in this : How to install Windows Wireless Drivers (Ndiswrapper)

    * Read #General Notes
    * In order to install ndiswrapper you need a copy the windows drivers for your Wireless ethernet device.
    * This is only meant to be installed if your card isn't supported by Ubuntu, check Ubuntu's list of natively supported wireless cards.
    * Check ndiswrapper's list of supported wireless cards if your card isn't supported natively, please visit Ndiswrapper's official supported cards list 

    * Find out if you have acx module loaded. Because acx module interferes with windows driver, we need to remove it if it is found. 

lsmod | grep acx

    * Remove the acx module if found. It could also be acx_pci or similar. Please Note: New kernel updates will auto load the acx module again. So repeat the following two commands every time the kernel is updated. 

sudo rmmod acx
sudo mv /lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/acx /root/

    * Install ndiswrapper and drivers (due to a bug in Edgy, you need to specify ndiswrapper-utils-1.8) 

sudo apt-get install ndiswrapper-utils-1.8
sudo ndiswrapper -i /location_of_your_wireless_driver/your_driver.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper

    * Set ndiswrapper to load on startup 

sudo ndiswrapper -m
gksudo gedit /etc/modules

    * Add the following module to the list 

ndiswrapper

    * Now you can configure your wireless card with ifconfig and iwconfig. 

    e.g. Supposing wlan0 is your wireless device. 

sudo iwconfig wlan0 essid "AP" key ababababababababab mode Managed
iwconfig

    * You sould now be able to see the MAC address of the access point and signal rate. 

[edit]

rebooted with dongle connected . seemed to have worked for me ... hope it helps

---

