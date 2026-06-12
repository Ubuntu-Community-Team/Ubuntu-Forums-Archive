---
title: "wireless adapter help?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by bytescribe on 2009-01-04
Like many others in this sub-forum, I'm a complete noob.

I am also a noob who is hoping to work with a LinkSys wireless USB adapter model WUSB54GC.

At first my bf and I set up the wireless router (model WRT54G2) and tested the USB adapter without configuring anything, as we had read someone was able to use the adapter "out of the box."

Well, it worked, but only for two or three hours. Once we tried to download something from the Synaptic...poof! No wireless connection. Then we found out that we needed the ndiswrapper plus the necessary driver. (I'm running Hardy Heron with a five-year-old 32-bit Intel processor, btw. And yes, I know that the chipset for my adapter is Ralink. ;-))

All well and good, but Quentin (my bf) had to download the necessary files and such and burn them onto a CD just so I could install them without having to put up with my parents' slightly dysfunctional Windows machine.

Quentin placed a couple of "how-to" HTML files on the disk, but because the instructions are more for experienced folks and not for noobs, I am having a very difficult time understanding what I need to do first, and how, exactly, to do it. 

And I'm the sort, unfortunately, who needs super-detailed step-by-step instructions. I went and looked up *some* stuff, and I'm that much closer to understanding the basics of networking (interesting stuff, this TCP/IP biz)...but that still doesn't solve the essential questions of:

HOW exactly do I install the files from the CD my boyfriend burnt? *(I extracted them from a zip folder he made onto the desktop. One HTML file he found said that the driver .EXE should be "unpacked" or unzipped[which is it?] into the ~home directory. But since I received the ndiswrapper, etc on a  CD-RW from my bf, I can tell there's going to be some extra steps--and I still don't completely know my way around Ubuntu yet. It all adds up to serious confusion.*

These are the files in question:
**ndisgtk_0.8.3-1i386.deb** (this is a file Quentin found as a result of his own small bit of research in finding the necessary files)
**ndiswrapper-common_1.50-1_all.deb**
**ndiswrapper-utils_1.9_1.50-1ubuntu1_i386.deb**
**WUSB54GC_20051228_dr.exe**


What precise steps do I need to take with these files? And I mean baby steps, if you all can provide it...I'm a smart woman...but a noob, nevertheless. And let's put it this way: I don't like screwing up. :-P

My two other options are these:

Buy a Linux-compatible adapter from Linux Emporium (a UK site), something I'm very tempted to do, which might end up being less of a headache...

OR

Completely unhook my computer, take it over to my bf's next week and have him configure it for me. 

I'd like to try configuring it myself, first though...just to see if I can do it...but I'm going to need assistance. :-P

Sorry if this post was long, but I figured the more info you all have about my situation, the better.

Blessings,
Kat ^.^

---

### Post by Michael.Godawski on 2009-01-05
hey bytescribe,

perhaps we manage to set up your wlan.
Have a look at this first:


[LIST]
[*][http://godawski.oxyhost.com/solvingwireless.html#ndiswrapper](http://godawski.oxyhost.com/solvingwireless.html#ndiswrapper)
[/LIST]
The deb files you have on the cd are not wrong but let's try to install ndiswrapper from the cd first.
Follow the instructions posted above, and report back when you succeeded or hit the wall.

To extract an exe file in Ubuntu you need the tool called cabextract. I do not know if it is on the Ubuntu CD. But you need only the inf and sys files from the wlan drivers. So I would extract them in windows first, see what files there are, and move only the inf and sys files to your Ubuntu machine, on cd or usb stick.

When you read the instructions posted above, there is a section describing how to change the source to install ndis from the cd; when you have done this you can try to install also cabextract from the cd.
```

sudo apt-get install cabextract
```To extract the exe open the terminal and navigate with the command cd to your Desktop where the folders probably are.

```
cd Desktop
```With the command ls you can list all files on the Desktop.
```
ls
```now run this to extract the exe:
```
cabextract WUSB54GC_20051228_dr.exe
```As I said we need this cabextract tool only to extract the drivers from in exe in Ubuntu.
You can extract the exe in windows more easily and move the extracted files to Ubuntu.

i see just now that my post is not very organized. :D

---

### Post by bytescribe on 2009-01-06
Hi Michael...well, your link looks promising, though the Ubuntu CD I need is at my boyfriend's house. 

As for looking at things via Windows, there is a small issue I must present to you.

For one thing, my dad is quite protective of his Windows machine, and does not like me to change much of anything without asking him, even though he probably wouldn't be able to comprehend what I would be attempting to do in the first place...just because his interest is in pipe organs, not computers. :-P

Secondly, his CD drive is messed up, so I cannot look at anything via CD/DVD. :-( 

Thirdly, his computer is online downstairs, and my computer is offline upstairs. :-P 

Anyway...you helped me unlock one possible clue, Michael, though like I said, the Ubuntu CD I need is at my boyfriend's...

I've subscribed to my own thread, so if you or anyone else make another reply, I'll be able to respond fairly quickly, despite my job hunt. :-)

BB,
Kat--the uber-noob.

---

### Post by rosspoko on 2009-01-08
Since your linux machine is not online, getting cabextract wont be easy.  Instead, as Michael suggested, you should probably use the windows machine to extract the exe file.  Since the cd drive is busted, you could use a flash drive.  Use the linux machine to move the  WUSB54GC_20051228_dr.exe file to the flash drive (just drag and drop), then plug the flash drive into the windows machine and click the exe file. It will probably run a self-installer.  Make sure that you set the installation path so that it extracts the files back onto the flash drive instead of to a system folder.  Now you can take the flash drive back to the linux machine, and copy the files to a folder, probably on your desktop or in your home folder.  

Next, get ndiswrapper running if you havent already.  clicking on the ndiswrapper-utils_1.9_1.50-1ubuntu1_i386.deb and ndiswrapper-common_1.50-1_all.deb files, in that order, should bring up straightforward graphical installers for each one.  You can also install ndisgtk_0.8.3-1i386.deb if you want, it is a graphical tool to make the installation more user friendly.  If you do install it, you can ignore the next paragraph and instead use the graphical tool at System - Administration - Windows Wireless Drivers, which is shown in the link from Michael.  

After ndiswrapper is working, open a terminal (its in the programs menus somewhere) and navigate to the directory where the drivers are.  If the drivers are on your desktop, this is done by typing ```
cd Desktop
``` as Michael said. Once you are in the right folder, type ```
sudo ndiswrapper -i infFile.inf
``` where infFile.inf is the name of the actual inf file for the driver.  It will ask you for your password.  after it finishes, run ```
ndiswrapper -l
``` to check to see if the driver installed properly. 

If the driver installed correctly, whether in the terminal or in the graphical tool, then you should now follow the steps in section 3.5 of

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

which is the first link on Michael's site.  

This should get your card installed.  Configuring it is usually fairly automatic, if you have trouble reply back here or check the various links
here and on Michael's page for tips.

---

### Post by bytescribe on 2009-01-10
Thing is, I don't have a card, I have a USB adapter.

I appreciate the extra info though...it will help me with my research.

A flash drive is something I probably should consider getting rather than trying to use a CD-RW.

BB,
Kat ^.^

---

### Post by bytescribe on 2009-01-12
Hi, again...

Michael: I went to extract the files from the Windows driver .exe file. Once I extracted that, I went into the "drivers" folder, and found these two files:

rt73.inf (Setup information)

and

rt73.sys (System file)

Are these the .inf and .sys files I need? They're the only ones I see with such extensions in the drivers folder. I also looked in the Utilities folder and saw nothing like it. So I am assuming the above files are what I need.

Not Feeling Quite So Scared,
Kat ^.^

---

### Post by bytescribe on 2009-01-12
I managed to use the ndisgtk GUI to install the .inf...but how do I install the .sys files?...also, other documentation says I need the .bin files, but the first link you posted says I did not need this.

Also, I plugged in my USB adapter, restarted the ndisgtk GUI and it says that "hardware is present." However, I ran the iwconfig command, and I got the following:
[B]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"gallegos"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:29:A9:83:2E   
          Bit Rate=2 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management: off
          Link Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/B]

Also, which free drivers do I need to "blacklist" if any? The documentation from the second link provided (help.ubuntu.community/WiFiDocs/Driver/Ndiswrapper), mentions the b43 and b43legacy for 8.04(Hardy Heron), but there's another driver that this site recommends for blacklisting, called "ssb." Also, in the documentation, the section on blacklisting comes before the one about downloading the drivers for one's specific chipset. So, did I need to blacklist the free drivers before trying to install the .inf file? 

Also, do I need to blacklist the free drivers before trying to install the .sys file? Because when I tried to install the .sys file using the ndisgtk graphical interface, I got a message saying the driver was invalid, and only seemed to request the .inf file (rt73)...Again, in my previous post, the only .inf and .sys files I saw were the rt73 ones I found in the "driver" folder when I extracted the .exe driver files. I know because I checked the property information of pretty much all the files and documentation

Hope to hear from you all soon...I feel like I'm halfway there, but not sure of the next steps...

BB,
Kat ^.^

---

### Post by bytescribe on 2009-01-16
Bump!

Hey...anyone there? I still rather need some help..

BB,
Kat ^.^

---

### Post by rosspoko on 2009-01-16
All that you need to install is the .inf file, as long as the .sys file is in the same directory as the .inf file ndiswrapper will find it (though it wont say that it did).  So you've done the installation successfully.

As far as the output of iwconfig, that all looks fine.  wlan0 is the wifi connection's name, and it already appears to be connected to a network.  lo and eth0 are the loopback interface and the ethernet interface respectively.  They will never show interesting output for iwconfig because they are not wireless devices.    

For the blacklisting, it might not be necessary to blacklist all 3 drivers, but you might as well just to be sure.  It does not matter that you installed the ndiswrapper driver before blacklisting the other drivers, but I believe you will need to restart your computer for the blacklist settings to take effect.

---

### Post by bytescribe on 2009-01-16
Thanks, Ross..

Well, I put both the .inf and .sys files on my desktop, so if that is considered a directory, then okay...the installation *was* successful...

Now...to attempt the blacklisting, which I will do when I get back home. 

Cross your fingers for me and wish me a bit o' luck...;-)

BB,
Kat ^.^

---

### Post by bytescribe on 2009-01-19
I am about to go and do the blacklisting stuff so my wireless connection can work, finally.

However, there are a few last pertinent questions I must ask:

When (and if) my blacklisting of the Linux drivers is a success:

What, if any, additional steps do I need to take 
to complete the process of getting and staying connected, such as "setting up the WLAN network" or setting WPA passcodes?

I'm asking particularly about the security stuff, because I took a look at the GUI window that mentions setting WPA passcodes and the like, and I don't know anything about how to set those up correctly, or what they're really about. Are they just for places like libraries, schools(universities, espec.) and other WiFi hotspots, where downloading ANYthing at all can be harmful to a really large network, or is it a must-do for Wi-Fi even on one solitary PC? 

If I set a WPA passcode, what does it do? Does it prevent me from accessing things like torrent sites? Or does it simply prevent hackers from getting into my system and fouling it up?

I would love some help on this, too.

BB,
Kat ^.^

---

### Post by bytescribe on 2009-01-19
Okay...Mercury is definitely retrograde! :-P

I tried to post a question or so about WiFi security and other detailed steps to completing my "getting wireless" quest.

And it hasn't shown up in the actual thread...

Glitch?

---

### Post by bytescribe on 2009-01-19
Never mind...I see it now...I guess it just took a few minutes for it to appear...*blush*

---

### Post by bytescribe on 2009-01-19
Okay...I went and took a look at the blacklist document in modprobe.

1)I assume I have to log in as root to edit the blacklist. If so, how do I do this with the sudo command?

2)I found some stuff that I found a bit confusing. For instance, the website I printed out that tells how to blacklist says that the bcm43xx driver from earlier vers. of Ubuntu (before Heron) was replaced by b43 and b43legacy. I have the b43 and ssb drivers but not the b43legacy. (The bcm43xx was already blacklisted, as I expected.)

There's also a driver called p54pci. Since I do not have a PCI card for wireless, but a USB dongle, do I not need to worry about this particular driver?

Anywho, I'll copy and paste what I do have:

[B][I]# replaced by b43 and ssb.
blacklist bcm43xx[/I][/B]

Can I assume that because the b43legacy driver is not listed, I don't need to worry about putting it in the blacklist?

And can I safely assume that once I've blacklisted the b43 and ssb drivers, and rebooted the computer that my adapter will pick up the signal and connect to the 'Net?

---

### Post by bytescribe on 2009-01-19
Well, I plunged in, found the sudo command for blacklisting the necessary drivers (assuming i did not need to mess with b43legacy) and I rebooted...

But I'm still not connected, unless I try hooking into the roaming wireless networks that pop up when I click on the network icon ("gallegos," "The Smiths")...but these poop out after a couple minutes. 

When I choose the "manual" configuration (and put in my desktop password to authenticate any changes), it shows stuff like "essid," "DNS" etc. Stuff I've no clue how to configure yet.

Here is my current iwconfig results (and subsequent questions) after blacklisting  :

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

When I click on the 'linksys' name in "Network Settings," (under wlan0 properties) it requires a password, but I don't know if there's a pre-set password created by Linksys, or if I have to make one up. If I have to make one up, does it already get encrypted by the security system, or do I have to keep on hand a reaaaaallly long password? :P

Secondly, under the "Connection Settings," there's listings for:

Configuration (static IP address)
IP address: (IP addy here)
Subnet mask: (mask number goes here)
Gateway address: (Gateway address obviously goes here.)

Whose IP, Subnet mask or gateway address do I have to use: mine or my parents' (since their ethernet cable is hooked into the router Pop bought and I am riding on THEIR router's radio waves)?

One interesting thing I noticed (and I know this is a completely "noob" observation, but I just want to give as much info as possible) was that when the "enable roaming" button is checked, I notice other networks like "gallegos," (which I tried to connect to, and it worked for a couple minutes then pooped out. Must be a different router down the street that I'm too far away from), "The Smiths" ("Matrix," anyone?) and "linksys" (which I assume is my parents router), and my own config screen is blanked out. 

But when I disable "roaming," by unchecking the box, my config screen lights up...and all I see is the "linksys" network (and "The Smiths"), the former of which requires a password. 

I know...long post...but I'm reaaaaally close to understanding some things about wireless (from a PC anyway..I've yet to config a laptop in the future)...so please bear with my incessant questions. :confused:

BB,
Kat, Who Really Wants to NOT be a Noob anymore ^.^

---

### Post by Lostin60's on 2009-01-19
> **bytescribe said:**
> 

But I'm still not connected, unless I try hooking into the roaming wireless networks that pop up when I click on the network icon ("gallegos," "The Smiths")...but these poop out after a couple minutes. 

When I choose the "manual" configuration (and put in my desktop password to authenticate any changes), it shows stuff like "essid," "DNS" etc. Stuff I've no clue how to configure yet.

BB,
Kat, Who Really Wants to NOT be a Noob anymore ^.^

Hey Kat! Great attitude, you'll be a super Ubuntuer one day. I, too am a noob, and I too just keep plowing ahead until I get where I am going.
I think the first thing to do is run 

```
sudo lshw -C network
```
you'll get a ton of return, but this is where you want to look.
```
 *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0b:03.0
       logical name: wlan0
       version: 03
       serial: 00:14:a5:14:76:70
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       [COLOR="Red"]configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom[/COLOR],12/17/2005, 4.10.4 ip=192.168.2.2 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```
If the area in red is the legacy driver, then blacklist it. If it shows your driver, you should be fine. If you are showing connections when you right click the network then, you should just need to configure your own network. I already had mine configured when I installed Ubuntu. (dual booting with Windows), so I need to check a couple things. But from all appearances, that is all you need. The connections you are getting on for a few moments are unsecured networks of your neighbors. Type in the ip of your router. You will get to a configuration page(s). You set a wep security password there. Write it down. You can find you SSID there, along with any info you need. From there I think you will be able to do it. I'll check back to see where you stand. BTW, your IEEE should be 802.11 for wireless. 
Sorry, just noticed something else in your post. Your router has assigned you an ip, same as your Dad's except for the last 3 numbers. Use yours, as that is how the router knows you're you. Subnet mask is prolly 225.225.225.0, although Ubuntu may modify that. It may also modify your ip. Actually, I think it gives you an "ubuntu ip" which points to  your actual ip. Don't let all this daunt you. At this point you only need to know what to put where. You don't need to know why or how it works. As with any command line, you just know what it does, but not how. You'll learn the hows as you go. Try this
```
ifconfig
```
and these excerpts are what you want to see.
```
lo        Link encap:Local Loopback  
          [COLOR="Red"]inet addr:127.0.0.1  Mask:255.0.0.0[/COLOR]

```
That is what ubuntu assigns, I think, and it points to your actual info. Now that's just my idea of what it does. The point is, you don't use it for your internet config.
```
wlan0     Link encap:Ethernet  HWaddr 00:14:a5:14:76:70  
          [COLOR="Red"]inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0[/COLOR]

```
This is your actual router info, and the first ip address is what you use for your internet config. Also, change the last number to 1 and that is your router ip address. Type it into your address bar, and it will take you to the router config page(s).

[COLOR="White"]aa[/COLOR]

---

### Post by bytescribe on 2009-01-20
Well, here is something interesting:

I am sitting upstairs, in my room, currently "tuned into" one of the wireless signals: from my neighbor "gallegos." So far, it has not pooped out, so hopefully I can post this before they log off for the night. :P I ran the command you recommended, Lostin60s, and here is the bit of information you said I should look for:

```
*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:21:29:6a:f0:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt73 driverversion=1.52+Linksys, A Division of Cisc ip=192.168.1.101 link=yes multicast=yes wireless=IEEE 802.11g
```

This IP that appeared after the driver information:

*ip=192.168.1.101*

Would this be considered the IP address of the router, or my unique static IP for my computer? 

Because when I discovered I was tuned into the 'gallegos' waves, I found this "active connection" information, which I am placing here:

IP Address: 192. 168.1.101 (which I am assuming is either my static IP or the router IP (unless, because I am doing wireless, they are one and the same.)

Broadcast address: 192.168.1.255 (which I am assuming is the 'gallegos' signal I seem to be receiving with some success for the time being. Or is it the broadcast address from MY router?)

Subnet mask: 255.255.255.0 (this was easy to figure out. :P)

Default Route; 192.168.1.1 (I am assuming this is my gateway IP)

Primary DNS: 12.207.232.47

Secondary DNS: 12.207.234.32
(These two DNS's I know are mine, not "gallegos." :P)

Okay, you also mentioned a WEP password. I did some research on the current wireless standards with the IEEE 802.11g, and it seems that WEP is a lot less secure than something I read about called WPA. In fact, because the wireless setup my dad purchased for me is pretty much new, off the shelf, it has both WEP and WPA standards. 

In fact, I think the default password setting might for "WPA/WPA2 personal" on wireless routers newer than say, five years old, because according to the information I printed out from Wikipedia about IEEE 802.11, the previous security standard for wireless, called Wired Equivalency Privacy, is, as of 2004, considered less secure than new standard called WiFi Protected Access.

Reading further, the WiFi Alliance **"refers to their approved, interoperable implementation of the full 802,11i *(though most routers might say 802.11g as mine does)* as WPA2, also called RSN, or Robust Security Network. 802.11i makes use of the Advanced Encryption Standard (AES) block cipher, whereas WEP and WPA use the RC4 stream cipher."**

Goddess, but I love Wikipedia! ;) I don't know if all that made sense to you, but just thought I'd share what I've learned, just as you've shared with me what you've learned.

Anywho, since you mention that I need to set my own password, whether it's WEP or WPA, can it be a regular password, such as the one I use for this and other sign-in sites, or what? Am I correct in assuming that I can do just that, because the router will encrypt my password?

> This is your actual router info, and the first ip address is what you use for your internet config. Also, change the last number to 1 and that is your router ip address. Type it into your address bar, and it will take you to the router config page(s).

I tried typing in the address I found when I ran the ifconfig command, into my firefox address bar and it said "connection not found." Could the reason be that I am tuned into my neighbors' radio waves and not my own Linksys router?

Looking forward to your reply...

BB,
Kat, Who's Pulling Away from the Shores of Noobville. ;)

---

### Post by Lostin60's on 2009-01-20
Check your messages...heheh
[COLOR="White"]aa[/COLOR]

---

