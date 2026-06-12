---
title: "Edimax EW-7318Ug USB howto"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by blackest_knight on 2006-10-18
Edimax EW-7318Ug this is a usb wireless54g device unlike the pcmcia offering you cant just plug and play you need to do some work first. 
this post should make it easy. 
The current ralink sources shouldnt need altering however if the VID and PID change then you will need to edit rtmp_def.h and enter the vid and pid 
found by typing lsusb into a terminal window 

lsusb produces 
Bus 005 Device 005: ID 148f:2573 Ralink Technology, Corp for me and this is already in rtmp_def.h so life gets simpler.

open a terminal and copy and  paste the following commands. 

[B]sudo apt-get install linux-headers-$(uname -r) build-essential g++-3.4
wget http://www.ralinktech.com/drivers/Linux/RT73_Linux_STA_Drv1.0.3.6.tar.gz
tar -xvf RT73_Linux_STA_Drv1.0.3.6.tar.gz
cd RT73_Linux_STA_Drv1.0.3.6/
cd Module/
sudo cp -v Makefile.6 ./Makefile 
make all
sudo cp -v rt73.ko /lib/modules/`uname -r`/kernel/drivers/usb/net/
sudo mkdir -pv /etc/Wireless/RT73STA
sudo cp -v rt73.bin /etc/Wireless/RT73STA/
dos2unix rt73sta.dat -f
sudo cp -v rt73sta.dat /etc/Wireless/RT73STA/rt73sta.dat
sudo insmod /lib/modules/`uname -r`/kernel/drivers/usb/net/rt73.ko

dmesg [/B]
# now plug in your device 
**dmesg** 
#should see something like 

[17385845.440000] idVendor = 0x148f, idProduct = 0x2573
[17385845.440000] **RT2573**<7>usb device name rausb0
[17385845.440000] **RT2573**<7>BulkOutMaxPacketSize  512
[17385845.624000] **RT2573**<7>rt73_get_wireless_stats --->

run the networking configuration tool from menu's **System->Administration->Networking**

hopefully now you see an unactivated rausb0 configure it with your ssid and encryption ect activate it and set the gateway device to rausb0
hopefully  now you can connect with it. 

and now make it load automagically in the terminal type 
[B]
sudo depmod -a[/B]


I was going to edit /etc/network/interfaces file but the gui tool does it for you. (**sudo gedit /etc/network/interfaces**)

thats it should be up and working
notes 
The tar file is liable to be updated at any time so if you cant fetch it check to see what version is available and alter the wget statement to suit.

---

### Post by blackest_knight on 2006-10-20
In theory the above post should work and it does for my laptop however it doesn't for an old k6 system with 256 meg ram. 
The Usb stick starts flashing its lights and sends packets even recieves a few but it doesnt actually connect.

I would welcome any comments if the method i posted works for you 
ie that its complete and satisfactory or any suggestions to get it to connect to my router. 
incidentally dmesg keeps going on about a missed interupt for the HD I guess such a slow processor might have problems anyway.

---

### Post by Pixie25 on 2007-04-17
I followed the instructions above, but I can't get it working.
I use edgy eft... 
when I run dmesg I  get the following error:

[17179738.712000] rausb0 (WE) : Driver using old /proc/net/wireless support, please fix driver !

I've downloaded the latest driver version. How to solve ?
help would be most appreciated.

---

### Post by Me! on 2007-08-22
:popcorn:

Thank you it is working now ! but with new driver 1.0.4.0

Thank you :KS

---

### Post by pite on 2007-09-24
Maybe I did something wrong, but it does not work. I followed given instructions _after_ plugging the thing in, and trying to reach the net. Does this make any difference?

After the process, I only got a wlan0 interface, and in the GUI an additional wmaster0 thing. no rausb0.
Then it lists the available networks, but after selecting an entry (wep-psk, tkip), it drops an error: (translated from hungarian) > Error while connecting - the requested wireless network uses security options unsupported by hardware
Vendor says it does know a lot about wep2 and stuff.

oh, and the dmesg output after insmodding:
> [  613.928000] rtusb init ====>
[  613.928000] usbcore: registered new interface driver rt73
[  645.152000] usb 3-6: new high speed USB device using ehci_hcd and address 6
[  645.428000] usb 3-6: configuration #1 chosen from 1 choice
[  646.020000] wmaster0: Selected rate control algorithm 'simple'
[  646.236000] wlan0: starting scan
[  647.232000] wlan0: scan completed

---

### Post by korisnickoime on 2007-10-02
deleted

---

### Post by korisnickoime on 2007-10-03
deleted

---

### Post by jnui on 2007-11-14
Hi there I have another similar install guide.

go to my forum to see how I got this to work.
the key for me to initially get it to work was to use the old driver.

then I could not get WPA working , and the trick was to use the iwpriv command
the normal iwpriv commands i found did not work for me I had to use slightly different commands.

the link to the entire post is here.
[http://www.niumata.com/forum/viewtopic.php?id=6](http://www.niumata.com/forum/viewtopic.php?id=6)

this post includes the old drivers so you can download, and a handy install script made by linuxemporium.co.uk that will take care of the initial install.

johnny
[www.niumata.com](www.niumata.com)

---

### Post by 23meg on 2007-11-14
The EW-7318UG just works in Gutsy, without having to switch drivers.

---

### Post by sebastjanp on 2007-12-06
No it doesn't. It works on the live mode but when installed there's the same sh..t :(

That's my second USB dongle that doesn't work. (first was belkin)
Does somebody have a suggestion which to buy? 
I have tried a several guides to get those to work with no go.
Please let someone tell me which Wireless USB dongle works out of the box.

---

### Post by 23meg on 2007-12-26
It certainly does work in Gutsy; I've installed it on three computers, no problems. I haven't tried it in the live environment. We're probably talking about two similar but different versions, or some difference in your configuration is preventing it from working after installation.

---

### Post by martin_n_c on 2008-01-02
I haven't got an internet connection on ubuntu, not even a wired one, so I can't use apt-get or wget. Is there any way I can follow the howto by downloading files to my windows partition first? I'm new to linux, so sorry for being ignorant!

---

### Post by martin_n_c on 2008-01-03
> **martin_n_c said:**
> I haven't got an internet connection on ubuntu, not even a wired one, so I can't use apt-get or wget. Is there any way I can follow the howto by downloading files to my windows partition first? I'm new to linux, so sorry for being ignorant!

Sorry - I should have added I'm using Gutsy (7.10). I've just upgraded from Feisty (7.04) and the flaky connection I had has gone. I can't seem to install an rt73 driver any more. I think my upgrade got rid of some of the headers I need, and I don't know how to get them back!

I tried the tutorial that jnui linked to above because that doesn't need an internet connection. Unfortunately,  I can't get that to work. I'd like to give the howto a go instead.

---

### Post by martin_n_c on 2008-01-13
Just an update. I got my  EW-7318Ug working thanks to the help of [Matt Hartley]("http://www.lockergnome.com/linux/2007/11/04/ubuntu-gutsy-with-expresscard-working-options/").

Did a fresh install of Gutsy (7.10) and followed the instructions he posted on January 10, 2008 @ 4:38 pm (follow the link above and scroll down the page). The script he refers to in step 3 is linked to from the top of the page, under the YouTube video. Look for a link called 'rt73usb-wifi'.

---

### Post by rodica.balasa on 2008-01-18
I managed to make it work using Edimax drivers, only on inconvinence: it is seen as a wired connection by network manager (using gutsy):

[http://www.len.ro/work/tools/old-new-i8000-2]("http://http://www.len.ro/work/tools/old-new-i8000-2")

---

### Post by reasoner on 2008-03-13
The script by Matt Hartly at [http://www.lockergnome.com/linux/2007/11/04/ubuntu-gutsy-with-expresscard-working-options/](http://www.lockergnome.com/linux/2007/11/04/ubuntu-gutsy-with-expresscard-working-options/)
almost worked to get my EW-7318Ug working under gutsy, but it needed one modification.

There is only three critical steps and one more step to restart so I'll list them here.
It starts by blacklisting a kernel module that (I think) interferes so it won't be reloaded in the future.

echo  'blacklist rt2500usb'  |  sudo  tee  -a  /etc/modprobe.d/blacklist

Next load the kernel module that is needed like this.

sudo  modprobe  rt73usb

In the end the script didn't work until I removed the blacklisted kernel module manually. Originally I did this last but I think it's best to do it here.

sudo  modprobe  -r  rt2500usb

The script next runs iwconfig which I think is just to see how things are going. The command is just:

iwconfig 

Finally  the script just restarts the networking system:

sudo   /etc/init.d/networking  restart

That might be all you need to do but the usual networking setup applies from here. For example I went to System/Administration/Network/WirelessConnection/Properties and unchecked roaming mode and typed in the ESSID of my wireless access point and set the configuration to DHCP. I haven't tried WEP yet.

I was using iwconfig to see the signal strength and strangely discovered that if I wrapped my hand around the radio that it ceased functioning and wouldn't start working again until I restarted the networking. I guess it was overheating and shutting itself down, but it would stop functioning after just a couple seconds. The radio gets pretty warm but I'm surprised it overheats that fast. Maybe it's not overheating maybe it's something else.

---

### Post by No_Gate$ on 2008-03-19
Somewhat new to this so hope it's Ok to post here. Have been struggling with getting a wireless connection to function using this hardware. To date the only time it has worked perfectly was in Live CD mode where it was brilliant. 

However, after installing I cant make it actually connect. I have tried various methods of getting a connection, including all of the ones listed in this thread plus some others I found via Google, and the nett result is still no connection.

Currently is configured in line with the instructions here [http://www.len.ro/work/tools/old-new-i8000-2](http://www.len.ro/work/tools/old-new-i8000-2) as suggested by rodica using Wicd as the network manager. Wicd appears to work perform OK as changing back to a wired connection gives an almost instant response from the switch. No wireless though.

The hardware is listed correctly using lsusb and the modules are all in the blacklist according to the instructions. IWCONFIG returns the device as wlan0. If the device is configured manually either using IWCONFIG and IWPRIV or using the GUI, it says it has connected but i am unable ping the switch or get to the internet. If DHCP is enabled it attempts to get an address but fails after around 4 attempts.

Have rebuilt from scratch 6 times now over the last couple of weeks using the i386 and AMD versions and have the same result.

Any help would be greatly appreciated.

A little frustrated but willing to persevere

Paul

---

### Post by elicoten on 2008-03-22
I found that the EW-7318UG can be configured using the instructions on the first post of this page if you are not using WPA. 

If you have a WPA encrypted network then try the instructions [http://www.niumata.com/forum/viewtopic.php?id=6](http://www.niumata.com/forum/viewtopic.php?id=6) as suggested earlier in this thread and use the IWPRIV SET commands as suggested at the end of [http://www.len.ro/work/tools/old-new-i8000-2](http://www.len.ro/work/tools/old-new-i8000-2) to input the WPA EncrypType and WPAPSK. Network Manager does not seem to be displayed the correct infomration but the wireless card is working.

---

### Post by BarnyB on 2008-03-31
> **martin_n_c said:**
> Just an update. I got my  EW-7318Ug working thanks to the help of [Matt Hartley]("http://www.lockergnome.com/linux/2007/11/04/ubuntu-gutsy-with-expresscard-working-options/").

Did a fresh install of Gutsy (7.10) and followed the instructions he posted on January 10, 2008 @ 4:38 pm (follow the link above and scroll down the page). The script he refers to in step 3 is linked to from the top of the page, under the YouTube video. Look for a link called 'rt73usb-wifi'.

As the above user quoted, if you got to Matt Harley's site he has a note at the top of the post advising NOT to use Wicd but to use NM due to id'd issues with Wicd and this chipset. Issues that I had are also listed on the site in the Comments section from a few days ago. I basically had messed around so much with my config files (as it seems you may have done) that I basically had to do a fresh install. Once done, I ran his provided sh script once and it all worked just fine.

My model is the EW-7318USG (USB dongle with the antenna)

---

### Post by No_Gate$ on 2008-03-31
Tried the suggestions again and still had issues. However, downloaded and installed MythBuntu 8.04 Beta, replaced Network Manager with Wicd and now works every time :)

Don't pretend to understand why but that's perhaps something to look at when I understand Linux configurations a little better.

---

### Post by portach king on 2008-05-02
Anyone have any advice on getting this working in Hardy?
The usb device is being detected but it isn't picking up any networks in wicd, and while it does list networks in NM it won't connect.
I have a broadcom card in my computer but it's not working correctly, hence the purchase of this card. The b43 driver are installed, but that shouldn't interfere, right?

---

### Post by No_Gate$ on 2008-05-02
Did yet another install (as it's so quick) using MythBuntu 8.04 and it finds and configures correctly using Network Manager without installing Wicd. Entered the WPA key and it's worked ever since

Hope this helps

Paul

**uname -a**
2.6.24-16-generic 
#1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux


**LSMOD for RT drivers.**
rt73usb                28928  0 
rt2500usb              26368  0 
rt2x00usb              14720  2 rt73usb,rt2500usb
rt2x00lib              25344  3 rt73usb,rt2500usb,rt2x00usb
rfkill                 10128  1 rt2x00lib
input_polldev           6928  1 rt2x00lib
crc_itu_t               3584  1 rt2x00lib
mac80211              192532  2 rt2x00usb,rt2x00lib
usbcore               169904  10 rt73usb,rt2500usb,rt2x00usb,lirc_mceusb2,snd_usb_audio,snd_usb_lib,usbhid,ohci_hcd,ehci_hcd

---

### Post by elicoten on 2008-05-04
I found with my Broadcom card that blacklisting b43 and unblacklisting bcm43xxx then re-extracting the firmware using some script which I found on this forum somewhere got my card working again.

I also have the EW7318Ug and it seems to work out of the box with Network Manager in Hardy, but somewhat unreliably. I might try compiling the same driver I used with Gusty for Hardy to see if that is any better

---

### Post by elicoten on 2008-05-04
I found with my Broadcom card that blacklisting b43 and unblacklisting bcm43xxx then re-extracting the firmware using some script which I found on this forum somewhere got my card working again.

I also have the EW7318Ug and it seems to work out of the box with Network Manager in Hardy, but somewhat unreliably. I might try compiling the same driver I used with Gusty for Hardy to see if that is any better

---

### Post by isnagil on 2008-05-05
Hi!!

Hey No_Gate$ I need more information please. 
I'm trying to install and configure the edimax ew-7318Ug in the new XUbuntu Hardy Heron. 
When you said that you have made a new installation you mean that you have install the 1.4 driver or the older?
Could you define the correct steps to get working this stuff?

Thanks

---

### Post by geezerone on 2008-06-03
Hi

I am having extreme difficulty in getting this device to work with Gutsy or Hardy.

---

### Post by elicoten on 2008-06-03
Its easier in Hardy - just plug it in. Are you sure you are using the same device. Not the EW-7813U**s**g or any other similar model? (see title for exact model).

In a clean Hardy installation it should literally be plug-and-play. If not it probably means you have tried to install some other driver, or blacklisted some modules or something.

If you are not using Hardy try upgrading to it. If you have followed some instructions to install another driver - uninstall it and hope that Hardy returns to using its built in drivers.

---

### Post by geezerone on 2008-06-03
Thanks for the speedy response.

I can do another clean install but what concerns me too is that if a system becomes 'unclean' let's say, I don't want to have to re-install everytime.

Anyway, I will give my 7318**UG** a go and see how it goes.

:guitar:

---

### Post by elicoten on 2008-06-03
It won't become unclean of its own accord. The default Ubuntu Hardy installation worked fine on my computer out the box (I did an upgrade from Gusty, so before the upgrade I removed all the modules that I'd installed to get the card working under Gusty).

Once you're on Hardy, you should be able to plug it in, and by ready to go.

I notice in your signature you have a link to WICD. I did not install and did not need WICD - it works fine for me with the Network Manager supplied in Hardy.

---

### Post by geezerone on 2008-06-03
> **elicoten said:**
> ...before the upgrade I removed all the modules that I'd installed to get the card working under Gusty).

Once you're on Hardy, you should be able to plug it in, and by ready to go.

I notice in your signature you have a link to WICD. I did not install and did not need WICD - it works fine for me with the Network Manager supplied in Hardy.

How and what modules were removed typically as I have tried various ways from posts on these forums and would like to be able to undo them.

I used WICD with a BT Voyager 1055 dongle which I had some success with but then stopped working, hence me getting the above device.

Thanks.

---

### Post by geezerone on 2008-06-03
I reinstalled Hardy and left the Edimax 7318UG device in during installation. I can now see my network but when trying to connect to it I keep getting asked for my (WPA2 Personal) password which is a long hex key.

I have tried configuring the nm-applet manually with fixed IP etc but no joy. Just out of interest why does the encryption change from WPA2 to WPA when you have set it to WPA?

May try WICD.

---

### Post by elicoten on 2008-06-04
Are you sure you are actually using WPA2? If not then that would explain why it's not working

The module I removed was the one I built - I'd actually tried to install several, but the name of the file was rt73.ko, and it was stored somewhere in the same place as all the other drivers, I think /lib/modules/kernel/... or something. Part of the installation instructions would give you this information depending on which instructions you followed.

Fixed IP/Static IP would not make any difference. I would double-check your encryption settings, or try as a test, disabling encryption and see if you can connect then. It sounds like its just a case of getting the encryption settings correct.

I have no experience with WICD, have never needed to try it. On mine, I simply select the network I want, type in thenetwork passphrase and that's all that's needed.

---

### Post by geezerone on 2008-06-04
Yes, deffo WPA2 but nm always shows WPA when configuring it again (others posts have said the same here).

I have tried WEP and still get the same problem.

I typed dmesg and got the information like the following:

```
[ 1889.488153] wlan0: authenticate with AP 00:1c:f0:e3:6f:d3
[ 1889.687837] wlan0: authenticate with AP 00:1c:f0:e3:6f:d3
[ 1889.887815] wlan0: authenticate with AP 00:1c:f0:e3:6f:d3
[ 1890.087791] wlan0: authentication with AP 00:1c:f0:e3:6f:d3 timed out
```(For info: Tried WICD but just hangs after configuration so will work with network manager for now).

Think this may be a bug. Still not plug-n-play unfortunately - just want wireless to work!

---

### Post by elicoten on 2008-06-04
I got those errors but I don't remember what I did to correct them. I think it means either wrong key or driver incorrectly installed. Which driver are you using? type lsmod to see a list of drivers in use.

---

### Post by geezerone on 2008-06-04
Not near machine at present to check module dependencies but I didn't install any driver - just using the Hardy default driver from fresh installation.

Will check later tomorrow exactly which.

---

### Post by geezerone on 2008-06-05
Some good news. I carried out the lsmod and showed rt73, rt73usb, rt2... drivers.

Blacklisting the drivers apart from rt73 still showed them after typing lsmod.

Anyway, I tried again (and again...) and out of interest type my wpa2 password under the network manager 'connect to another wireless network' window whilst keeping the encryption option set to wpa. I also changed frequency from channel 12 to a lower channel on my WAP (e.g. 10) and ensured that the device was extended via the usb cable and now auto-connects after login :)

What I am now looking into is getting the auto-login to work and prevent the 'keychain' authentication window appearing, i.e. auto connect to keychain. If I type my password then it connects straightaway.

---

### Post by elicoten on 2008-06-05
You shouldn't have **both** RT73 and RT73USB. If I remember correctly the RT73 one is the one you would have downloaded and installed manually. I would suggest unintalling that one (or at least renaming and moving it out of the /lib/modules/... (wherever it resides) directory.

The RT73USB module works fine for me with no problem, I think it may include and get loaded together with some of the RT2x00 drivers so don't worry about those.

I found that it stores the WPA keys and uses them automatically once they have been entered once - no keychain messages so might still be a drivers issue.

Unfortunately this is going beyond my depth I'm still fairly new to Ubuntu  I wonder if someone else knows about more about Network Manager and authentication, keychains, etc...

Anyway all the best and let us know how you get on and what you did to fix the problem. I would suggest unblacklisting all the drivers expect from RT73 and then using sudo modprobe -r to unload the RT73 driver (or just restart the computer after modifying the blacklist again).

Hope something of what I've said is helpful keep us updated.

---

### Post by geezerone on 2008-06-05
I didn't install any drivers but just used that which came with Hardy.

I will get an exact *lsmod *output done but how is uninstalling the non-required drivers done out of interest?

I believe that the pam keymanager is a possible fix for keychain nagging but time will tell.

For now, at least, the machine is working wirelessly without any driver download/install.

If I was a masochist I could try my BT Voyager 1055 USB adapters and get them working... but think I shall leave that for another day. :lolflag:

---

### Post by elicoten on 2008-06-05
When you reinstalled Hardy did you format the hard drive or just reinstall over the existing installation? Have you previously followed directions (i.e. possibly even the ones in the first few posts of this forum?) to install or compile drivers?

If you do modprobe -v you will get a list of modules loaded and you will see where all the files are located. Offhand I do not remember where they are but its somewhere under /lib. Taking care to ensure you don't remove any of the built-in modules, delete the module that is a result of compiling/installing the driver/following the instructions to install the drivers.

I hope this makes sense. I don't know why you are having problems with a keychain - I would imagine it is because you might be using the wrong driver. Do you know the name of the interface? (What's it called in iwconfig or ifconfig?)

---

### Post by geezerone on 2008-06-05
Hi

Formatted over previous Hardy installation. Didn't install any drivers - just used ones that came with install.

The key-chain only prompts me if I configure unit to 'auto-login'.

I am using wlan0 (not rausb or or other) and works with DHCP also.

---

### Post by geezerone on 2008-06-06
lsmod output:

```
rt73usb                27136  0 
rt2x00usb              12800  1 rt73usb
rt2x00lib              22528  2 rt73usb,rt2x00usb
rfkill                  8592  1 rt2x00lib

```

---

### Post by elicoten on 2008-06-06
Funny mine is rausb0 but looks like the right drivers. Not sure what else to say.

---

### Post by geezerone on 2008-06-13
Thanks for the time, I suppose one could say that the pre-installed drivers with Hardy DO actually work with this device. Just need to remember that using WPA2 don't select this in the nm configuration but use WPA instead (for me that was one of two problems anyhow - other was changing WAP channel number).

Working now anyhow. :)

---

### Post by geezerone on 2008-06-14
Guess what? Not working now after I plugged in an ethernet cable??

Now the wireless keeps dropping off every few seconds and reconnecting but unusable. :(

---

### Post by elicoten on 2008-06-14
I've found that you can only connect to one network at once wtih Ubuntu network manager - my observation may be incorrect, and I'm sure there's a way to do it (perhaps by fiddling with IP routing or something) but it seems that connecting to one network automatically disconnects from any others ur connected to, whether ethernet or wireless.

---

### Post by geezerone on 2008-06-15
Hi, back again!

I carried out lsmod as shown below:
```

**rt73usb                27136  0 **
rt2x00usb              12800  1 rt73usb
rt2x00lib              22528  2 rt73usb,rt2x00usb
rfkill                  8592  1 rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
mac80211              165652  2 rt2x00usb,rt2x00lib
```

Would the 'bold' line be correct with nothing associated?

Thanks again.

---

### Post by elicoten on 2008-06-15
The driver you want is the rt73usb, but if you look you'll see the rt73 depends on the 2nd and 3rd lines (rightmost column shows dependencies or something like that) and the rest of them are needed by the rt2x00lib which in turn is needed for the rt73usb. So I think you need them all.

But I'm really not sure this is way beyond my knowledge really - more like random guesses and observations. It certainly looks similar to whats on my computer.

---

