---
title: "WUSB54G v1 (feisty)"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by xsaint on 2007-04-22
I recently installed feisty and am experiencing total failure at getting my WUSB54G v1 wireless card to work. I have explored every nook of the internet for answers, found many but none work on my system. I will assume I am doing something wrong. Here is my systems status for each of the important pieces that I know to look for.

Blacklisted islsm and islsm_usb

  restarted system

loaded ndiswrapper using synaptic, and the gui (ndisgtk), but i use the terminal for most of this.
installed linksys driver v1, which ndiswrapper -l confirms that wusb54g driver installed
plugged in usb device

now ndiswrapper -l  also shows device present 1915:2234 present (alternate driver: prism54usb)
not sure why this is, since i blacklisted the prism drivers

Now, I can see the device using **lsusb**, which shows device id **1915:2234**
I see the wireless card in **System **-> **Adminstration ** -> **Network**
I see available networks in my neighborhood with signal strengths,

But, I can't connect to my network, or any network available. I'm using the same settings as my router.
     WEP, 64bit hex, shared

When I goto **System **-> **Administration **-> **Windows Wireless Drivers**, it says hardware present: **No**.

So, now that I know the system can identify the hardware, but not associate it with those drivers, what do I do. I tried assigning the wusb54g drivers to that device using:
     ndiswrapper -a 1915:2234 wusb54g

It returns with could'nt create symlink for 1915:2234, driver wusb54g is not installed (properly)!
I have removed the wusb54g drivers and I can still see the available wireless networks, just cant connect.

Anyone out there in the interweb have a similar problem. This is a common usb device, I can't imagine why it shouldnt work out of the box. Thanks

---

### Post by benfrasersimpson on 2007-04-23
Im having exactly the same problem, any help would be greatly appreciated!
Thanks

---

### Post by gwhitener on 2007-04-24
Same boat.  I started with Ubuntu about a month ago, and really like it, but this is killing me.  I have gotten a PCMCIA card to work with ndiswrapper (on my laptop), but my WUSB54g v1...is less than a doorstop in Ubuntu (too light, really, to be useful).  From what I can tell, other people have gotten the thing to work, but there seems to be no definitive install procedure available (at least not centrally located, and the Dapper instructions don't work for me).

To echo what is posted above, and what I have also done:

Using ndiswrapper, I have also installed the drivers up to the point where I can see hardware present, driver present.  However, I have never seen any available networks.  This might be related to a different problem which I never resolved in Edgy, where the network icon never showed up in the top right corner.

However, now, in Feisty, that appears automatically, but no wireless option.

Hmmm.  I still have not had the time to do as another forum post indicates, which is to blacklist certain drivers, install ndiswrapper, THEN plug in the USB WLAN.

Can anybody comment?  It seems like this is a real problem for a lot of users, and that this is the place to come for help (I have considered moving to other Linux distros, heresy perhaps, but they all seem to point here for install advice, so I figure I am in the best spot).

Finally, and this is where my total noobness and OS pedigree will shine through, isn't this a big enough problem that someone competent (definitely not me) could put together a small installation wizard of sorts?  I know, I know, but this is motivated by a month of frustration, so please take that into account when flaming me.

Sigh.  I hope someone can help out.  Were I not so cheap, I would just try to find a compatible device.  At any rate, any help would be greatly appreciated.

---

### Post by gwhitener on 2007-04-25
Just to echo what is above.  Installed ndiswrapper packages, including the gui front end, installed drivers for version 1 (downloaded from Linksys, when I tried the other drivers mentioned elsewhere from another vendor, it didn't work, though that was in edgy).

I have not blacklisted anything yet, but that will be my next move.

Have the people on this thread had any success with blacklisting the Ralink drivers?  Some people claim that helps.  I will keep fooling around, and report any progress, if any.

Cheers.

---

### Post by benfrasersimpson on 2007-04-25
OK, i have managed to get it working.
First of all i added all of the following to my /etc/modprobe.d/blacklist file

blacklist bcm43xx

blacklist rt2500

blacklist rt2561

blacklist rt25xx

blacklist rt2570

blacklist r8187

blacklist r818x

blacklist NET2280

blacklist ISL3886

blacklist islsm

blacklist p54u

blacklist islsm_usb

and then rebooted the computer

THen on a different PC, downloaded [http://packages.ubuntu.com/feisty/net/ndisgtk](http://packages.ubuntu.com/feisty/net/ndisgtk)

Installed that, from the file browser, and all its dependencies installed automatically.
I then installed the inf files, although the driver did not appear in the Windows Wireless window, however when i typed ndiswrapper -l it said it was.

I then disabled wireless roaming in Network, and put in hte details of my network, and then it worked

Hope this helps somebody.

---

### Post by gwhitener on 2007-04-29
This worked for me.  I didn't do any work on the issue until after I saw the last post.

I opened the blacklist file, added the entries, and immediately the update manager started, and life was good again.

There are still issues, of course, but the good news is I am once again wireless, and fully functional in Ubuntu.  I still see no networks available around me, and the icon for network configuration does not recognize that I am connected.  Other than that. booya!

Thanks a ton!

I will link to this thread in the sticky at the top of the Wireless forum.

Cheers.

---

### Post by AmyRose on 2007-05-01
Ndiswrapper? >.> Ndiswrapper should be a last resort, not the first thing to try.

I did this instead: [http://ubuntuforums.org/showpost.php?p=2570962&postcount=3](http://ubuntuforums.org/showpost.php?p=2570962&postcount=3)

Works and doesn't use ndiswrapper. Oh, and delete anything you installed with ndiswrapper.

---

### Post by gwhitener on 2007-05-01
Amy-

I understand that some people have objections to using ndiswrapper, but I think that for the Prism devices it is the only thing that works reliably.  That said, I did not go through and try blacklisting several things first, in different combinations, to see if they were interfering with the reverse-engineered drivers.

From what I understand from the forums, Ralink based devices seem to work much better out of the box, in general.

Additionally, the WUSB54g is a USB based device, which also seems to add some trickiness to the whole thing.

Do you have experience with this stuff?  I am new to Ubuntu, and Linux in general, so if there is a better way, and I am talking here in a practical sense, to get my USB dongle working and me connected to the interweb, I am all ears.

Cheers, and thanks for the feedback.

---

### Post by mcook2 on 2007-07-07
I guess this'd be a sort of "here's my status" report on this topic ....

I have a WUSB54G v1 - it has USB id 0019 2234 and uses a Prism chip or chipset - not Ralink.

I am running Feisty x86-64 AMD so can't use ndiswrapper or the Linuxant solution as drivers have to be 64-bit and there aren't any - at least not yet, altho' there is a guy over on a Linksys forum who is working to produce Windows 64-bit drivers for various "legacy" WNICs including this one. 

Out of the box, WUSB54G v1 seems to get recognized using the native prim54usb driver, and after uninstalling network-manager and fiddling around with WICD and iwconfig I was able to get wlan0 going - at least unencrypted to start with. 

It'll work for a bit, but slowly, and then it seems to run out of buffers - for example ping fails with "ping: sendmsg: No buffer space available" and about the same time I start seeing these messages in my kernel log:   "kernel: [  261.193222] wiphy0: unknown frame RXed (0xcf)".  It'll load a couple of web pages and then it hits the wall.

Reading some of the many other forum entries about this here and elsewhere I was surprised that I got it to work at all.

I'm sort 1/2-way thru writing up a more complete post to include lsusb and lsmod output as well as dmesg and syslog. However, it's lot of stuff and I'm not sure if it's really worth the effort as there seem to be various bug reports relating to prism and network-manager. I'm sure it'll work one fine day and it's not as if I need to get it working to send e-mails to Grandma or please my boss or anything like that. My wires are working fine.    

Along the way I got rather confused among all the different Prism54 web links and alternate firmwares to try but I always seem to end up getting the same results if it works at all, and right now I have gone back to running "vanilla Feisty" as far as i can tell, using the distribution levels of the isl* firmwares with prism54usb and prism54common NOT backlisted.

I'll let you know if I find out anything else - I'm thinking it could just be that I need to set some special config parms someplace -  any suggestions most welcome and I will sure try them - meantime anyone interested can let me know here if they want all those logs and stuff.

Enjoy the good weather!

---

### Post by be4truth on 2007-07-11
I connected a Linksys WUSB54G Ver.4 to my xeron laptop and installed Ubuntu Mint. After the installation it worked out of the box. Haven't checked with encryption but otherwise works fine.

---

### Post by L19L91L on 2007-07-20
> **xsaint said:**
> 

So, now that I know the system can identify the hardware, but not associate it with those drivers, what do I do. I tried assigning the wusb54g drivers to that device using:
     ndiswrapper -a 1915:2234 wusb54g

It returns with could'nt create symlink for 1915:2234, driver wusb54g is not installed (properly)!
I have removed the wusb54g drivers and I can still see the available wireless networks, just cant connect.


I was able to do this last part and it says that wusb54g is already in use for 1915:2234. I do not see any wireless in the networks though. It only shows the settings for wired. I blacklisted the said drivers here and I'm still not getting the icon. I'm going to try the ndiskgtk now.

---

### Post by L19L91L on 2007-07-20
I'm getting an error when I try to install ndiskgt. It says "Error: Dependency is not satisfiable: ndiswrapper-utils-1.9" Can anyone help me? I believe that my ndiswrapper is installed. Thanks.

---

### Post by mcook2 on 2007-07-22
> **be4truth said:**
> I connected a Linksys WUSB54G Ver.4 to my xeron laptop and installed Ubuntu Mint. After the installation it worked out of the box. Haven't checked with encryption but otherwise works fine.

Good for you!  But this thread is about WUSB54G v1.  It uses an older, different chipset to the v4 model, and so uses different drivers.  

Most of the stuff I've read about the v1 card suggests it's easy to get it to work on x86 architecture using the original Linksys Windows XP driver with ndiswrapper.  

However, on x86-64 architecture, you need a 64-bit driver and the only ones available seem to be from  prism54-islsm and softmac. 

I'm still trying to figure out how to get and apply all the latest patches to recompile these successully, and it looks like I probably need a newer kernel than my Ubuntu Feisty 7.04 2.6.20.16-generic amd64, which presents a whole new adventure all by itself.

Sure is interesting,

M.C.

---

### Post by mcook2 on 2007-07-22
> **L19L91L said:**
> I'm getting an error when I try to install ndiskgt. It says "Error: Dependency is not satisfiable: ndiswrapper-utils-1.9" Can anyone help me? I believe that my ndiswrapper is installed. Thanks.

Looking back at my notes I believe I had to upgrade ndiswrapper 'cos Feisty ships with an old version.  What level is your ndiswrapper?  

Also, ndiswrapper-utils 1.9 is a separate package, and it looks like you do not have it installed? Check using System -> Administration -> Synaptic Package Manager.

The last note I made was that I uninstalled ndisgtk and its dependencies, but it had seemed to work for me using:

> Commit Log for Mon Jun 25 01:15:33 2007
Installed the following packages:
ndisgtk (0.6-0ubuntu3)
ndiswrapper-common (1.38-1ubuntu1)
ndiswrapper-utils-1.9 (1.38-1ubuntu1) 

This was before I realized that WUSB54G v1 is not a Ralink device, and so does not (cannot) use the rt* driver(s).  You have to download the drivers from Linksys (any version will do) and after extracting them use the WUSB54G.inf file in the WUB54Gv1 folder with ndisgtk.

This was before I ran into my own personal "showstopper" on x86_64: "'Bad magic': not a 64-bit driver."

---

### Post by Roswellgrey on 2007-08-15
Just installed a V1 on a new / clean install of Fiesty.

Using the latest ndiswrapper from sourceforge, 
the default install of wpa_supplicant and 
after blacklisting the drivers as detailed near the top of this thread, 

I have to say it works extremely well (even with WPA).

Thanks for the info here - it helped a lot :)

---

