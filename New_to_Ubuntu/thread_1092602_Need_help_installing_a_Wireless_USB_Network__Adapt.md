---
title: "Need help installing a Wireless USB Network  Adapter"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by Lakeside5 on 2009-03-10
I have just tried to install a D-Link USB Network adapter, to use with my Linksys N Wireless Router. I guess it is meant for a Windows XP system (which it in fact mentions  in the instructions) but I was able to do through and finish successfully the software wizard (installation  CD) by using WINE, and install to a virtual C drive.  BUT, when I do step  2- actually connect the USB to a USB port, and the 'Found New Hardware' icon is supposed to come up..it doesn't. And I don't see this hardware listed along with the other  hardware (like cd Rom drive or  external hard drive).
Is there a way around this, or maybe I shouldn't have bought this? please help, thanks.

---

### Post by stanz on 2009-03-10
I won't be much help-sry...
but wine...a virtual C drive??? I give ya credit for trying.

Have you passed thru the:
**[COLOR=Red]Main Support Categories[/COLOR]**--->Networking & Wireless Section?
You might find someone has made it thru this.

My Linksys Wired/Wireless experience has been positive--but--
I've never needed to use the setup disk (usually meant only for m$).
and I've not done the virtual setup, like you have here...

Linux needs its own drivers to use these devices--just might take some
time finding them.

Hope this helps...  ;)

---

### Post by Lakeside5 on 2009-03-10
Thanks Stanz, will do :)

---

### Post by anewguy on 2009-03-10
2 things I would do:

(1) With the device plugged in, do lsusb in a terminal and post the results so we can see the device id -> we might be able to find the chipset from there

(2) After (1) [to be sure we don't need to blacklist something]:

install ndiswrapper and its utilities

using ndiswrapper and your Windows driver, install the driver to Linux


I've never tried using Wine for a driver before - I think it would only apply to apps actually running in Wine.

Using ndiswrapper, install the driver straight to Linux.

If you need any help or info on doing that, just post back and we'll be glad to help you out.

dave :)

---

### Post by abyssius on 2009-03-10
> **anewguy said:**
> 2 things I would do:

(1) With the device plugged in, do lsusb in a terminal and post the results so we can see the device id -> we might be able to find the chipset from there

(2) After (1) [to be sure we don't need to blacklist something]:

install ndiswrapper and its utilities

using ndiswrapper and your Windows driver, install the driver to Linux


I've never tried using Wine for a driver before - I think it would only apply to apps actually running in Wine.

Using ndiswrapper, install the driver straight to Linux.

If you need any help or info on doing that, just post back and we'll be glad to help you out.

dave :)

Assuming the computer you're setting up is not presently connected to the Internet, you can find the ndiswrapper software on your install CD. If you browse your CD, you’ll see directory named [pool].  If you open [pool] -  this will lead you to two sub-directories: [main] and [restricted].  Open the [main] directory and you will see several directories labeled alphabetically.  If you open the [n] directory, you’ll see two directories labeled [ndiswrapper] and [ndisgtk].

The procedure is to open the [ndiswrapper] directory. You’ll find two install packages: ndiswrapper-common and ndiswrapper-utils. First, install the ndiswrapper-common package (double-click on it). Next, install ndiswrapper-utils in the same fashion. Next, go one directory level up (back to where you saw the [ndisgtk] and [ndiswrapper] directories).  Open the [ndisgtk] directory and install that package.  This adds a [Windows Wireless Drivers] menu item to your [Administration] menu. You’re all set to install the Windows driver for your wireless adapter.

The next step is to locate the windows driver files.  You will need locate two files *your_adapter.inf* and *your_adapter.sys.* These files are usually located on the CD that came with your adapter. They are sometimes compressed within the .exe file on that CD. If this is the case, you can copy the .exe file to your desktop, then double-click on it to expand all the compressed files. You only need the .sys and .inf file, you can delete everything else. Once you've located these files, open the [Windows Wireless Drivers] menu, click the [Install New Driver] button, then browse to the .inf file and select it. This will install the drivers easily for you.

---

### Post by BDNiner on 2009-03-10
Yes, you seem to be making this more complicated than it needs to be. I don't think that you can install a driver for you wireless adapter using wine. Although you may be able to run the utility which I can see how someone would think that this is a valid solution to at least try.

The first thing we would need is the chipset of your wireless adapter. Plug the device in and run either 
```

lsub

```
or 
```

lshw -C network 

```
in a terminal, post the results and hopefully it can be determined how to get your wireless device working.

---

### Post by Lakeside5 on 2009-03-10
Ok BDNiner, Anewguy, when I enter lsusb:
Bus 005 Device 005: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]
Abyssius, maybe I'm doing this  wrong but, currently I am ON the  computer I want to set the wireless up for, the wireless USB is connected to a usb port, but I also have my modem connected to a wired router, which I am using right now. thanks.
I might have done this wrong,  but I browsed the cd (went to places>CD Rom drive where it was mounted, and open, but did not see any of the directories you list. thanks

---

### Post by anewguy on 2009-03-10
Ok, we can see from the lsusb as I requested that the chipset is ralink rt73.  There are many posts on getting the driver working for this device in Ubuntu.  Some recommend serialmonkey drivers, others have a different approach.  A yahoo search with ubuntu rt73 driver turned up many links.  A place to start might be:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73)


Also, if you do require ndiswrapper at some point, it is in the
/pool/main/n folder - you will see 2 folders there -> 1 for ndiswrapper - open it and double-click each file in there to install it.  The second is ndisgtk.  You may wish to open that folder and double-click on the files there to install it as well.  Ndisgtk is a gui'd front end to ndiswrapper, and some people prefer using it.  I have other posts in the forum about getting these packages if needed off of the installation CD.  Since you still have an internet connection, I would use synaptic package manager to install ndiswrapper and ndisgtk, but only if you need them.  It may be that by following one of the many links on setting up your device in ubuntu that you may find you don't need ndiswrapper.

Please post back if you have any questions at all along the way.

dave :)

---

### Post by Lakeside5 on 2009-03-11
Thanks  so much for the help.  I will try this tomorrow (1:20 am here now).
I still  don't know how to find the files you mention. I could give screenshots of what I find when browsing the installation disk (browsing the cd rom where it is mounted). So I sure hope I don't need ndiswrapper because I can't find it on the disk. G'night

---

### Post by Talon2 on 2009-03-11
Something to consider:  Life is short.  If your current adapter isn't just working then you might consider selling it so you can get one that "just works":

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833315075](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315075)

---

### Post by Lakeside5 on 2009-03-11
Well, u may be right, this guy talked me into buying his that he says he never used (new, in an opened box) as I only had $20 after shelling out for a new Linksys wireeless N router lol I hope he will take it back, but now I have learned to check for Linux compatibility next time.

---

### Post by Lakeside5 on 2009-03-11
Until I find Linux supported adapter I can buy locally (no credit card lol)  OR a local store that is familiar with Linux- Future Shop guys can't tell me for sure if they have any tht work well with Linux- I am  going to give this ndiswrapper a try.  I downloaded ndiswrapper from sourcceforge but have no idea how to use it to insstall my   Windows  drivers.

---

### Post by firefly2442 on 2009-03-12
I would install ndiswrapper from the Ubuntu repository and not from sourceforge.  Maybe try using Synaptic?  When I used ndiswrapper some time ago I think I also used "ndisgtk" to do the configuration and do the actual driver install.  Essentially, I had to give it an INF file and then it figured out the windows drivers and installed it.

---

### Post by anewguy on 2009-03-12
Well, let's go through the prerequisites first, then on to the detailed instructions.

(1)have the windows driver for your device loaded to your desktop.  These need to be the individual .inf and .sys files - not aip file or exe.

(2) Go through synaptic package manager and install ndiswrapper.  Do not use the one from sourceforge or go through the hassle of trying to compile ndiswrapper.

When you have both of these ready, then do the following:

go to a terminal window (application/accessories/terminal)

Type:

cd ~/Desktop

sudo ndiswrapper -i xxxxxx.inf <press enter>.  Replace xxxxxx with the name of your windows driver .inf file.

sudo ndiswrapper -l <press enter> - that's a lower case "L" for list.  It should return saying your device is loaded and the driver.  If not, stop and post back here.

sudo modprobe ndiswrapper <press enter>

sudo depmod -a <press enter>  This sets up for installing the ndisdriver kernel module.  

sudo ndiswrapper -m <press enter>  This is supposed to make ndiswrapper load at boot.  However, this doesn't seem to work anymore, so we do the following additional step:

cd /etc <press enter>

gksudo gedit modules <press enter>  This calls up the editor to edit the modules file.  This file contains the extra kernel modules we want load at boot.  Go to the end of the file and add a new line that says ndiswrapper, then save the file and exit.

Reboot.  Look for the network manager icon on the top bar (it looks like 2 screens on top of each other).

Click on the icon and see if any wireless networks show.

Post back what happens.

dave :)

---

### Post by Lakeside5 on 2009-03-12
Whoa, u two! Looks like ur gonna sort me right out here, thanks so much! I will try all this out after I've had my coffee and breakfast :)

---

### Post by eeperson on 2009-03-12
You shouldn't need to use ndiswrapper for a wireless adapter that uses the rt73 chipset.  It is already supported.  Just install the rt73-common package from the repositories.

Also, for future reference, Wine cannot be used to install hardware drivers.

---

### Post by Lakeside5 on 2009-03-12
"Also, for future reference, Wine cannot be used to install hardware driver"  Yeah, I kinda get that impression now  LOL :)  So, I have found and enabled  'rt73   common package'  Now what? I have the usb adapter plugged in, but I do not see it listed with the other hardware in 'places' (with the cdrom, eternal hardrive etc.).  Should I run the driver installation disk again (as I tried to install drivers using wine before).  I can see the contents of the disk when I go to the cdrom icon in 'places' and 'open to see the disk files, but not sure what to do, just getting myself mixed up.  And after I manage to install drivers (as you are saying that with 'rt73' on here now, I can actually install Windows drivers, without the ndiswrapper, or installing linux drivers) then how do I actually install the adapter itself after? Soryy to be so dense :) thanks for your advice so far.  If this doesn't work I will return to trying the ndiswrapper, but of course I would opt for the quicker solution- human nature ;) *edit  I think the windows drivers are actually installed, because when I went to the disk directory, 'drivers' (only one file in there, the 'setup .exe' which I had run before) and clicked the 'setup' it asked me if I wanted to uninstall the drivers, I clicked no. But how do I install the adapter when I can't find it? The 'link' light that is supposed to light up on the adapter istelf, is not on nor is the 'activity' light, BUT I do se it in the terminal: [B]Bus 005 Device 004: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]
[/B]

---

### Post by eeperson on 2009-03-12
The rt73-common package contains the Linux drivers.  So, now that you have installed that package the Linux drivers should be installed.  

Now try unplugging the your wireless usb stick and then plugging it back in.  Then wait a few seconds and hopefully it will be detected.  Also, make sure that you don't use a USB extension cable, it can cause some problems with this driver.

You won't need the install disk because that probably only contains the Windows drivers.  Ndiswrapper is a compatibility layer that lets you use some Windows drivers on Linux.  So as long as you don't have to resort to ndiswrapper you won't need the Windows drivers.

---

### Post by Lakeside5 on 2009-03-12
Thanks for all the help guys, and the education lol. I will have to see if that guy will either take the device back, or tell me WHY the lights don't come on, or why I can't find it anywhere, when it is listed in the terminal when I do 'lsusb'. grrrrr.

---

### Post by eeperson on 2009-03-12
I have installed this same wireless adapter on Debian.  The light only comes on when data is being transferred.  I am guessing that you the drivers are installed but the networking needs some configuration. What comes up if you type:
```
iwconfig
```

---

### Post by Lakeside5 on 2009-03-12
I get this, eeperson :(, 

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:CD:28:B5   
          Bit Rate=2 Mb/s   Tx-Power=7 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=41/100  Signal level:-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
Don't think this is relevant, but I am still on a wired internet connection (modem connected to a wired Linksys router) and don't have the new wireless router connected here yet, I am still just trying to find this blasted usb adapter!

---

### Post by eeperson on 2009-03-12
The section that starts with 'wlan0' is your wireless adapter.  It appears that it is installed. The rest is network configuration which you will need a wireless router to connect to in order to configure.:D

---

### Post by Lakeside5 on 2009-03-12
Thanks, but I'm still confused because.. I have a wired linksys router hooked up right now, and my daughter's computer used to connect to me wirelessly, so we had a wireless network on here before (may still). The wireless USB adapter plugged in right now is not a Linksys, but a D-link DWL G122 AirPlus G.

---

### Post by eeperson on 2009-03-12
I think you may be already be connected to the your router.  If you wireless network doesn't have a password that may be the case.  Is your wireless network called "linksys"?  If so, try disconnecting your network cable and see if you can connect to a website. You may be all done.

---

### Post by Lakeside5 on 2009-03-12
I just disconnected the cable (one from the computer to the wired router) and couldn't connect to the internet,  As I understood the pamphlet that came with the adapter, I have to install the USB adapter after installing the drivers, and only then can I hook up my wireless router, but I  can't find the wireless USB adapter. Do you think I should disconnect my wired router and try to install  my wireless Linksys N Router?  thanks again

---

### Post by eeperson on 2009-03-12
What do you mean that you can't find the USB wireless adapter?  The USB wireless adapter is the little USB stick that is plugged into your computer.

If you know that the router you are currently working with has a working wireless connection, then it may be easier to try to wireless setup on your computer first and then install the new router.

Can you connect to your current router in your web browser by IP address(the address is usually 192.168.0.1)?  If so, can you do that with the network cable unplugged?

---

### Post by Lakeside5 on 2009-03-12
I plugged it into the usb port, so it is there physically, but I wanted to 'see' it listed under 'places' along with the cd rom, external hard drive etc. Or even a 'found new hardware' etc.  When I click the 'network' icon (two computer screens) it shows two wireless networks- one is my neighbours I guess, not interested in that..and the other one says Linksys. I get two options: connect to hidden wireless network, the   other 'create new wireless network'. lists  'auto Linksys', should I click that?  then it would  ask me for an encryption key for security.
I just remembered why I don't have wireless set up on here when it was before- I recently had ubuntu re-installed on here hard drive was reformaatted) so all my settings were wiped I guess.

---

### Post by eeperson on 2009-03-12
When everything is working properly it won't show up under places.  That is only for files and folders.  Also, you usually won't get a 'found new hardware' hardware notice(unless it something that requires a special driver).  There is a reason for this.  It is because Linux is distributed with most of the drivers that exist for it (As opposed to Windows where you usually have to hunt down a drivers or install them from a disk).  

Because of this, when you have some new hardware you can usually plug it in and Linux will load up a driver and set it up for you.  As a result it is usually not set up to give you as many notifications about new hardware.

Since you can see local wireless networks that means that the network adapter is installed and is working.  I am assuming that 'linksys' is your wireless network.  So, just use your network icon to connect to that one.  Then see if you can connect to your router by IP address.  If you can connect to your router by IP address but can't connect to websites then you probably need to configure DHCP.

---

### Post by anewguy on 2009-03-12
It won't be listed under places, not the USB adapter.  What you need to do is click on the network manager icon on the upper bar (should look like 2 screens on top of each other).  If you click on it and wirless networks show, then it means that your adapter is working.  As mentioned by the previous poster, "linksys" is the name (ESSID) of the wireless network it just connected to by default - it would have nothing to do with the identity of your usb device.  Most routers, if you don't update them, will broadcast ESSID (basically the name of the wireless network they handle) that will be the same as the manufacturer - linksys, dlink, etc.. You will probably need to physically disconnect your direct-connect cable, then look in network manager for your network and connect to it.  If it is not a wide-open network, then you will also need either the WEP or WPA password or passphrase to connect - network manager will prompt for it if the network you try to connect to requires it.

Try looking under network manager then post back.

dave :)

---

### Post by Lakeside5 on 2009-03-12
Aahhhh..that makes sense, now I know a little bit more about Linux.  so, should I take my wired router off (Linksys) and connect my new wireless router up to the modem, but have the wireless router still hooked up to the computer, until I get it configured?  I am assuming that the wireless adapter should be configured for the wireless router, not the existing wired on (Linksys also).*edit*  Network Manager icon> wireless network>linksys> Connection established. You are now connected to the wireless network Linnksys  As well, both green light are on on adapter (solid 'link' and blinking 'activity' light) And I could get into the wireless router, and set user name and passwords (for the router, and also the ones given from my ISP account (for internet connection with them). In setup I chose PPPoE (not automatic configuration DHCP).  But once I disconnect the cable from the computer to the wireless router, there is no internet connection.

---

### Post by eeperson on 2009-03-12
Yeah, setup up your new router (you will have to have to have it connected directly to your computer so you can setup wireless).  Once, it is setup you should be able to connect to it by going to the network icon.

---

### Post by Lakeside5 on 2009-03-12
I appreciate this sooo much eeperson, anewguy, and everyone else.  One last thing you can do for me- cross yer fingers, here goes lol

---

### Post by Lakeside5 on 2009-03-12
Well I'm back, but only because I connected my wired router back up to my computer ;(  when I tried to just use the wireless one, and connect it to the modem and the computer, yes I could connect but as soon as I disconnected the cable from the computer to the wireless router..bye bye internet.  Will try some more and post.

---

### Post by Lakeside5 on 2009-03-12
Just   went to System>Preferences>network configuration and found **Linksys n** listed there, but under 'connected' was 'never', and the**auto Linksys** listed as 'connected now' so u are right, it automatically connected to the connection made before with the wired router (right now the wireless router is  connected to the computer and the modem, so I am confused).  How do I get the Linksys  n to work?

---

### Post by anewguy on 2009-03-12
Try unplugging the hard-wired connection, then either restart the network or just reboot.  Check under network manager then to see if your network is listed - if so, try your browser.  If that doesn't work, then try clicking on your network in network manager.

Dave :)

---

### Post by Lakeside5 on 2009-03-12
OMG :) I guess the trick was, to reboot!  I did as you said, unplugged the cable from the wireless router to the computer, THEN rebooted, and I went to the network manager icon, clicked 'linksys' and am connected. Two weird things though: When it was rebooting. as the desktop icons were coming up, I got a pop up box with a wireless network, asking for key encryption code (wep) but it was for my neighbours wireless network- which of course I don't want and wish it wouldn't show up in my networks list.  So I clicked it off, and clicked on Linksys. I have not completeley configured this though, I guess I have to set a password key encryption, I kind of forget how I did that last year with the wired one, I can just make up a code? thanks again a million times for getting me this far, I was about to shell out for a different adapter/router :)
or pay someone... and I aint rich lol

---

### Post by anewguy on 2009-03-13
Specific instructions for that depend on your router and the level of protection you are putting in.  WEP is fairly easy to set up, but is also easily cracked.  WPA is harder to set up.  You should search for a manual on the net for the specific router you have, perhaps at the manufactures site.  Most manuals are included in pdf format on the installation disk for Windows that came with the router.

Another form of protection is to set which physical machines can actually connect to your wireless network.  This is done by the hardware address of the adapter, not the IP address of the system.  This is done using the MAC address, and usually the router will have a section for setting the allowed addresses.  Some routers show the currently connected wireless devices so you can select it right on the set up screen.

Another thing to remember is 64 versus 128 bit encryption, password versus passphrase, etc..  If you are not familiar with these things, I would suggest you research them a little on the net first.

Some routers let you connect to the "service" port via http to 192.168.1.1 or 192.168.1.0.  They all will require a user name and password [not your logon - this is specific to the router] before you can do anything on the router.  Some routers provide descriptive or help texts in regard to each option.

Dave :)

---

### Post by firefly2442 on 2009-03-13
Yeah, that's good advice.  I would also try to setup restrictions based on the MAC address.  Essentially, a MAC address is a unique identifying value for all network devices (wireless, wired, etc.).  They can be spoofed but it's unlikely that someone would be able to figure out your MAC address.  This way, you can limit your wireless network to only your computer and your friends/family.

---

### Post by Lakeside5 on 2009-03-30
I thought I would stay with this thread, to show what was done before, how I got wireless, what hardware I'm using etc. Well, everything was working fine but of course I had to wreck things when configuring my wireless router, trying to set up a webserver on here.  I must have put in some wrong numbers, because now I can't even get into the router.  I tried unplugging router, pressing the 'pin' in the back, to reset it to factory settings. I can't get into it at  192.168.1.1 or '''''''.100, or ...1.2 etc. I  can only   access network now that I am back to using my wired router.  A 'lsusb' shows my USB D-link network adapter is plugged in, but my wireless router won't show up with iwconfig, or  in the Network Manager.  Does anyone have any ideas to fix this? thanks again.

---

### Post by Talon2 on 2009-03-30
> **Lakeside5 said:**
>   I must have put in some wrong numbers, because now I can't even get into the router.  I tried unplugging router, pressing the 'pin' in the back, to reset it to factory settings.

With most routers you have to have the router turned on and hold the pin in for at least so many seconds for the reset to factory defaults to take place.

After reading this thread again:  Something I have learned over the years when working on my network is that it is best to turn all components off, wait about a minute then bring things back up.  In some situations things need to be turned on in a certain order.  

Good luck.

---

### Post by Lakeside5 on 2009-03-30
Talon2, I followed your advice and was then able to get into my wireless router (yeah, makes sense to leave the router ON when I press the reset button lol). The only change I made to the wireless router was to put in my ISP info (user name/password for my ISP account) and to change to 'PPoE'.  But for some reason I still can't get it to work again, I can't get on the internet (am on the wired one right now).

---

