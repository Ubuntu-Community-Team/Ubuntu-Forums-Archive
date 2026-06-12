---
title: "ndiswrapper, &quot;require auth for wireless&quot; loop?"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by farnswerth on 2011-07-24
[COLOR="Red"]Edit:  [SOLVED]  If you searched for an issue where you have the Realtek 8176 usb, and it just plain won't get recognized, double check that you have the right driver(oh yes, it's possible that what you thought you downloaded was not what you needed.  Read on.).  If you have a "require authorization..." loop, the wrong driver *can* do this[/COLOR]  My problem was that the linux driver I had was the wrong one, even though I clicked the link that worked for other people.  Seems that those driver id's can get confusing, plus, realtek's website is a bit wonky for me.  

the driver marked RTL8188CE on the download page is mislabeled, and does NOT work for my adapter  (MAKE SURE that the filename listed on the download description is the same as the filename you actually get when you download.)

The one marked RTL8188CE-VAU is the correct one.(For me, at least.  I have a generic branded usb adapter. It looks like this [Link]("http://www.amazon.com/150Mbps-WIFI-WIRELESS-ADAPTER-802-11/dp/B002XGDU9M/ref=pd_cp_e_3")

Thanks to Wildmanne39 for finding the correct driver!

[COLOR="Red"]/Edit[/COLOR]




Okay, I have a no-name wireless usb adapter, and I installed ndiswrapper and installed a winxp driver.  This is the only way I could get anything even close to internet connectivity, but all it does is try to connect and then give me the "require authentication for wireless network" dialog box, over and over.  ( I read that this can be because the driver is wrong, or something, but I copied straight from the driver cd, onto the desktop, and instaled from there...  so I think I read wrong?)

I've tried this on 11.04, 10.10, 9.10(using a live cd AND installing for each of them...  So I've been at this a Very Long Time).  I've tried all the tutorials on getting wireless to run, installing drivers, etc. that I could find. (if it wil help to list them here I will.  But there's a lot.) I tried to configure a wired network to my windows laptop(what I'm using now) and I can connect to the network but not the internet(ICS on, etc.)  

lsusb shows my chipset for the generic usb adapter as 8176 (Realtek), and I've found some info online about other chipsets from Realtek, but I don't know what to do with that info.

I've spent the last two days trying to figure this out, and before that, I've spent almost no time with ubuntu(or linux distros at all).  So I only kinda know how the processes work.  I'm tired, sstressed out with this thing, My sanity is in question...  Please, help?

---

### Post by androssofer on 2011-07-24
Ive been through similar issues... you could spend years tryin to get it to work.. in the end i gave up and got a wireless usb tht i knew ubuntu supported... i know its a cheeky solution... but works :-)

here is a thread to help choose:

[http://ubuntuforums.org/showthread.php?t=556037](http://ubuntuforums.org/showthread.php?t=556037)

---

### Post by farnswerth on 2011-07-24
> **androssofer said:**
> Ive been through similar issues... you could spend years tryin to get it to work.. in the end i gave up and got a wireless usb tht i knew ubuntu supported... i know its a cheeky solution... but works :-)

here is a thread to help choose:

[http://ubuntuforums.org/showthread.php?t=556037](http://ubuntuforums.org/showthread.php?t=556037)

Thanks, I'll definitely get another one when i can, but it's gonna be a quite a while before I can afford one.  Like, a couple months at least.

---

### Post by anewguy on 2011-07-25
Try following this thread, and pay attention to the link it provides.  BTW - the 8176 is the usb product id, not the actual chipset.

[http://ubuntuforums.org/showthread.php?t=1617972]("http://ubuntuforums.org/showthread.php?t=1617972")

dave ;)

---

### Post by sadaruwan12 on 2011-07-25
My friend I also had the same issue what you're facing right now. I asked every one and searched every where I managed to find my way around with the same software your using.

So it seems like still the ndiswrapper hasn't taken the full priority so here is a link that I've posted how I managed to get the wrapper working.

Hope this help you.

[Click Me]("http://myfossness.blogspot.com/2010/05/how-to-get-rtl8187b-working-in-ubuntu.html")

---

### Post by beew on 2011-07-25
I would just buy a new usb wireless card that works. This one works out of the box, I got it for about $16, you can get it on ebay for about $6 I think
[http://www.cty.ca/ProductDetails.asp?pid=3267](http://www.cty.ca/ProductDetails.asp?pid=3267)

---

### Post by farnswerth on 2011-07-25
> **anewguy said:**
> Try following this thread, and pay attention to the link it provides.  BTW - the 8176 is the usb product id, not the actual chipset.

[http://ubuntuforums.org/showthread.php?t=1617972]("http://ubuntuforums.org/showthread.php?t=1617972")

dave ;)

Thanks, that post has a link to another post that says
> **cavalier911 said:**
> From [www.pcidatabase.com](www.pcidatabase.com) :
```
Device ID:	0x8176
Chip Number:	REV_01
Chip Description:	Realtek RTL8188CE Wlan 802.11n
```

Go here: [http://ubuntuforums.org/showthread.php?t=1604101](http://ubuntuforums.org/showthread.php?t=1604101)  **thread #6**

And that one says:

> **dushyanthan said:**
> After some trial following instructions on this post this is what worked for me:

1) Go to R[http://www.realtek.com.tw/downloads/...true#RTL8188CE]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE") and download the tar.gz file

2) open terminal and do 'sudo apt-get install build-essential'

3) Follow the readme file's instructions:

[LIST]
[*]sudo su
[*]make
[*]make install
[*]reboot
[/LIST]
When I logged in again I was on WiFi....

SHould I do it this way, instead of with ndiswrapper?  

Okay, I extracted the downloaded tar.gz and I get a folder called rtl_92se9de_linux_mac80211_0003.0401.2011    Do I navigate to this folder(with the cd command in the terminal) or one inside it?

---

### Post by androssofer on 2011-07-25
> SHould I do it this way, instead of with ndiswrapper? And if so, do I extract the tar.gz file first? As in, I click on it(to get to the readme), it opens in archive manager. should I extract with archive manager before following the readme instructions ?

i would say tht way would work btr than ndiswrapper.

i would extract it first, then follow the readme.

cd into the folder it created. then run the make, make install etc. tho read the readme first, it should say if u need to go to a different folder

---

### Post by farnswerth on 2011-07-25
> **sadaruwan12 said:**
> My friend I also had the same issue what you're facing right now. I asked every one and searched every where I managed to find my way around with the same software your using.

So it seems like still the ndiswrapper hasn't taken the full priority so here is a link that I've posted how I managed to get the wrapper working.

Hope this help you.

[Click Me]("http://myfossness.blogspot.com/2010/05/how-to-get-rtl8187b-working-in-ubuntu.html")

Thank you  Glad theres some peopl who are having success.  I'll try this one next!

---

### Post by farnswerth on 2011-07-25
> **androssofer said:**
> i would say tht way would work btr than ndiswrapper.

i would extract it first, then follow the readme.

cd into the folder it created. then run the make, make install etc. tho read the readme first, it should say if u need to go to a different folder


I extracted, followed the instructions in the post, which were the same as the readme.  I was in the right directory, everything loaded and no errors, etc.  Rebooted, nothing changed.  Still can't see a wireless connection, tried ifconfig to see what was going on there(supposed to show wireless in there?  read it in one of those posts) I get eth0  link encap: Ethernet
                                and
                   lo    link encap: Local Loopback

there's a bunch more info on those two, but I don't have the ethernet connected atm.  Can post it if it's needed. 

Anyway, from what I've gathered from the forum posts, internet, and what I *should* have going on here, My wireless adapter isn't configured right?  The only time I get anything is with ndiswrapper loaded with a WinXP driver, and that seems to be the wrong driver.

I read that REaltek drivers ending in "su" i.e. rtl8188su(or whatever) are the ones made for usb.  Don't know if this is true but when I tried to download any other than the one posted 

> Go here: [http://ubuntuforums.org/showthread.php?t=1604101](http://ubuntuforums.org/showthread.php?t=1604101) thread #6
here,

I just get a Realtek dummy page, like the drivers are no longer available.  SO I don't know what to do on the get-the-linux-driver side of things.

---

### Post by wildmanne39 on 2011-07-25
Hi, run these commands in a terminal and we can help you, most likely you have more then one driver for the wireless card installed since you tried ndiswrapper and after you remove it, and others if there are others it will work.

```
sudo lshw -C network
```
```
lsmod
```
```
lsusb
```
```
rfkill list All
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

Thank you

---

### Post by Noncon on 2011-07-25
What type of security are you using on the router?  If it is something like WPA-PSK (TKIP) or WPA2-PSK (AES), your adapter may not be capable of that level of security, so you will need a new adapter. 

I had to toss more than a few older/cheap adapters because of this.  You could try turning off security at the router temporarily to see if you can connect. 

KJ

---

### Post by farnswerth on 2011-07-25
```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:3f:00.0
       logical name: eth0
       version: 01
       serial: 00:16:35:ab:0c:84
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5752-v3.10 ip=192.168.1.108 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:e2400000-e240ffff

``````
lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
vesafb                 13449  1 
nvidia               9766978  44 
snd_hda_codec_hdmi     27479  4 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
hp_wmi                 13418  0 
ppdev                  12849  0 
sparse_keymap          13666  1 hp_wmi
tpm_tis                13993  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
usbhid                 41704  0 
snd_timer              28659  2 snd_pcm,snd_seq
parport_pc             32111  1 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
hid                    77084  1 usbhid
psmouse                73312  0 
tpm                    21251  1 tpm_tis
tpm_bios               13460  1 tpm
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
floppy                 60032  0 
tg3                   131476  0 

``````
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````
rfkill list All
Bogus list argument 'All'.
```rfkill list all, and rfkill list  didnt give me anything.

This adapter worked great for xp, I haven't changed the encryption at all when I changed over to ubuntu...   

I am more than willing to reinstall and start from scratch, by the way...

---

### Post by wildmanne39 on 2011-07-25
Hi, ok here we go make sure that you have uninstalled ndiswrapper by using this command
```
sudo apt-get autoremove ndiswrapper
```

Then open synaptic,install kernel-headers and build-essential then put your 
Go to [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Download the RTL8188CE-VAU driver.

Follow the readme file's instructions:

    ```
sudo su
    make
    make install
```
    reboot
If it does not connect or you have problems post back here.

Disconnect your wired connection before you reboot.

---

### Post by farnswerth on 2011-07-25
> **wildmanne39 said:**
> Hi, ok here we go make sure that you have uninstalled ndiswrapper by using this command
```
sudo apt-get autoremove ndiswrapper
```

Then open synaptic,install kernel-headers and build-essential then put your 
Go to [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

Download the RTL8188CE driver.

Follow the readme file's instructions:

    ```
sudo su
    make
    make install
```
    reboot
If it does not connect or you have problems post back here.

Disconnect your wired connection before you reboot.

I got a couple of questions, first I noticed that the "8188" driver that I download is actually "8192".  seems to be the same for kernel 2.6.34and earlier  and 2.6.35and later.  Could this be an issue?

Also, when I extract the downloaded file, in the main folder are three different driver folders, 8192ce 8192de and 8192se.  Should I be doing something, like getting rid of two of them, before I go into terminal and start the make process?

---

### Post by wildmanne39 on 2011-07-25
Hi, I found the driver I had to do some more research this is the link.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Just delete all the other ones you download before and install this one. 
I am sorry the site made it so difficult.

---

### Post by wildmanne39 on 2011-07-25
Here is a screenshot this is for 11.04.

---

### Post by farnswerth on 2011-07-25
> **wildmanne39 said:**
> Hi, I found the driver I had to do some more research this is the link.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Just delete all the other ones you download before and install this one. 
I am sorry the site made it so difficult.


That did it :D   THANK YOU!
No need to apologize, I should have paid more attention and thought it through, but the sheer number of different posts and tutorials we come across, trying to fix our computers, makes it easy to slip up.  Hopefully someone will come across this and some of this info will help them out.

Thanks to Everyone who took the time to write me!



the driver marked RTL8188CE on the download page is mislabeled, and does NOT work for my adapter

The one marked RTL8188CE-VAU is the correct one.

---

### Post by wildmanne39 on 2011-07-25
Hi, your welcome! that is great I am glad it worked, enjoy ubuntu.

---

