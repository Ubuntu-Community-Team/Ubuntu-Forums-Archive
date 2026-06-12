---
title: "Installing the WiFi Driver (for RTL8192SU)"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Tux_2008 on 2010-01-06
[SIZE=1](Ubuntu 9.10 32-bit)[/SIZE]

Hi,

I recently purchased a USB wireless receiver that uses the Realtek RTL8192SU chipset. After searching and not finding a Linux wireless driver I emailed Realtek, and they sent me the correct Linux driver (I've uploaded the .zip [[COLOR=Blue]**HERE**[/COLOR]]("http://sites.google.com/site/solidpace/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091112.p4.zip?attredirects=0")).

I've tried following the (to me somewhat confusing) readme file, but I can't figure out how to install the driver.

Could you please show a complete beginner what I'm supposed to do, as I seem to be too thick-headed to understand how this install is supposed to be done?

All help is greatly appreciated! Thanks!:)

---

### Post by K.J. on 2010-01-06
This doesn't quite answer your question, but a much simpler (although certainly not better) method is to use ndiswrapper (ndisgtk is the GUI) to install the Windows driver. You'll need WINE installed because it comes packaged as an exe. Run the .exe and make note of where the files are extracted to (most likely /home/username/.wine/drive_c/DRIVERS).

You then use ndisgtk to install the .inf file for your adapter.

---

### Post by Methuselah on 2010-01-06
This might help you since it has pictures even a screencast.
[http://amitech.50webs.com/installing/index.php.html#source](http://amitech.50webs.com/installing/index.php.html#source)

---

### Post by themusicalduck on 2010-01-06
Before doing anything with ndiswrapper or any other file. Have you checked under System > Administration > Hardware Drivers for a downloadable driver?

---

### Post by Tux_2008 on 2010-01-06
> **Methuselah said:**
> This might help you since it has pictures even a screencast.
[http://amitech.50webs.com/installing/index.php.html#source](http://amitech.50webs.com/installing/index.php.html#source)
Hi, thanks for the link! Unfortunately, this does not seem to work for me, "./configure" doesn't give any response, and while 'make' and 'make install' do work; it doesn't seem to install the driver (at least it doesn't recognize any wireless networks). Perhaps something must be set-up or configured beforehand manually, as the "./configure" step didn't do anything? The link is very useful though, I'll be keeping it in my bookmarks, thanks!


> **themusicalduck said:**
> Before doing anything with ndiswrapper or any other file. Have you checked under System > Administration > Hardware Drivers for a downloadable driver?
Hi, thanks for the reply, there are drivers for my Nvidia graphics card but not for the wireless.:(


> **K.J. said:**
> This doesn't quite answer your question, but a much simpler (although certainly not better) method is to use ndiswrapper (ndisgtk is the GUI) to install the Windows driver. You'll need WINE installed because it comes packaged as an exe. Run the .exe and make note of where the files are extracted to (most likely /home/username/.wine/drive_c/DRIVERS).

You then use ndisgtk to install the .inf file for your adapter.
Hi, thanks for the tip with ndisgtk and ndiswrapper, the wireless does work this way, but if at all possible I'm attempting to get the native drivers to work primarily, as ndiswrapper/ndisgtk have quite many limitations of usage. But certainly a backup solution, thanks!

---

### Post by Natasha D on 2010-06-06
Ok so the thing is that I'm a complete linux noob! And I need to get my wireless adapter working soon, or I face losing out on internet!
Yeah, so I have no idea where to even begin with the installation process for these drivers! :|
Any help at all would be GREATLY appreciated!

---

### Post by joshruehlig on 2010-06-07
natasha what is your chipset/wireless card model? (example this thread was about rtl8192su)

Do u have the install cd or a manual that came with ur card?

what do u get when u type "lsusb" in the terminal? (menu>accessories>terminal)

---

### Post by anewguy on 2010-06-07
> **Natasha D said:**
> Ok so the thing is that I'm a complete linux noob! And I need to get my wireless adapter working soon, or I face losing out on internet!
Yeah, so I have no idea where to even begin with the installation process for these drivers! :|
Any help at all would be GREATLY appreciated!

Being a complete noob, let's try to get you started.  Please do the following and post the outputs back here:

- open a terminal window -> Applications/Accessories/Terminal

- if your adapter is a USB device, or if your PC is a laptop, type:

lsusb <press enter>  This asks Ubuntu to list (ls) the known USB devices on the system.  

- if your adapter is not USB, or if your PC is a laptop or desktop:

lshw <press enter>  This asks Ubuntu to list (ls) the known hardware devices on the system.  This will create quite a long list, so look for something similar to the following and copy only that section.  Note that yours will look different  mainly look for the "Wireless interface".

```
        *-network:0
             description: Wireless interface
             product: 88w8335 [Libertas] 802.11b/g Wireless
             vendor: Marvell Technology Group Ltd.
             physical id: 7
             bus info: pci@0000:00:07.0
             logical name: wlan0
             version: 03
             serial: 00:1e:2a:46:a8:b4
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ndiswrapper+wg311v3 driverversion=1.55+NETGEAR,12/30/2005,3.2.3.2 ip=10.0.0.3 latency=32 multicast=yes wireless=IEEE 802.11g
             resources: irq:18 memory:cffe0000-cffeffff memory:cffb0000-cffbffff

```

The reason for doing both:

- if using an external USB adapter, or on some laptops where the internal wireless card is connected to internal USB (you won't even know it), the lsusb will give us the information

- the lshw will show what driver, if any, is being used, if the device is "claimed" or not and other features.


Dave ;)

---

### Post by joshruehlig on 2010-06-07
haha i was dumb only suggesting lsusb, i forgot most people arent even using usb. ive been using usb for a few months now with my setup so i forgot

---

### Post by Natasha D on 2010-06-08
> **joshruehlig said:**
> haha i was dumb only suggesting lsusb, i forgot most people arent even using usb. ive been using usb for a few months now with my setup so i forgot

Hey, thanks guys, 
It was a usb device, but it wasn't mine, and it was too frustrating to deal with, so I returned it to its rightful owner..

I do however still need a wireless adapter (preferably a pcmia one) that will work (more or less out of the box) with ubuntu (v. 10.04), so if you have any suggestions, could you please let me know?!

I really like ubuntu so far, and I'm hoping to not have to switch back to windows cuz of internet issues :(..

---

### Post by beew on 2010-06-08
Hi,

I also use a USB network card ( a Netcore wireless card that costs $10 :)). The driver is rtl8187 according to network manager. It works out of the box. But before I got it to work, I have to disable the internal wireless card first else networkmanager would give pirority to the internal card, which is damaged. 

If your computer has an internal card maybe you will need to disable it first. 

Go to terminal and type lshw -c network.
scroll down to *-network  description: wireless interface and see if it is enabled or not.  You can check by looking at the line that starts with "configuration" and see if it is broadcasting or not. If yes, then it will tell you the name of the driver.

To disable it, type:

sudo gedit /etc/modprobe.d/blacklist.conf

when the file backlist.conf comes up, add the line "blacklist <driver name>" without the quotations. <driver name> is the name of the driver you found in lshw -c network. Then save and exit. This would disable the internal card.

---

### Post by Natasha D on 2010-06-08
> **beew said:**
> Hi,

I also use a USB network card ( a Netcore wireless card that costs $10 :)). The driver is rtl8187 according to network manager. It works out of the box. But before I got it to work, I have to disable the internal wireless card first else networkmanager would give pirority to the internal card, which is damaged. 

If your computer has an internal card maybe you will need to disable it first. 

Go to terminal and type lshw -c network.
scroll down to *-network  description: wireless interface and see if it is enabled or not.  You can check by looking at the line that starts with "configuration" and see if it is broadcasting or not. If yes, then it will tell you the name of the driver.

To disable it, type:

sudo gedit /etc/modprobe.d/blacklist.conf

when the file backlist.conf comes up, add the line "blacklist <driver name>" without the quotations. <driver name> is the name of the driver you found in lshw -c network. Then save and exit. This would disable the internal card.

it only says Ethernet interface under network description!

---

### Post by joshruehlig on 2010-06-08
U don't need to disable anything in network manager... Ive had multiple wireless cards on all listed in network manager at the same time all giving me signal. If your computer loads a bad driver then you may have to disable that through blacklisting to enable the right driver for your card.

"it only says Ethernet interface under network description!" Natasha your computer is different then his, you said you took out the usb wifi so you probably have nothing in right now.

So Natasha you are looking for a PCI (or PCI-e?) card that works out of the box with ubuntu 10.04?
Is your computer a laptop that already has u.fl (antenna) lines? How many?
Or are you on a desktop that needs its own antenna?

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
I'm sure we can find you one for cheap on ebay, many wireless cards work out of the box, or with minimal tweaking on ubuntu.

---

### Post by anewguy on 2010-06-08
Expanding on the above, the link will take you to a page where you can click on PCMCIA to see the adapters supported by Linux. If your device is not listed there, this link will take you to the PCMCIA start page for adapters that require ndiswrapper to work.  From there you can click on the various adapters to find their status with Linux.

Dave ;)

---

### Post by anewguy on 2010-06-08
I'd like to recommend you also try the following.  I found it earlier (I think last week) while researching a similar problem for someone else.  Note that even though the numbers don't match don't worry - just try it as-is:

```
Step-by-step, here we go:

- open a terminal window (applications/accessories/terminal)

- type:

sudo mkdir -p /etc/Wireless/RT2860STA/ <press enter>

This creates a new folder called Wireless in the /etc system folder, and creates another folder called RT2860STA within that folder.

-type:

sudo touch /etc/Wireless/RT2860STA/RT2860STA.dat <press enter>

This creates a file called RT2860STA.dat in the newly created folder. Note that the file is empty.


- type:

sudo service network-manager restart <press enter>

This will restart network manager, so it will find the newly created folders and file, and should now show your wireless working. Click on the network manager icon in the upper tray and be sure "Enable Wireless" is checked.

You can now close the terminal window:

- type:

exit <press enter>

```

Dave ;)

---

### Post by Natasha D on 2010-06-09
> **joshruehlig said:**
> 
So Natasha you are looking for a PCI (or PCI-e?) card that works out of the box with ubuntu 10.04?
Is your computer a laptop that already has u.fl (antenna) lines? How many?
Or are you on a desktop that needs its own antenna?

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
I'm sure we can find you one for cheap on ebay, many wireless cards work out of the box, or with minimal tweaking on ubuntu.

Thanks for the link, I'll look into it..
My computer is a laptop, it's a Sony Vaio VGNS46GP... I'm not sure about the antenna thing :S (I feel like a complete computer n00b right about now :( )

---

### Post by RyuzakiTenseiga on 2010-07-04
I am also attempting to install this chipset so my Usb wifi antenna will work in ubuntu 10.04 . Unfortunately I am inexperienced at installing .tar.gz files . I do have the .tar.gz file on my devices driver cd . Any help would be greatly appreciated. Is there a way to use gui to do this?

---

### Post by joshruehlig on 2010-07-04
Check if your wireless work out of the box.

Do you have the same chipset as ours? **If you dont know plug in your usb and type "lsusb" in the terminal, this will tell us something.**

usually .tar.gz file I just double click and ubuntu chooses to unpack (or extract) them.

As for your cd there should be a linux or hopefully ubuntu readme that may help, btw I usually never use the cd software as it is usually not the latest, but lets get your chipset first.

As for gui, yes most can be done with a gui. run "sudo nautilus" in a terminal and do what you need to do, but often times the terminal needs to be used.

---

### Post by RyuzakiTenseiga on 2010-07-04
Wow a reply . Ok first I know that its rtl8912su . Another issue I have is without my usb antenna working I can't use synaptic package manager or anything so its still a fresh install without updated info . as for lsusb I see it lists a realtek semiconductor device but i don't remember the exact text . I'm still relatively noob status so bare with me.  I basically don't understand the steps to install this .tar.gz (same as one in 1st post on thread)

---

### Post by joshruehlig on 2010-07-04
> **RyuzakiTenseiga said:**
> Wow a reply . Ok first I know that its rtl8912su . Another issue I have is without my usb antenna working I can't use synaptic package manager or anything so its still a fresh install without updated info . as for lsusb I see it lists a realtek semiconductor device but i don't remember the exact text . I'm still relatively noob status so bare with me.  I basically don't understand the steps to install this .tar.gz (same as one in 1st post on thread)

**Can you please run lsusb in a terminal and post the exact results**. If you have ubuntu .tar.gz file should just be able to be double clicked, thats ubuntu 10.04 is configured to open .tar.gz files, but if that doesn't work just right click the file and open it with archive manager then extract it.

You can also untar the file in a terminal...

---

### Post by RyuzakiTenseiga on 2010-07-06
lsusb gave me this:
Bus 002 Device 002: ID 0bda:8192 Realtek Semiconductor Corp.

---

### Post by joshruehlig on 2010-07-07
> **RyuzakiTenseiga said:**
> lsusb gave me this:
Bus 002 Device 002: ID 0bda:8192 Realtek Semiconductor Corp.

I'm 80% sure that if you follow these directions you will have your wireless working.

[http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html)

This worked for me but I have the rtl8172, but we may need to look for a different driver for you to start with. Just try the steps and keep me posted on if you have any problems

---

### Post by RyuzakiTenseiga on 2010-07-07
OK so I went and tried to follow the steps like you advised me . 
problem is at the second command in step 2

unzip rtl8192SU_usb_linux_v2.6.0006.20100226.zip 

it says directory not found . am I just not typing it into the terminal right? I wish I could just find a .deb file that would install this chipset for me but I don't know if that is at all possible.

also on launchpad i found a bug fix thats at this link: 
[https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455)

I am unsure if this would help me either. 
I assume the link you gave me is a step by step to compile the driver right?

Sorry I am having so much trouble but I really appreciate the help.

---

### Post by baguahsing on 2010-07-07
I just downloaded a driver from the Realtek website for the rtl8192su and it is rtl8192su-usb-linux-v2.6.0006.20100625.zip which seems to be a newer version.  I am using 10.04 and I believe you are using 9.1.  I don't know if it really makes a difference.  If you want it let me know.  I need this driver for an Asus usb-n10 wireless adaptor for my laptop.

---

### Post by RyuzakiTenseiga on 2010-07-07
> **baguahsing said:**
> I just downloaded a driver from the Realtek website for the rtl8192su and it is rtl8192su-usb-linux-v2.6.0006.20100625.zip which seems to be a newer version.  I am using 10.04 and I believe you are using 9.1.  I don't know if it really makes a difference.  If you want it let me know.  I need this driver for an Asus usb-n10 wireless adaptor for my laptop.


I am running 10.04 Amd64 version . That does look to be a newer driver but I don't know if it will make a difference actually either . I can't even seem to manage to get the terminal to let me use the cd~/desktop command at this point .

---

### Post by joshruehlig on 2010-07-07
> **RyuzakiTenseiga said:**
> I am running 10.04 Amd64 version . That does look to be a newer driver but I don't know if it will make a difference actually either . I can't even seem to manage to get the terminal to let me use the cd~/desktop command at this point .

The instructions I gave must be used to "hack" the rtl usb drivers for the kernels in ubuntu 10.04. It shouldn't be too hard to execute those command, don't just copy paste, see what you are actually doing.

cd ~/Desktop  #should work
#not cd~/desktop ... cd opens and the directory is ~/Desktop (or /home/"yourusername"/Desktop

before you run unzip in the terminal make sure you have the .zip file in your current directory. type "ls" this list whats in your current directory. This can also be done by just double clicking the .zip file in a file viewer, it should normaly open with archive manager. Anyway type ls, see whats in there, the command posted may not always be perfect so make sure you are unzipping the correct file.

dont worry you can do this. Ohh and hopefully the driver also works on AMD builds, I cant guarantee it but you should be able to do all of the driver building and findout in a matter of minutes. If not we can try the easier, but I belive worse way of using ndiswrapper.

______________________________

Ohh and use the newer version if you want, might be better? I use it.. just make sure the commands you use are changed for the specific files.

---

### Post by RyuzakiTenseiga on 2010-07-07
ok I will try that next and let you know what happens. Of course knowing my track record at this point I may have a few more issues but I know I can work through it eventually. 


Also I found a .deb on launchpad that was related to RTL8192SU at this link :
[http://launchpadlibrarian.net/51039041/linux-firmware_1.34.2%7Etest1_all.deb](http://launchpadlibrarian.net/51039041/linux-firmware_1.34.2%7Etest1_all.deb)

its a bug fix i believe.

---

### Post by joshruehlig on 2010-07-08
> **RyuzakiTenseiga said:**
> ok I will try that next and let you know what happens. Of course knowing my track record at this point I may have a few more issues but I know I can work through it eventually. 


Also I found a .deb on launchpad that was related to RTL8192SU at this link :
[http://launchpadlibrarian.net/51039041/linux-firmware_1.34.2%7Etest1_all.deb](http://launchpadlibrarian.net/51039041/linux-firmware_1.34.2%7Etest1_all.deb)

its a bug fix i believe.

Might work, you can try it, just tell me if you want ndiswrapper instruction, its probably the easyest way to get it working

---

### Post by RyuzakiTenseiga on 2010-07-08
i came close last night but during make install it either crashed or my laptop overheated . ndiswrapper may be my next step but will aircrack-ng work then?

---

### Post by joshruehlig on 2010-07-08
> **RyuzakiTenseiga said:**
> i came close last night but during make install it either crashed or my laptop overheated . ndiswrapper may be my next step but will aircrack-ng work then?

Lol netbook cooler? haha. ndiswrapper cant do aircracking... I dont think this chipset can either someone needs to write a patch for the drivers. I recommend WN11v2, I picked one up for $6 bucks (not from ebay, I forgot where) and it works out of the box in ubuntu.

[http://cgi.ebay.com/Netgear-WN111-100NAR-802-11b-g-n-USB-WiFi-Adapter-NR-/280529755081?cmd=ViewItem&pt=LH_DefaultDomain_0&hash=item4150e05bc9#ht_500wt_1154](http://cgi.ebay.com/Netgear-WN111-100NAR-802-11b-g-n-USB-WiFi-Adapter-NR-/280529755081?cmd=ViewItem&pt=LH_DefaultDomain_0&hash=item4150e05bc9#ht_500wt_1154)

---

### Post by RyuzakiTenseiga on 2010-07-08
Seriously? Well I got this antenna from geeks.com for like $40. It works amazingly in windows usually at minimum 4-5 bar signal. And I think I actually had that usb thing before and it didn't even compare to this antenna.  So I guess I will be a little busy today and won't have time to work on it . If you want to give me the ndiswrapper method I can try that next since it doesn't matter as much if its not compatible with aircrack-ng . I guess that explains why it wouldn't work in Backtrack too. Thanks.

---

### Post by joshruehlig on 2010-07-08
> **RyuzakiTenseiga said:**
> Seriously? Well I got this antenna from geeks.com for like $40. It works amazingly in windows usually at minimum 4-5 bar signal. And I think I actually had that usb thing before and it didn't even compare to this antenna.  So I guess I will be a little busy today and won't have time to work on it . If you want to give me the ndiswrapper method I can try that next since it doesn't matter as much if its not compatible with aircrack-ng . I guess that explains why it wouldn't work in Backtrack too. Thanks.

Sure ndisgt is a gui for ndiswrapper and makes it very easy. First download the Windows XP driver for your device. 

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true) (This also has some very new Linux drivers, I'm gona update and post check them out)
____

sudo apt-get install ndisgt #should also get ndiswrapper

sudo ndisgt
____

browse to the windows XP .inf file you downloaded. Should now work upon startup.

*I had a problem of it not working after a resume from suspend, in that case you need to unplug and replug the usb, or do what did and write a sript that runs after a resume that virtually unplugs, and replugs your usbs. If you have this problem check post #6 of this earlier thread.

[http://ubuntuforums.org/showthread.php?t=1466185](http://ubuntuforums.org/showthread.php?t=1466185)

Feel free to ask me for any help.

---

### Post by RyuzakiTenseiga on 2010-07-10
so I finally had the oppurtunity to successfully complete the steps from the saimux link 
Unfortunately when I attempted to boot the ubuntu system it had either a black screen or a bunch of text regarding the system . 
the error I managed to catch was [drm:drm_fb_helper_panic] *error * panic occured . 


whats up now?

---

### Post by joshruehlig on 2010-07-10
> **RyuzakiTenseiga said:**
> so I finally had the oppurtunity to successfully complete the steps from the saimux link 
Unfortunately when I attempted to boot the ubuntu system it had either a black screen or a bunch of text regarding the system . 
the error I managed to catch was [drm:drm_fb_helper_panic] *error * panic occured . 


whats up now?

Sorry I really dont know?** Maybe try to boot recovery style through grub**, I dnt know the the buttons of the top of my head. Thats really weird. Your not messing with anything that would affect booting at all? I dnt see how the two are unrealated,when u said that ur computer was freezing on compiling that was weird too. I'm sorry this is over my head...

The only thing even touching the booting sequence is #sudo make install, and that wouldn't still get you to something, command line.

I would personaly would LiveCD, recover files. fresh install, then compile drivers fresh. But I like creating tons of installs lol

---

### Post by RyuzakiTenseiga on 2010-07-10
Damn I wonder if it has anything to do with it being a wubi install..... I'm pretty sure it was either an error on my part or a hardware issue with this laptop . still I do believe we are on  the right track.


So this morning I attempted a fresh install and compiled it as steps say . As I do sudo modprobe 8712u it goes to a black screen with a cursor in top left as well as an unmovable mouse icon. ???? My fault or problem unknown?

---

### Post by joshruehlig on 2010-07-10
> **RyuzakiTenseiga said:**
> Damn I wonder if it has anything to do with it being a wubi install..... I'm pretty sure it was either an error on my part or a hardware issue with this laptop . still I do believe we are on  the right track.


So this morning I attempted a fresh install and compiled it as steps say . As I do sudo modprobe 8712u it goes to a black screen with a cursor in top left as well as an unmovable mouse icon. ???? My fault or problem unknown?

weird? its just a wifi module... umm i never do wubi install, I always hear bad thing about them. Its up to you if you really want a good ubuntu desktop I would do a fresh install and see if you can get the wireless working after that. BTW use the newest driver  and use the instructions provided in document. they work with no work arounds for me, unlike the older ones that I was using. Then if you can get it working post and Ill show you the best way to get it working on startup.

heres the link
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

it finally properly supports the kernel, the instructions are in document folder

---

### Post by RyuzakiTenseiga on 2010-07-10
Thats the driver I just tried . I think I made an error though.

I actually started a new thread just in case this was a separate problem . 

This was my post on that thread:

So I have recently been making attempts at  setting up my RTL8192SU chipset usb wifi . After struggling to set it up  by following the steps on this link: [http://www.google.com/url?sa=t&sourc...Kw0jUyXQukrfIw]("http://www.google.com/url?sa=t&source=web&cd=10&ved=0CEEQFjAJ&url=http%3A%2F%2Fsamiux.blogspot.com%2F2010%2F05%2Fhowto-realtek-8192su-usb-dongle.html&ei=T8Q4TM7MOYqisQPk_-RR&usg=AFQjCNGTj8NTxESTDWmqKw0jUyXQukrfIw")

After doing this I had no idea what it was supposed to look like but It  did display several warnings along the lines of "*warning*: cast  from pointer to *integer*  of *different* size"

not knowing what this means doesn't help . 

I continued following steps as another error occurred "cp  cannot stat  autoconf.rtl8712_usb_linux.h" 
I then entered sudo modprobe 8712u and my screen went black i was forced  shut down .
Upon rebooting I found it also would lock up if my usb device was  plugged in 
It will boot with it unplugged but as soon as it is plugged in again it  will lock up my system and send it to a black screen. 
I would really appreciate any assistance . 
If you need more info let me know and I will do my best to help
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=9573072") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=9573072")

---

### Post by anewguy on 2010-07-10
Just curios if you ever tried the file creation I recommended.  I know it doesn't say your chipset number, but I actually found a thread that showed this as the solution for someone WITH your chipset.  They didn't need to install drivers, etc., just install Ubuntu and do the file creation.  I posted this to someone elses post about this same adapter and it worked for them as well.

If you haven't done so, get back to a clean slate (remove any of the drivers, etc., you have installed for getting this working) and try it.  If it doesn't work you aren't out anything but 5 minutes of time.

---

### Post by RyuzakiTenseiga on 2010-07-10
actually i didn't see your file creation method .

and I don't know how to get it back to a clean slate is there a way besides reinstall?

oh btw , i was playing with backtrack 3 and managed to get it to detect wlan0! 

of course i couldn't figure out how to get it to function properly .  

so I am thinking that possibly the steps need a sudo - i command from the start?

---

### Post by joshruehlig on 2010-08-13
Try a clean install of ubuntu (preferably not wubi) and follow the instructions in the Documents folder with this package. Has been working for my since late July release of the driver.

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

---

### Post by gharika on 2010-08-31
try this

[http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html)

this worked for me :)

---

### Post by aviator01 on 2010-09-01
I compiled the driver and installed using "sudo checkinstall"  On reboot the ASUS wirless was working just fine.  I tried following the directions in the driver pack, but I could only get the wireless to work with "make" then "sudo insmod 8712u.ko" per the instructions.  So I follwed the instructions in this thread about "how to install ANYTHING".  Anyway, using checkinstall seemed to work for me. 

Does anybody have any better ideas???

---

### Post by lopata on 2010-09-10
> **gharika said:**
> try this

[http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html)

this worked for me :)

wow  this damn worked for me also xD

i reinstalled the x86 version

x64 didnt worked..

now to make aircrack work with it..

---

### Post by RyuzakiTenseiga on 2010-11-08
So i finally made it back here. 

I am starting over and using virtualbox and ubuntu 10.10 . 
So is there hope for this usb dongle ? (Hornettek Janus RTL8192su chipset)

---

### Post by clevetbs on 2010-11-13
> **gharika said:**
> try this

[http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html)

this worked for me :)

this method certainly worked. 
just one question monitor mode is supported on this card but aircrack-ng doesnt see it.

---

### Post by pi/roman on 2011-01-19
> **joshruehlig said:**
> I'm 80% sure that if you follow these directions you will have your wireless working.

[http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html)

This worked for me but i have the rtl8172, but we may need to look for a different driver for you to start with. Just try the steps and keep me posted on if you have any problems

Thanks joshruehlig. I just got an rtl8192su usb and this guide worked for me on 10.10.  For testing purposes i wanted to see if other methods in this thread worked so i plugged this dongle into various other distros and any other methods, including the downloaded driver without the alterations in this guide, had too many compiling errors to fool with.

The only thing that should probably be added is that gcc does need to be installed to compile this driver:
```
sudo apt-get install gcc
```Also the driver needed to be modprobed a few times before it started working but maybe it just had a long init period.

---

### Post by Bucky Ball on 2011-01-20
It should be as easy as downloading the driver, untarring it, cd to the directory and:

```
sudo su
make
make install
```

Then reboot.

A tip, and this took me an age to work out. If you put:

```
sudo make
sudo make install
```

... it doesn't work!!! For some reason you need to 'sudo su' and become root, then run:

```
make
make install
```

Worked straight away for me installing Realtek driver for my card.

---

### Post by walt.smith1960 on 2011-01-20
I have a couple RTL8192SU devices and have yet to compile anything. The reason mine didn't work out of the box was a missing folder & its firmware file.  The problem and solution are documented here:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

Natty 11.04 will recognize this device without any tweaking at all.

---

### Post by pi/roman on 2011-01-20
> **walt.smith1960 said:**
> I have a couple RTL8192SU devices and have yet to compile anything. The reason mine didn't work out of the box was a missing folder & its firmware file.  The problem and solution are documented here:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

Natty 11.04 will recognize this device without any tweaking at all.

Thanks walt, the same is confirmed with mine.

---

