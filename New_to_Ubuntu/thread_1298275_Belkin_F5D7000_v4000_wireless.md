---
title: "Belkin F5D7000 v4000 wireless"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by darkeye123 on 2009-10-22
Hi there,

I recently installed ubuntu on my desktop computer which uses a Belkin 802.11g wireless adapter. I am having trouble connecting to my wireless network, so I hope you can help me!

**iwconfig returns:**

          lo        no wireless extensions.
 

 eth0      no wireless extensions.
 

 wmaster0  no wireless extensions.
 

 wlan0     IEEE 802.11bg  ESSID:""   
           Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated    
           Tx-Power=20 dBm    
           Retry min limit:7   RTS thr:off   Fragment thr=2352 B    
           Power Management:off
           Link Quality:0  Signal level:0  Noise level:0
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 

 pan0      no wireless extensions.

**lspci returns:**


00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge  
 00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]  
 00:08.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)  
 00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)  
 00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)  
 00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)  
 00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)  
 00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge  
 00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)  
 00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)  
 00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)  
 01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]  
 
 
Also, my wireless network uses a WEP64-bit key, but when I look in the connection settings there is no 64-bit option, only 40 key and 128 passphrase. If you need any more information please let me know! 

Thank you for your time!

---

### Post by 101011010010 on 2009-10-22
Have you tried : System> administration> hardware drivers? 
This post should help with the version 2 driver. [http://ubuntuforums.org/showthread.php?t=197102&highlight=BCM4318 ]("http://ubuntuforums.org/showthread.php?t=197102&highlight=BCM4318")
I hope this helps.

---

### Post by bkratz on 2009-10-22
[quote=darkeye123;8147955
 
 
Also, my wireless network uses a WEP64-bit key, but when I look in the connection settings there is no 64-bit option, only 40 key and 128 passphrase. If you need any more information please let me know! 

Thank you for your time![/quote]




From Wikipedia:

Standard 64-bit WEP uses a [40 bit]("http://en.wikipedia.org/wiki/40-bit_encryption") key (also known as WEP-40), which is concatenated with a 24-bit [initialization vector]("http://en.wikipedia.org/wiki/Initialization_vector") (IV) to form the RC4 traffic key. At the time that the original WEP standard was being drafted, U.S. Government [export restrictions on cryptographic technology]("http://en.wikipedia.org/wiki/Export_of_cryptography") limited the key size. Once the restrictions were lifted, all of the major manufacturers eventually implemented an extended 128-bit WEP protocol using a 104-bit key size (WEP-104).
 A 128-bit WEP key is almost always entered by users as a string of 26 [hexadecimal]("http://en.wikipedia.org/wiki/Hexadecimal") (base 16) characters (0-9 and A-F). Each character represents four bits of the key. 26 digits of four bits each gives 104 bits; adding the 24-bit IV produces the final 128-bit WEP key.
 A 256-bit WEP system is available from some vendors, and as with the 128-bit key system, 24 bits of that is for the IV, leaving 232 actual bits for protection. These 232 bits are typically entered as 58 hexadecimal characters. (58 × 4 = 232 bits) + 24 IV bits

---

### Post by darkeye123 on 2009-10-22
Thanks to both of you. 

I'm sure that your advice will come in useful, but I just need a push in the right direction to get started. Sorry... I'm really new to Linux.

When I go to System>Administration>Hardware Drivers the system searches for drivers, but turns up empty. It says that there are no proprietary drivers installed on this system, and there is no B43 box to check. I'm not sure what to do. I have the manufacturers disc with drivers on it if that is helpful.

Thanks again!

---

### Post by 101011010010 on 2009-10-23
Hello again,  I'm not too sure, (using 9.10beta/rc),but if you go into System> administration> software sources, there should be an option in the Ubuntu software tab that says "Proprietary drivers for devices (restricted)" and another for "Software restricted by copyright or legal issues (multiverse)". The wording might be slightly different on Jaunty, but you should be able to tell which ones (in 9.10, they are the third and fourth options down). Make sure that these are enabled and also ,just in case, under the Updates tab, there is an option for "Unsupported updates", enable this option as well.   Close the window, start the update manager (system> administration> update manager), click on the check button, make sure that nothing you want is going to be removed or anything that you don't installed and update. Hopefully when you have done this, under system>administrator> hardware drivers the driver you want will be there. I hope this helps.

---

### Post by darkeye123 on 2009-10-23
Alright. I went to System>Administration>Software Sources and made sure everything was enabled... including the cd. When I opened Hardware Drivers the Broadcom B43 Driver was there! Yay! 
 
So I clicked on activate, put in my cd and then waited for it. It said downloading and installing, but then the window suddenly closed (no error reports or success messages) and the driver was not activated. I rebooted my computer and it still won't let me install/activate the driver. Is there some way I can do this manually? Perhaps this is because I do not have the computer in question hooked up to the internet (although I think the driver was on the cd.) 
 
Thanks again.

---

### Post by anewguy on 2009-10-23
It is possible that you need to be online for that to work - I've never used it but it did say "downloading" correct?  At any rate, if you have no other access (hard wired) to the net while you are attempting this, it should also be possible to install the driver manually using the command line and a utility called ndiswrapper (and it's GUI'd front end, ndisgtk).  There are some out there who would balk at this, since they think the new b43 drivers are the way to go, but sometimes it just works best to use ndiswrapper and be done with it.  So.....

Check with the package manager and see if it shows ndiswrapper installed or not.  If so, skip this step:

- put in the LiveCD you installed from
- using the file browser, navigate the CD to the main/pool/n/ndiswrapper folder
- click each of the files there (1 for utils and 1 for common) to install them
- navigate the CD to the main/pool/n/ndisgtk folder
- click on the file there to install ndisgtk

Next you need the Windows drivers for your device.  Since you have the CD for it, I would suggest the following first:

- put in the driver CD
- using the file browser, navigate the CD searching for a "driver" or "drivers" or some such thing sub folder.  In this folder, see if there are individual .inf and .sys files.
- if there are individual .inf and .sys files, copy them to your desktop 
- if there is only an executable, try opening it - it may come up in the archive handler so you can extract just the .inf and .sys files.  If not, post back and we'll get them for you.

At this point, you should have the Windows driver .sys and .inf files on your desktop.  Start ndisgtk (you may have to go to a terminal window and type ndisgtk and press enter).  You want to install a new device and point it to your desktop for the driver files.

Once done with that, it might be wise to add to the blacklist so that the other modules don't conflict with your new driver:

- sudo gedit /etc/modules.d/blacklist.conf

- scroll to the end of the last line in the file and press enter a couple of times

- add these 2 lines:

b43
ssb

Save the file, close the editor and reboot.  Then see if your wireless is working.

If you have any questions at all or any problems just post back!

Dave :)

---

### Post by darkeye123 on 2009-10-23
Hello again,

I followed the instructions regarding ndiswrapper and ndisgtk, and the installation went fine.

I opened up ndisgtk and installed the driver located on the manufacturer's install disc. (It never asked for the sys file...) After i clicked on install driver, A message box popped up and said that it could not tell if the hardware was present. As soon as I closed that box, however, the ndisgtk itself said that the harware was present.

When I ran sudo gedit /etc/modules.d/blacklist.conf, A blank text document popped up. I added the two lines to the bottom, but It said I could not save since the file could not be located.

Thanks a lot!

---

### Post by 101011010010 on 2009-10-23
Hello again,
It's a simple mistake. Instead of, > sudo gedit /etc/modules.d/blacklist.conf replace modules.d with modprobe.d. > sudo gedit /etc/modprobe.d/blacklist.confWe've all done it at some point. ;-)
I hope this helps you finally get it working.

---

### Post by anewguy on 2009-10-23
> **101011010010 said:**
> Hello again,
It's a simple mistake. Instead of,  replace modules.d with modprobe.d. We've all done it at some point. ;-)
I hope this helps you finally get it working.

Thanks!  I was thinking of having the OP modprobe ndiswrapper and adding ndiswrapper to modules.d when I remembered ndisgtk seems to take care of that, and sure got the path wrong for the edit as a result :redface: .  Thanks for pointing the OP to /etc/modprobe.d/blacklist.conf due to my error!

Thanks again, and I hope the OP has luck now getting the wireless to work!

Dave :)

---

### Post by darkeye123 on 2009-10-23
Thanks again guys.

So i went looking around on the forums, and i found that by running the commands:

sudo modprobe -r b43 ssb wl
sudo modprobe ndiswrapper

I was able to use iwlist scan to search for networks around me, and they are displayed properly. 

However, I have no clue what to do with the Network Manager thing. I know my bssid, but i think my router's mac address is the same? I'm pretty sure I entered all the info correctly, but it still wont connect... Any suggestions on what I'm missing?

Thanks.

---

### Post by anewguy on 2009-10-23
So your wireless is at least working now, in that you can see wireless networks?  If so, then at least we're past the hard part.  If you see your network listed in network manager, what happens when you try to connect to it?  Do you have MAC filtering on in the router, and if so, I assume that you have this network adapters MAC already in the allowed list?  Do you have WEP, WPA, or anything like that running on the router?  Password or passphrase?  Well, you probably get the idea.....

Let us know:

(1) if you at least see wireless networks in network manager (if not, is roaming enabled?)

(2) what happens when you try to connect?

Thanks!

Dave :)

---

### Post by anewguy on 2009-10-23
BTW - I'm going to be unavailable for a short while (maybe a couple of hours) as I am doing some other updating which requires my browser being closed.  I'll get back to you as soon as I can, and I'm sure someone else will jump in with help as well.

Dave :)

---

### Post by 101011010010 on 2009-10-23
Hello again,
If you type in the terminal> iwconfiglook for the name of your wifi interface i.e wlan0 etc, you'll see > Link encap:Ethernet   HWaddr 00:11:22:33:44:55  (the numbers will be different). The HWaddr is the mac address you need to enter into the mac address option in network manager.
I hope this helps.

---

### Post by darkeye123 on 2009-10-23
I can scan for networks using the iwlist scan thing, but no networks show up in the Network Connections Application. I am not sure what you mean by roaming or how to enable it. :(

Thanks

---

### Post by bkratz on 2009-10-23
> **darkeye123 said:**
> I can scan for networks using the iwlist scan thing, but no networks show up in the Network Connections Application. I am not sure what you mean by roaming or how to enable it. :(

Thanks

Assuming you are using network manager--

Do you have a small icon in the upper right hand corner that looks like 4 or 5 vertical bars?  If so, left click on it and you should see the available AP's. Right click on it and you should be able to configure the network commands specified above. You will have to add a wireless entry named for your network. The rest really is probably pretty self explanatory. If not, post back.

---

### Post by darkeye123 on 2009-10-23
I got it working! :)

I followed bk's instructions and suddenly it works. YES!!!!

I'd like to thank everyone who helped me. You guys are awesome!

Thanks again!

---

### Post by bkratz on 2009-10-23
> **darkeye123 said:**
> I got it working! :)

I followed bk's instructions and suddenly it works. YES!!!!

I'd like to thank everyone who helped me. You guys are awesome!

Thanks again!

Please go to the thread tools above and mark it solved so everyone else can benefit.

---

### Post by anewguy on 2009-10-23
Thanks bkratzsb for finishing up with the OP while I was away!

To darkeye123 - you're welcome!

EDIT:  Forgot to mention, after looking back in the thread, that you actually didn't need to do the modprobe -r to unload the b43 and ssb kernel modules -> having them in the blacklist and then rebooting "should" have taken care of that for you, as the blacklist tells Ubuntu what modules not to load at boot. 

Any way around it, I'm just glad it's all working for you!

dave :)

---

