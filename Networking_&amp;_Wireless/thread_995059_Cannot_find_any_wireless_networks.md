---
title: "Cannot find any wireless networks"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by Scarlath on 2008-11-27
Hello!

First of all, I decided to create this thread as this section of the forum fits my problem more than the Installation & Upgrade board. If someone can merge the threads, feel free to do so. The original thread can be found [_here_]("http://ubuntuforums.org/showthread.php?t=992725").

**Anyway, to the problem:**

My current setup of this computer:

[LIST][*]Dual-boot between Ubuntu 8.10 and Windows XP
[*]1024 MB RAM
[*]Intel Pentium 4 CPU, 3.00 GHz (2 CPUs)
[*]nVIDIA GeForce 6200LE Graphics Card, 256 MB
[*]**Wireless Network Card: D-Link DWL-G122 (rev C1)**[/LIST]
When I first got the Ubuntu 8.10 installation CD I ran the live enviroment to check if everything was working properly - and it was! My wireless USB network card was recognized out-of-the-box (which I've also read about that it should be) and I could happily surf the web while inside the Live CD.

A few days later I decided to install the OS itself, everything went fine except that after the installation, I can no longer seem to find any network at all! Which seems very strange seeing as it worked fine while running the live enviroment.

And finally, today, while haven't find any solutions I boot into the live enviroment again, only to find that it is no longer working in there either. Which is even stranger as it worked before under the live cd.

A few commands in the terminal gave me this information (told to do this in the old thread):

```
ludvig@ludvig-desktop:~$ lsusb
Bus 005 Device 002: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]
```
```
ludvig@ludvig-desktop:~$ lsmod | grep -i ether
ludvig@ludvig-desktop:~$
```
```
ludvig@ludvig-desktop:~$ lsmod | grep -i usb
rt73usb 30464 0
crc_itu_t 10112 1 rt73usb
rt2x00usb 18816 1 rt73usb
rt2x00lib 36224 2 rt73usb,rt2x00usb
mac80211 216820 2 rt2x00usb,rt2x00li
usbcore 148848 5 rt73usb,rt2x00ubs,ehci_hcd,uhci_hcd
```
Please note that I've had to manually type these command outputs over to my Windows boot where the connection *is working* to post them here. Thus, there may be typoes.

I tried doing [_this_]("http://pennsylvania.ubuntuforums.com/showpost.php?p=5971799&postcount=14") to solve it. However I couldn't copy or paste any files from the cd or from any partition (or I might just be doing it the wrong way, who knows... I'm a complete newbie to Linux (Ubuntu)). Besides, the only file I could find in /lib/firmware/ was rt73.bin, there was no rt73usb.bin file. I also used the search tool which came back with no results.

Could it be so that I'm just missing some simple setting to get all of this working, a button to push or a box to click, just like that or do I have to go through some rather complicated process (which I'd rather avoid...)?

Any help is highly appreciated, I really want to get this running so I finally can get rid of Windows. ;)

Thanks in advance.

EDIT: Just realised that the title may have been badly chosen seeing as I dont know if the network card is even working under Ubuntu right now (it should be though)... either way, you understand that I have a problem nonetheless!

---

### Post by Scarlath on 2008-11-28
Anyone?

---

### Post by Scarlath on 2008-11-28
After trying and trying to find a solution, I'm sending this back to the first page while I try to get some rest. See you all later and thanks in advance.

---

### Post by Scarlath on 2008-11-29
Still no reply? :(

---

### Post by pipesmoker on 2008-11-29
Patience is a virtue?

---

### Post by gnusci on 2008-11-29
Please post the output of the following commands:

$ iwconfig > ~/Desktop/wlan.txt
$ ifconfig >> ~/Desktop/wlan.txt
$ dmesg | grep rt73 >> ~/Desktop/wlan.txt
$ sudo lshw -C network >> ~/Desktop/wlan.txt

Pay attention that the first one use only one "**>**" the other ones two "**>>**". Then post the contents of the **wlan.txt** file that you will find on your desktop.

---

### Post by Scarlath on 2008-11-29
> **pipesmoker said:**
> Patience is a virtue?

Yeah ;)

> **gnusci said:**
> Please post the output of the following commands:

$ iwconfig > ~/Desktop/wlan.txt
$ ifconfig >> ~/Desktop/wlan.txt
$ dmesg | grep rt73 >> ~/Desktop/wlan.txt
$ sudo lshw -C network >> ~/Desktop/wlan.txt

Pay attention that the first one use only one "**>**" the other ones two "**>>**". Then post the contents of the **wlan.txt** file that you will find on your desktop.

Here you are:
```
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=5 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      Link encap:Ethernet  HWaddr 00:16:e6:4b:63:df  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:a4:28:ed  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-E9-A4-28-ED-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[   13.761204] Registered led device: rt73usb-phy0:radio
[   13.761236] Registered led device: rt73usb-phy0:assoc
[   13.761265] Registered led device: rt73usb-phy0:quality
[   13.761766] usbcore: registered new interface driver rt73usb
[   25.764913] firmware: requesting rt73.bin
  *-network
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 19
       serial: 00:16:e6:4b:63:df
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:e9:a4:28:ed
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7e:25:75:0b:52:d6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Uh.. If I'm not completely wrong then it seems the first command was lost in the text file, am I right?

---

### Post by gnusci on 2008-11-29
Wait, you have no setted up any ESSID:

[B]wlan0     IEEE 802.11bg  ESSID:""  
Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated[/B]

How did you configure your network?, Using the Network Manager?

---

### Post by Scarlath on 2008-11-29
When I first tried it out in the Live CD I was able to choose from different networks in the network manager thing in the upper "task bar" in Ubuntu. Choosing my network made it 'just work'. I did not have to do anything else other than select which network I wanted to connect to.

When I installed Ubuntu though, it could no longer find any networks. I've tried to use the option "Connect to a hidden wireless network", entering the proper SSID but it will not connect. I get this blue spinning icon then it goes back to 'disconnected' (or whatever it says, I get this text-bubble saying I was disconnected or something along those lines, if necessary I can go check it...).

---

### Post by gnusci on 2008-11-29
Have you tried do the configuration with the Network Manager:

**$ NetworkManager**

---

### Post by Scarlath on 2008-11-29
**$ NetworkManager** said "You must be root to run Network Manager!".

**$ sudo NetworkManager** return a new line for me to enter a new command. How exactly do I set up a network?

---

### Post by gnusci on 2008-11-29
Now you should be see the icon in the taskbar...

[http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/)

Then you can try to set up a connection....

---

### Post by Scarlath on 2008-11-29
I already saw the icon before doing that command however. I've seen it all the time, sorry if I was not clear about that. The thing is that I cannot see any networks to connect to once clicking on that icon (which I did in the live enviroment). Nor can I access my network by entering the SSID. 

First I get this blue, spinning icon which says "Attempting to join the wireless network '[ssid]'.". Then it stops and says "Disconnected. The network connection has been disconnected.".

If you look at the website you just linked, at their first page you see this picture of how it should look like when clicking the icon; how good link quality different wireless networks around the computer has etc. It looked somewhat like that when I was in the LiveCD (however, as I said in my first post - after installation it doesn't even work under the LiveCD either...). Now, it's just greyed out pretty much (only the top part of it) and I cannot see any networks there. I hope you understand what I mean :)

---

### Post by Scarlath on 2008-11-30
Bump as it's been over 24 hours :)

---

### Post by raakken on 2008-11-30
I have the same problem after updating 8.04 to 8.10. Now the webcam is "gone" and I can't get my wifi radio on(I can't find any networks).

---

### Post by Scarlath on 2008-11-30
Glad to hear I'm not the only one... I guess :wink:

Is your system set up somewhat the same?

Anyone got any more ideas on what to try?

When I installed Ubuntu I left the wireless network usb adapter plugged in, perhaps I should not have done that? Or should it not matter? It shouldn't matter :(

---

### Post by Scarlath on 2008-12-01
Just tried disabling / reenabling networking (through the tickbox in the network manager)... didn't work either.

---

### Post by Scarlath on 2008-12-03
Still haven't found a solution ._.

---

### Post by Scarlath on 2008-12-04
Bump.

---

### Post by Geffers on 2008-12-04
> **raakken said:**
> I have the same problem after updating 8.04 to 8.10. Now the webcam is "gone" and I can't get my wifi radio on(I can't find any networks).

Me too :( ethernet fine just the wifi not working now.

Fortunately I still have a working V8.04 partition.

Geffers

---

### Post by Scarlath on 2008-12-05
Bumping this, once again :)

---

### Post by Scarlath on 2008-12-06
> **Scarlath said:**
> Bumping this, once again :)

... and again ;)

---

### Post by hnmcc on 2008-12-06
I have the same problem with 8.10 - in the Live version from the off.  But I have recently sampled three other distros, all of which have seen and connected to the Intel wireless adapter on my Thinkpad X41 easily.

None of the 8.10 network functionality sees the wireless adapter at all: so there are no networks to connect to, and no obvious way of investigating the problem (let alone repairing it).  The hardware testing functionality does see the adapter, and implies that it's working (which it obviously is and does - in Windows and elsewhere in the Linux world).

Not good.

---

### Post by psychoelf on 2008-12-07
Ok...my wifi has been working fine with 8.10 until today.  Started watching a DVD and when it was over my wifi was gone.  The only thing odd that had happened today was that I left on desktop effects when I put my laptop to sleep and had to do a hard boot to get out. 

Network Manager shows up, but no wifi.  I'm having the same problem where I can manually punch in my network name/pass but it won't connect.  My wife's laptop is working great though.

---

### Post by psychoelf on 2008-12-07
Got it working again.  Installed Wicd and booted into recovery mode.  Used recovery tools to repair damaged packages and while I was there did a system scan just in case.  Rebooted and all is well.  Sorry I forgot to link the posts I found these great ideas.

P.S.  On a Gateway 6850FX with the Intel 4965AGN.  Was reading a few forums about HP's with wrong specs that actually have 5100's, so double check with dmesg.

---

### Post by Scarlath on 2008-12-07
I dont have a HP computer though :(

Okay, so if no one is able fix my problem, could you perhaps recommend a wireless usb network adapter that works fine with Ubuntu (and Windows, of course)?

I'd really like to get this fixed first though, so the above is just a emergency solution, so to speak.

---

### Post by psychoelf on 2008-12-07
Have you tried recovery mode with the package fixer?  I dual boot so its a boot option.  Im not sure how if Ubuntu is your only OS, but you could probably find out how on the forum.


Also, try to be patient with results.  You may have a unique problem.  I started using Ubuntu with version 6 and after the first update I had no Wifi until version 7.  The best thing you can do is try all suggestions.  If they don't work, try a clean install with the newest version.  Try checking other distro forums to see if somebody with the same hardware is having the same issue.  I don't know much about Linux, but I do know that the community has the best support out there.

---

### Post by Scarlath on 2008-12-07
Thanks for the reply, what exactly is it that I do with the package fixer? Do I need to have an internet connection? Do I need to have the CD in the drive, etc?

Thanks

---

### Post by psychoelf on 2008-12-08
On my computer my GRUB menu has a listing for my current linux kernel, a recovery kernel, and Vista.  This was all automatically setup by Ubuntu.  When I boot to the recovery kernel it boots first into a utility mode and the package fixer is an option under that menu.  All you have to do is select the repair option, it does the rest for you.  You should not need the CD in the drive.  I do not think you need the internet for this part, but if your hardwire ethernet still works, plug it in just in case.

You will need an internet connection to install Wicd -> [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) 
just follow the Ubuntu instructions and be sure to replace "hardy" with "intrepid".

Your hardwire ethernet still works I hope?

Hope this helps.

---

### Post by Scarlath on 2008-12-08
> **psychoelf said:**
> On my computer my GRUB menu has a listing for my current linux kernel, a recovery kernel, and Vista.  This was all automatically setup by Ubuntu.  When I boot to the recovery kernel it boots first into a utility mode and the package fixer is an option under that menu.  All you have to do is select the repair option, it does the rest for you.  You should not need the CD in the drive.  I do not think you need the internet for this part, but if your hardwire ethernet still works, plug it in just in case.

You will need an internet connection to install Wicd -> [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) 
just follow the Ubuntu instructions and be sure to replace "hardy" with "intrepid".

Your hardwire ethernet still works I hope?

Hope this helps.

I haven't tried any wired connection yet as I, as I mentioned earlier, would have to drag my entire setup (screen, keyboard, computer, etc.) downstairs in order to do that.

Ugh... it's really driving me crazy. :(

Might try your suggestions later though, thanks. Why would I need Wicd though?

And... qouting myself:
> Okay, so if no one is able fix my problem, could you perhaps recommend a wireless usb network adapter that works fine with Ubuntu (and Windows, of course)?

I'd really like to get this fixed first though, so the above is just a emergency solution, so to speak.

---

### Post by clw3388 on 2008-12-08
> **Scarlath said:**
>  Why would I need Wicd though?
:

wicd is a wired and wireless network manager. 
I believe the thought behind this is the native ubuntu network manager may be broke...
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD) instructions to install..

Might hardwire.. if working run the updates.. It's resolved some of my wireless network issues in the past...

---

### Post by psychoelf on 2008-12-08
What he said up above (Wicd).

As for a USB wifi, not sure as I've never used one, but try this:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#Wireless%20USB%20Adapters](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#Wireless%20USB%20Adapters)

---

### Post by Scarlath on 2008-12-09
Thanks. If I get time this week I'll try to connect to the internet via a cord and then update, perhaps that'll fix it... else I'll try your other suggestions.

---

### Post by psychoelf on 2008-12-21
Just a heads up.  After an update a few days ago, my wifi stopped working again even though I had Wicd installed.  I hooked up my ethernet and reinstalled Network Manager, which uninstalls Wicd, and Wifi is working again.  Weird eh?

---

### Post by scubajgp on 2008-12-21
Hey, I am having the same problem since I upgraded to 8.10.  I have used 8.04 for a long, long time, without any network problems, now I can no longer connect to my wireless unless I go back two kernels.  Then, I have no audio, and no print from my E-mail provider.  Sucks!

How can I go back to 8.04 (dual boot).

---

### Post by psychoelf on 2008-12-21
You can dual boot.  Just create a separate partition and install 8.04 to that partition.  You can also share the swap partition, but if you use hibernate then you may want another swap for that install.  GRUB should automatically update with the other version. (Please note that I'm not an expert and am basing this off of what I have read)

---

### Post by Marco_Lwb on 2009-01-09
Hi all !

I've the same problem...but reversed! :)

I'm using a live version of Ubuntu 8.10 and my wireless network works fine !

I've installed on a new dedicated HD the 8.04 Studio version and the wireless don't work.

My USB lan adapter is linked and it's "polling" but I can't see the SSID list of available wireless network in Network Manager and the same happen with terminal "iwlist wlan0 scan" ...no scan result.

The strange thing is (at least for me...as I'm a new Ubuntu user :) ) that I can get the correct wireless network info 
when I type "sudo iwlist wlan0 scan" !! 

Could it be something like a "user permission" issue ??

Sorry for my English.. :)

Ciao !
Marco

---

### Post by Marco_Lwb on 2009-01-09
Problem solved !

I've not tweaked anything...I've just installed WICD and now I'm surfing over the net ! :)

Ubuntu Studio 8.04 (32 bit)
D-Link DWL-G122 (Rev. C1)
Wicd 1.4.2


As said in my previus post, I have installed on another disk (same PC) the Live version of Ubuntu desktop 8.10 (64 bit) that works flawlessy with the standard software release.

I could post my settings hoping to help other users...

Cheers,
Marco

---

