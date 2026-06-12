---
title: "[SOLVED] Has anyone figured out WG111v2 on Gutsy?"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by sennep on 2007-10-25
**_[SIZE="4"]For a step-by-step guide, see[/SIZE]_**  [post #6]("http://ubuntuforums.org/showthread.php?t=590942#6")


I'v tried a bunch of things, including ndiswrapper and wifi-radar.. but still no connection.. all I get is NO DHCPOFFERS RECIEVED.. I'm trying to connect it with wpa-psk, (I've heard it works out of the box with WEP, but it's not my router so I'm not able to configure it).. I'm new to ubuntu and I really want this to work, cause it's a real pain having to start windoze everytime I need to use the internet..

So just to check if it's really possible, is there anyone out there who have been able to get the wg111v2 to work on gutsy with wpa?


EDIT:

Never mind I figured it out! Wohoo! Internet! Turns out I had to use wicd, and the win98 driver that was on my cd didn't work, so I had to download an older version of it..

---

### Post by sgant on 2008-01-14
what driver did you use?  Are you using it with ndiswrapper?  I'm using wicd and I can see my network, but it doesn't connect.  Could you give details on your setup?

---

### Post by sennep on 2008-01-15
yes I'm using ndiswrapper.. I can't remember which version of ndiswrapper but it's the one that's on the ubuntu live CD (the Ubuntu 7.10 Live CD that is)..

so basically my setup is:
Ubuntu 7.10
Netgear Wg111v2 USB wireless device
Wireless network encrypted with WPA-PSK (TKIP)
ndiswrapper and wicd

I was able to get a connection before I installed WICD, but I had to retype my password every time I logged on to ubuntu, and connecting to the internet took like a minute, so I uninstalled network-manager and installed WICD.. So I guess WICD isn't really needed, but it made things a whole lot easier for me, and the time it took to connect was reduced to a couple of seconds..

As for the driver, this is the driver I used [http://www.majorgeeks.com/Realtek_RTL8187_USB_Wireless_LAN_ME2000XP_d5165.html](http://www.majorgeeks.com/Realtek_RTL8187_USB_Wireless_LAN_ME2000XP_d5165.html)

(use the driver in the win98 folder found in that download) and yes, there is a win98 folder in the download even though it only says (ME/2000/XP) on the web site..

I should point out that my wg111v2 is a 0846:6a00 (if you type "lsusb" (small L not capital I) in the terminal, the output should say something about your Wg111v2 and there should be some strange numbers like 0846:6a00 or  0846:4240
I've heard that you should use the driver I mentioned above for the  0846:6a00, but for the 0846:4240 you should use this driver [ftp://downloads.netgear.com/files/wg111_2_1.zip](ftp://downloads.netgear.com/files/wg111_2_1.zip)

I also blacklisted the rtl8187 driver, and I used Ndisgtk (a graphical frontend for ndiswrapper, but this isn't really needed)..

feel fre to ask if there's something you don't understand or don't know how to do, like blacklisting rtl81817 or installing ndisgtk..

---

### Post by shaggydavid on 2008-01-18
can you tell me what blacklisting rtl 81817 is?

---

### Post by Hightide on 2008-01-18
I had a similar problem with the Netgear WG111v2 usb on 7.10 until I could drastic action and reinstalled Gutsy. Now my 2 PVC's  all  work fine  even with the rtl8187 driver.

But before you take this action, please look at Kevdogs tutorial

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)


be back later:)

---

### Post by sennep on 2008-01-18
[SIZE="5"][COLOR="Red"]**I haven't been able to get my wg111v2 working in Hardy (Ubuntu 8.04), the guide below is for Gutsy (Ubuntu 7.10)**[/COLOR][/SIZE]


[SIZE="4"]**_In case anyone needs it, here's a step-by-step guide to what I did to make it work:_**[/SIZE]
These instructions are for Ubuntu 7.10 (Gutsy Gibbon). If you use Xubuntu, you must substitute the word "gedit" in the instructions with the word "mousepad", if you use Kubuntu, I'm not really sure, but I think you can use the word "pico" instead.

_**First step**_

First, plug your wireless adapter into your Ubuntu computer.

Find a computer with an internet connection and download these things:
[ndisgtk]("http://packages.ubuntu.com/gutsy/i386/ndisgtk/download") (you must choose a mirror) this is a graphical frontend for ndiswrapper, so you don't have to type so much.

(If you don't want to download ndisgtk you don't need to, it's just so you don't have to type so much. Just see the notes in **step 4** when you get there if you don't have ndisgtk.)


Next, you need to download a driver we can use with ndiswrapper (ndiswrapper is a small program that let's you use your wireless adapter's windows driver in Ubuntu)

You must first figure out what driver you need, to do this, locate the terminal (Applications-->Accessories-->Terminal)

Inside the terminal, type this: ```
lsusb
``` and hit enter (that's a small L and not a capital i by the way)

in the output, there should be a line saying something about your WG111v2, and there should be some strange number like 0846:6a00 or 0846:4240. I've heard that if your Wg111v2 is a 0846:6a00, you should use [this driver]("http://www.majorgeeks.com/Realtek_RTL8187_USB_Wireless_LAN_ME2000XP_d5165.html"). (you must choose a mirror).
If you have the 0846:4240 version you should use [this driver]("ftp://downloads.netgear.com/files/wg111_2_1.zip") instead. 


After I downloaded the driver I needed (in my case the 0846:6a00 driver) I unzipped it in Windows, then I burned a CD with the driver and ndisgtk on and copied it to a folder on the Ubuntu computer (just make a new folder in your home directory and put it there). 
If you have a dual-boot system (both Windows and Ubuntu installed on the same computer) you can just download the files in windows and unzip, and when in Ubuntu you can just copy the files from your windows partition.

**Note:**Make sure the name of folder you make doesn't have any spaces in it. See "Troubleshooting ndisgtk" at the end of this guide if you want an explanation.



_**2**_
Then I installed ndiswrapper, to do so, open synaptic package manager (System--> Administration--> Synaptic Package Manager), and find the two packets named "ndiswrapper-common", and "ndiswrapper-utils-1.9", (use the search function, just search for the word ndiswrapper) and install them.. (you install them by clicking the box next to them and choosing "Mark for installation", and then click the button called "Apply"). You don't need an internet connection to do this, it will ask you to insert your ubuntu live CD and it get's them from the CD if you don't have a connection.

After ndiswrapper has been installed, you should install ndisgtk, to do that, simply locate the folder you copied it to, and doublecklick the ndisgtk file. A window should pop up, and there should be a button that says "install package" or something like that. Click the install package button, and wait until it's finished.


_**3**_
Ubuntu has some built-in drivers for the WG111v2 that needs to be disabled so they won't conflict with the ndiswrapper driver. In order to do so, type this in the terminal  ```
sudo gedit /etc/modprobe.d/blacklist
``` and press enter, you will be asked for your password, so type your password and press enter, a document should open.

If you have the 0846:6a00:
add "blacklist rtl8187" without the quotes to the bottom of the document and save the file. Restart your computer.

If you have the 0846:4240:
I'm not really sure which driver should be disabled, so to be on the safe side, just add all of these  to the bottom of the document and save the file. 
blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb
blacklist rtl8187
blacklist r8187b

Restart your computer.


**Note:** After restart, to check if the drivers were disabled (or blacklisted to be more correct), in the terminal, type ```
lsmod
``` and hit enter. This will list a bunch of stuff, if the drivers you blacklisted are not listed, you have successfully blacklisted them. If they are listed, you can try to remove them by typing this in the terminal "sudo rmmod drivername" without the quotes and hit enter. _**Example:**_ sudo rmmod rtl8187


_**4**_
Then, I loaded the windows driver using ndisgtk (a menu item called Windows Wireless Drivers is found
under System --> Administration after you install ndisgtk) Simply click on Windows Wireless Drivers, and it should be pretty straight forward how you use it to load the driver. For the 0846:6a00, use the driver in the win98 folder found in those driver files you downloaded in the first step, for the 0846:4240 the driver is inside the folder called ndis5 in the driver files you downloaded earlier. **Make sure you point it to the file that ends with .inf **

After loading the driver, in Windows Wireless Drivers, I clicked the button called Configure Connection (or something like that). I turned roaming OFF, and then I typed in the SSID (also known as network name or ESSID), I chose my encryption type (like WEP or WPA) and I typed in my password. Also, I chose DHCP in that box underneath the password box. I did not set any other settings than those.

After a minute or so, it suddenly connected, and everything worked fine. If it doesn't connect after a minute, don't worry, just proceed to **step 5**.

**Note:** If you don't want to download ndisgtk, **or you can't get ndisgtk to work**, you can point ndiswrapper to the correct driver by using the terminal, see Troubleshooting ndisgtk in the notes at the end of this guide.

_**5**_
But the next time I started the computer, it didn't load ndiswrapper. So to make it load on startup, I typed this in the terminal: ```
sudo gedit /etc/modules
```  (and hit enter)
It will ask you for your password, after you give it your password, a document will open. Add "ndiswrapper" without the quotes to the end of the document and save the file. The next time you restart, ndiswrapper should load automatically.

**Note:**If your unable to get a connection after you restart, try retyping your password. (not because I think you spelled it wrong, but because this will make Ubuntu try to connect). Give it a minute, (it might take even longer). On my desktop it connected after one minute on the first try, but on my laptop I had to retype my password three times before it connected (and yes, I'm sure I spelled it correctly all three times). If you go to System--> Administration -->Systemlog. Click daemon.log on the left side (and scroll all the way to the bottom) you can monitor what happens when you try to connect. Look what "dhclient" is doing. It should do stuff like "DHCPDISCOVER", "DHCPREQUEST" and finally "DHCPOFFER". If you don't get "DHCPOFFER", but instead you get "NO DHCPOFFERS RECIEVED", try to retype your password. Also make completely sure you have set the correct SSID and encryption, and that roaming is off and you have chosen DHCP.

_**6 (optional, but could be useful)**_
Some people (like me) experience that you have to retype your password every time you start Ubuntu, and that it takes a minute to connect. To solve this I installed Wicd (an alternative to network-manager), that solved all my problems. After I installed Wicd it connected after a few seconds, and I never had to retype my password again. Here are the instructions I used to install Wicd [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

And of course, I had to set my SSID and password and encryption type in Wicd.


_**7**_
That's it, hopefully you have now got a working internet connection, if not, feel free to ask for help!:) Comments are of course also welcome:)


_**Notes:**_

**_32bit and 64bit_**
I've only tested this on 32bit (x86) Ubuntu and Xubuntu. I have not tested the 64bit versions, and I don't know if they will work with 64bit versions. If you have no clue whether you have a 32bit or 64bit Ubuntu, you most likely have 32bit, think back to when you downloaded the ISO (the CD file thing) for Ubuntu, if you chose the Standard personal computer (x86 architecture) option, you have 32bit.

If you wish to try on a 64bit Ubuntu, note that the link I provided in the guide to the ndisgtk is the 32bit version of ndisgtk. Click [here]("http://packages.ubuntu.com/gutsy/amd64/ndisgtk/download") for the amd64 version of ndisgtk. I guess you might have to use a driver made for 64bit version as well. I know very little about this, so I would advice to search the forum specifically for how to do this with 64bit. 

_**Troubleshooting ndisgtk**_
I've noticed that Ndisgtk (Windows Wireless drivers menu thing) seems to have a problem with spaces in folder names when pointing to the .inf file. I had to rename a folder so that the path to the .inf file had no folder names with spaces in them.


If you don't want to download ndisgtk, or you can't get it to work, you can point ndiswrapper to the correct driver by using the terminal:

```
sudo ndiswrapper -i your_driver.inf
``` "your_driver" is the path to and name of your driver. Hit enter.
**Example:**  sudo ndiswrapper -i /home/sennep/RTL8187/WIN98/Netrtuw.inf

**Note:** Capitalization does matter! If something is in uppercase letters, make sure you write that in uppercase when you use the ndiswrapper command! **netrtuw.inf** is NOT the same as **Netrtuw.inf**

then type:
```
sudo depmod -a
``` and hit enter. Then type:
```
sudo modprobe ndiswrapper
``` hit enter, then type:
```
sudo ndiswrapper -m
``` hit enter.


I order to check if it was installed correctly, type ```
ndiswrapper -l
``` and hit enter (small L not capital i). It should say something about that your driver is installed and that hardware/device is present. If it doesn't, make sure your WG111v2 is plugged in, and try to reinstall the driver, make sure you wrote the correct path to the driver, and make sure you wrote .inf at the end.

Then manually configure your connection, (by right clicking the network symbol and choosing manual configuration if I remember correctly), turn roaming off, set the SSID, encryption type, password and choose DHCP.


**_Out-of-the-box with WEP_**
Shaggydavid discovered that the WG111v2 should work out of the box with 128bit WEP encryption, but only if your router is set up properly! see posts [13]("http://ubuntuforums.org/showthread.php?t=590942#13") and [15]("http://ubuntuforums.org/showthread.php?t=590942#15")


_**Leaving the WG111v2 in the USB port**_
I left my wireless device plugged into the usb during the entire process, I didn't take it out or plug it in at a certain step. I actually plugged it in before I installed Ubuntu, and I haven't unplugged it since.

---

### Post by shaggydavid on 2008-01-18
when installing gutsy gibbon, should i have the netgear wlan pluged in to the usb before booting and installing the os?  will this help the os config the device?

---

### Post by ruabelk on 2008-01-20
My first attempt at Ubuntu:

Directions are great; but I can't seem to fine the two packets named "ndiswrapper-common", and "ndiswrapper-utils-1.9". Is there a source on the website?

Thanks for taking the time to post this info, I'd have been here a long time!

---

### Post by ruabelk on 2008-01-20
Additional comment; found ndiswrapper on sourceforge.net. Should I use 1.9 or is it safe to use the latest stable version [1.51]?

---

### Post by sennep on 2008-01-20
> **shaggydavid said:**
> when installing gutsy gibbon, should i have the netgear wlan pluged in to the usb before booting and installing the os?  will this help the os config the device?

hmmm, I have no clue if that makes a difference or not.. I've heard that you're not supposed to do that on Windows, but I've always thought that was because the driver must be installed first, so I'm not sure the same rules apply for Ubuntu.. All I can say is that mine was plugged in to the usb during installation.. sorry I can't be of more help..





**ruabelk**: you couldn't find the packets? that's really strange.. I found mine by going to System --> Administration --> Synaptic Package Manager. Inside Synaptic Package Manager, I used the search function and searched for the word ndiswrapper. The packets you need should be in the results.. 

Just to clarify something, 1.9 is the ndiswrapper utilities version, while 1.51 is the ndiswrapper version.. I used  ndiswrapper utilities 1.9 and ndiswrapper 1.43.. both are installed with the packages  ndiswrapper-utils-1.9 and ndiswrapper-common..

I would advice you to try installing through Synaptic Package Manager again, since this is by far the easisest way to do it. I think the files on sourceforge might have to be compiled from source, and that can be a tedious process.

If they're not in your search results, I wonder if we have to enable some repositories.. but I really think all the repos needed for ndiswrapper should be enabled by default.. but just in case, go to Applications --> Add/Remove. Inside Add/Remove click the button called Preferences (or something like that), and make sure your main and universe repositories are enabled, also, make sure the Ubuntu CD itself is enabled. (All those options are inside that Preferences thing somewhere).. Try the Synaptic approach again..

If the synaptic approach doesn't work, try this little trick to make it install ndiswrapper from CD: In the terminal, (Applications-->Accessories-->Terminal) type this ```
sudo apt-cdrom add
``` and hit enter, it will ask you for your password, type it and press enter.. then type ```
sudo apt-get update
``` and hit enter.. after that, ```
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
``` and hit enter..

If all else fails, you can try downloading the .deb packages from [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndiswrapper&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndiswrapper&searchon=names&subword=1&version=gutsy&release=all)
When they are downloaded, you just doubleclick on them to install..

---

### Post by shaggydavid on 2008-01-20
[QUOTE=sennep;4172670]hmmm, I have no clue if that makes a difference or not.. I've heard that you're not supposed to do that on Windows, but I've always thought that was because the driver must be installed first, so I'm not sure the same rules apply for Ubuntu.. All I can say is that mine was plugged in to the usb during installation.. sorry I can't be of more help..

in windows they say not to, but i have installed both ways in windows xp pro sp2, is has the same effect and i can not tell a difference.  im going to try to install gutsy with it in from boot till end,  and then if that dosnt work i will try the oppisite.  kinda like research.  i installed gutsy on an e-machines laptop that had an installation of windows media center on it.  it found the adapter and the network my house usess and let me connect to it.  only thing is the enternet did not work.  i will load my findings later. thanks for the help.

---

### Post by ruabelk on 2008-01-20
Well, we're almost there.

Followed your tips, more or less, ended upwith ndiswrapper-1.8 but the wg211v2 is recognized and I can connect to the AP. Only problem I have now is it does not give me the choice of using WPA-PSK. I havd to use WEP128. Any suggestions?

---

### Post by shaggydavid on 2008-01-23
it helped to have it in the usb when installing. i also had to change the wep encryption from 64bit to 128bit, and my passphrase worked then. i hope this helps. it does work out of the box if you have your router setup right.

---

### Post by sennep on 2008-01-23
> **ruabelk said:**
> Well, we're almost there.

Followed your tips, more or less, ended upwith ndiswrapper-1.8 but the wg211v2 is recognized and I can connect to the AP. Only problem I have now is it does not give me the choice of using WPA-PSK. I havd to use WEP128. Any suggestions?

I only had the choice of WEP before I installed ndiswrapper, but after installing ndiswrapper I got the option to choose WPA-PSK.. You installed utils 1.8? I used 1.9, but I have no clue what the difference is between them, so I don't know if that might have anything to do with it.. Is your device a 0846:6a00 or a 0846:4240? are you using network manager or Wicd?




> **shaggydavid said:**
> it helped to have it in the usb when installing. i also had to change the wep encryption from 64bit to 128bit, and my passphrase worked then. i hope this helps. it does work out of the box if you have your router setup right.

That's good news:) I also left it in the usb when installing (due to laziness), and I did get the option of WEP..unfortunately it's not my router, and the router was configured for wpa-psk, so I never got a chance to test if it actually worked out of the box.. I'll put it in my guide that it will work with 128bit WEP out of the box..is your device a 0846:6a00 or a 0846:4240?

---

### Post by shaggydavid on 2008-01-23
its a 0846:6a00.  also manual config didnot work.  i had to go to the network icon in the top left click once to see the networks and after i changed my router settings it worked i typed in my passphrase and presto,it did take about a minuet for it to conect, and every once in a wile the signal drops to 0% all you have to do is disconnect (from the icon again by ckicking on the network) after it disconnects, click on the network icon again and ckick on your network and it will conect again.

---

### Post by Daneel24 on 2008-01-25
> **sennep said:**
> here's a crude step-by-step guide to what I did

This actually worked perfectly for me, thanks :) I do have to reconnect manually occasionally but it's not too bad.

---

### Post by ODF on 2008-01-25
Looking good so far for me.

In my case networking was actually working but was VERY unstable.

Thanked you :D

---

### Post by ~vel on 2008-01-28
> **Daneel24 said:**
> This actually worked perfectly for me, thanks :) I do have to reconnect manually occasionally but it's not too bad.

Did you by chance find a fix for it dropping?

---

### Post by Daneel24 on 2008-01-30
Nope, sorry. It's not that much of a problem to me as I mostly use it for surfing and I wouldn't have any idea what to do about it either way...

---

### Post by ~vel on 2008-01-30
Hmm, it's kind of a necessity to me to have a constant connection since I bridge my connections with my xbox 360  =/

---

### Post by sennep on 2008-02-02
**~vel**: Are you using Wicd or network-manager?

---

### Post by ~vel on 2008-02-02
network manager. it's using the prism54 driver

---

### Post by sennep on 2008-02-02
are you using it with ndiswrapper? and what encryption type?

And what is the usbid of your device? (those numbers you get when typing lsusb in the terminal)

---

### Post by miketowninc on 2008-03-24
Hello

I followed all the steps but I cant connect. My cord works because I see my hotspot but when I connect it never gets my IP. I use wep 128. 

Please help before I abondon Ubuntu!!!

---

### Post by sennep on 2008-03-25
> **miketowninc said:**
> Hello

I followed all the steps but I cant connect. My cord works because I see my hotspot but when I connect it never gets my IP. I use wep 128. 

Please help before I abondon Ubuntu!!!

Post the output of these commands:


```
ndiswrapper -l
```

```
lsusb
```

```
lsmod
```

```
iwconfig
```

```
sudo lshw -C network
```

---

### Post by miketowninc on 2008-03-25
HI

Thanks for the answer. Here are the results. Just so you know i tryed connecting without security. And it go the usuall 192.168... but nothing else. I couldn't reach the routers fireware. 

michael@MichaelsUbuntu:~$ ndiswrapper -l
netrtuw : driver installed
        device (0846:6A00) present (alternate driver: rtl8187)
michael@MichaelsUbuntu:~$ lusb
bash: lusb: command not found
michael@MichaelsUbuntu:~$ lsusb
Bus 004 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
michael@MichaelsUbuntu:~$ lsmod
Module                  Size  Used by
af_packet              24840  4 
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
dock                   10656  0 
container               5504  0 
sbs                    19592  0 
battery                11012  0 
video                  18060  0 
ac                      6148  0 
button                  8976  0 
ndiswrapper           185240  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
joydev                 11328  0 
pcmcia                 41388  0 
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
pcspkr                  4224  0 
serio_raw               8068  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
psmouse                39952  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  4 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
ata_generic             8452  0 
ata_piix               17540  4 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  4 sg,sd_mod,sr_mod,libata
b44                    28300  0 
mii                     6528  1 b44
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 ndiswrapper,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
michael@MichaelsUbuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Pompidous Hotspot"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:E7:13:A6:0D   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

michael@MichaelsUbuntu:~$ sudo lshw -C network
[sudo] password for michael:
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:1b:8a:31
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=32 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1b:2f:72:96:b3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netrtuw driverversion=1.45+Realtek Semiconductor Corp. link=yes multicast=yes wireless=IEEE 802.11g


Thanks!!

---

### Post by sennep on 2008-03-27
Those all look fine.

With security turned off, try to use MAC filtering and see if this makes a difference.

---

### Post by miketowninc on 2008-03-28
That didn't help.:( Is there a way I can chat with you about this? I take classes online and I need to work on my own computer. Thanks!!!

You can write me at [email]miketowninc@hotmail.com[/email]

---

### Post by miketowninc on 2008-04-02
I so how manage to connect to another wifi spot in my area and it gets the IPs and everything. But the internet is very very very very slow. I bet that there is o percent packet loss. Also if you ping there is no return.  Can you help?

---

### Post by sennep on 2008-04-03
I'm not sure what could be wrong, your output looks fine. I've heard some people have this problem though, that they are able to connect but it's extremely slow.
You might want to try connecting step by step at the command line since this supposedly makes it easier to troubleshoot. Have a look at kevdog's guide [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by miketowninc on 2008-04-07
I tryed that and it didnt help. Any other ideas? I tryed both wep and no wep

---

### Post by m4cks on 2008-04-07
I would like to report my results (new gutsy install). I have been able to use both rtl8187 and the ndiswrapper driver, but both have problems:

Device is a netgear wg111v2 (real v2), reporting as 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

rtl8187:
No security: Works, but performance degrades after a while
WEP/WPA: Works, but performance degrades after a while

ndiswrapper (tried with both the netgear (win9 1_3_0 drivers and also the realtek manufacturers/OEM drivers)

No security: works perfectly. fast. holds connnection.
WEP/WPA: associates to AP, but does not "talk".. some packets are sent, but I can't get a DHCP response.

...since no security is not an option, I'm still stuck with the rtl8187 and degraded performance. If anyone knows why security might not be working with ndiswrapper and the two drivers I tried, I'm all ears.

also, router (siemens) is saying this when I try to connect with security:

2008-01-03 01:09:47 GMT E |Wireless |Station MAC 00:1B:2F:71:82:E9 - association failed - responding station does not support the specified authentication algorithm.

It should be noted that WEP/WPA works perfectly fine in windows with this device and AP.

---

### Post by miketowninc on 2008-04-16
Ok so this is what I have done. I created an Ad-Hoc with a different wireless card and I tried connecting to it with the WG111v2 in Windows XP. And it worked. But once i tryed it in UBUNTU it says that it connected but it says it doesnt have any IP. I can't ping anything. This has to be a problem with ubuntu right?

The Ad-Hoc is open.

---

### Post by sennep on 2008-04-16
sorry for the late answer guys I've been offline for some time..

**m4cks:** it seems to be a mystery unfortunately, many people have this problem. If you are able to use MAC filtering with ndiswrapper you have at least a minimum of security. Also, this one guy couldn't connect with ndiswrapper at all, but when he enabled MAC it suddenly worked, so it might be worth a try.


**miketowninc:** The problem definitively happens when you use ubuntu, so it's a problem related to ubuntu at least, but it's not necessarily the OS itself, but rather the driver or ndiswrapper or network manager.
The strange thing with your case (and many others) is that all the output looks fine, so it's nothing obvious to troubleshoot. Some people are able to connect out of the box with the rtl8187, but I haven't been able to do that. If you want to try to disable ndiswrapper and connect with the native rtl8187 driver, simply remove the rtl8187 from the blacklist, and remove ndiswrapper from the /etc/modules list. 
If you can wait 8 days until ubuntu 8.04 is released, rumor has it that rtl8187 has been fixed, so it should work out of the box, with no need for ndiswrapper or anything like that. (if the rumor is true that is).

---

### Post by miketowninc on 2008-04-16
Ok I will wait 8 days I guess. Eventhough i downloaded the beta and it didnt help. lol. oh WEll we shall see.

---

### Post by sennep on 2008-04-18
> **miketowninc said:**
> Eventhough i downloaded the beta and it didnt help.
That's NOT a good sign for us wg111v2 people:(

---

### Post by miketowninc on 2008-04-20
Just in case. With my week cmd promt skills I tried to blacklist the wg111v2 ndiswrapper driver so I could use the native driver and it did work. But can you tell me how to blacklist and stuff like just so I know I did it right. Or a way to tell what driver wg111v2 is using?

---

### Post by sennep on 2008-04-22
> **miketowninc said:**
> Just in case. With my week cmd promt skills I tried to blacklist the wg111v2 ndiswrapper driver so I could use the native driver and it did work. But can you tell me how to blacklist and stuff like just so I know I did it right. Or a way to tell what driver wg111v2 is using?


if you do the ```
lsmod
``` command, you can check the output too see if ndiswrapper is listed (which means it's running) and if rtl8187 is running. (you have to restart first though)


blacklisting is just putting the name of the driver in blacklist found in /etc/modprobe.d/blacklist
You can open that list by typing this:
```
sudo gedit /etc/modprobe.d/blacklist
```

So to unblacklist the rtl8187 you just remove it from that list.



To stop ndiswrapper, I don't think you need to blacklist the driver ndiswrapper uses, but rather simply remove the word "ndiswrapper" from the list found in /etc/modules
You can open that list by typing:
```
sudo gedit /etc/modules
```

(I haven't actually tried it myself, but I think that should be sufficient to stop ndiswrapper from starting up).

---

### Post by walkerp1 on 2008-05-06
Thanks so much! I made the mistake of trying to get my wg111v2 working in Hardy using the procedure outlined in your post. I finally managed to get it connected for less than twenty seconds, and then my box locked up. After the reboot, it wouldn't work again...and who would want it to in that case?

This morning, I reloaded Gutsy from my trusty USB stick, and using your procedure had my wireless up in no time at all. For the life of me, I cannot imagine why ndiswrapper is not considered critical enough for the live-cd?!! Does anyone have an idea if we're close to getting a native driver for the wg111v2?

---

