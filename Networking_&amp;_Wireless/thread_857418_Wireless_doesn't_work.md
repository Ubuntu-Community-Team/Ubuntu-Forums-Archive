---
title: "Wireless doesn't work"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by Tinkel on 2008-07-12
Hello Everybody,

I installed Ubuntu on my computer a few days ago. (I'm very happy with this :) ) But my wireless doesn't work. It now doesn't even want to turn on anymore. I have Windows on this computer as well and there wireless has no problem. :mad:

Where should I start??? Thanks

---

### Post by falcon61102 on 2008-07-12
If you could post the results of:
```
lspci
```
and
```
lshw -C Network
```

We can see what kind of hardware you have and begin to help you out.

---

### Post by adldesigner on 2008-07-12
I second falcon61102's request.

To post that output, get into a terminal (Applications > Accesories > Terminal) and type:
```
lspci
```
Then copy and paste the screen output into your reply.
Remember to enclose it with CODE tags.

Also, if you copy from Ubuntu's Terminal instead of using Ctrl-C you use **Ctrl-Shift-C**.

Do the same for:
```
sudo lshw -C network
```
It will ask for your password and then show you the output.

Both are needed to start to diagnose the problem. ;)

---

### Post by Tinkel on 2008-07-12
I have to restart my computer, I'll be right back.
Thanks

---

### Post by Tinkel on 2008-07-12
so for the first command it says:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:00.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
06:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
06:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

for the second, it just doesn't stop 'thinking' and one of my two cpu's is working 100% for the whole time. At some point I stoppes it. :confused:

---

### Post by falcon61102 on 2008-07-12
That's odd... it can take some time to run through it.  How much time did you give it?  And did you notice where it got hung up at?  Also, as adldesigner suggested, run it as sudo if you didn't, that way you don't get the warning about running it as admin.  Also, make sure other processes aren't trying to use the network card at that point, that can slow it down.  Try it again and see if can't get it to respond.  Sometimes just a restart will do that.

---

### Post by adldesigner on 2008-07-12
> **Tinkel said:**
> 
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Ok, so your wireless card is being seen.

Hmm, about your problem with the command, how about trying the following command instead?
```
sudo lshw -C network > ~/Desktop/lshw_output.txt
```
Then go into your Desktop, open your lshw_output.txt file and copy it's contents here.

Remember to enclose the code in CODE tags (the small numeral -#- in the top menu)

---

### Post by Tinkel on 2008-07-12
Okay;
So the terminal gets stuck again on : PCI (sysfs)

I tried with the output.txt but it says : 
bsch /home/tineke/Desktop/lshw_output.txt : No document or file found of this type

what's up with the code tags by the way? where is it, what's it for?

---

### Post by falcon61102 on 2008-07-12
All the code tags do are put the lines of code in those little boxes so its easier to read... if you click New Reply or click Go Advanced on under the quick reply box, it will bring you to another page with more buttons to add stuff to your posts.  One of those buttons is a # and that will add the code tags, just put your code between the two tags and you're good to go.

---

### Post by falcon61102 on 2008-07-12
As far as the other thing goes, it sounds like it's hanging up because another ap is trying to access your network at the same time or your network card is busy.  If you look in the upper right hand corner of the desktop in Ubuntu, you should see a network monitor icon.  Click on that and make sure that it's not trying to connect to anything before you run that command again.  Also try running:
```
ifconfig
```
and:
```
iwconfig
```
And post the results.

BTW... those boxes are what the code tags do, just in case my last post was a bit confusing...

---

### Post by Tinkel on 2008-07-12
Okay, I got that. But I'm working with two computers so I can not really copy and paste.  Acually my computer answer starts with:```
bash: /home/tineke/Desktop/lshw_output.txt : No document or file of this type found
```

voila

---

### Post by falcon61102 on 2008-07-12
One solution would be to creat a file "lshw_output.txt" on your desktop and run the code again and see if it writes to it this time.  Have you tried that?

---

### Post by Tinkel on 2008-07-12
So for ifconfig and iwconfig it replies:

```
ineke-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:fb:45:f5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:219 Adresse de base:0xa000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:2702 erreurs:0 :0 overruns:0 frame:0
          TX packets:2702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:135100 (131.9 KB) Octets transmis:135100 (131.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:b8:6a:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-B8-6A-A9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

tineke@tineke-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by falcon61102 on 2008-07-12
Ok... it looks like you have drivers installed, whether they are the right ones, I can't tell from that, unfortunately.  

Have you tried running the lshw -C Network command again?  

Also it looks like it's trying to connect to a router they may have WEP or WPA security enabled, is that your case?

If you click on the Network Manager in the upper right of the desktop, do any Access Points show up in the menu?

---

### Post by adldesigner on 2008-07-12
> **falcon61102 said:**
> Have you tried running the lshw -C Network command again?  


This can work too, but you'll have to scroll to find the network entries.
```
sudo lshw
```

---

### Post by adldesigner on 2008-07-12
> **Tinkel said:**
> 

```
wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
It seems like this could be the wireless network interface -although without lshw's output we can't know for sure-.

What strikes me as odd is the fact that it shows no name for ESSID, so that would mean that your pc cannot see the network. Maybe your wireless interface is not seeing any router broadcasting around. 
[LIST]
[*]Is it turned on?
[*]Are you connected to it from another computer?
[/LIST]
Take into account falcon61102's suggestions as per the Network Manager's Access Point settings, since none appear in this output.

---

### Post by calvinps on 2008-07-12
May I quickly butt in on this? I am having the same problem as the correspondent in this thread and I have attempted the codes that were posted.

I have the pictures of results here.

Hope this helps ;)

---

### Post by falcon61102 on 2008-07-12
calvinps, if you could start a new thread so that we don't get the commands confused because you may have to run certain things that Tinkel won't and vice versa.  If start a new thread and come back here with a link to the new one, we can help there.  It will be less confusing because the hardware in question is different.

BTW... it looks like you system may not have drivers loaded for your network card.

---

### Post by falcon61102 on 2008-07-12
[QUOTE=adldesigner;5372852]What strikes me as odd is the fact that it shows no name for ESSID, so that would mean that your pc cannot see the network. Maybe your wireless interface is not seeing any router broadcasting around. 
QUOTE]

The card may be seeing a router but depending on how it was configured, it may not be getting the name of the router.  The way that it says ""Nickname:.."" it looks like it may be trying to access the router but is getting messed up with router interface.

---

### Post by calvinps on 2008-07-12
[http://ubuntuforums.org/showthread.php?p=5373060#post5373060](http://ubuntuforums.org/showthread.php?p=5373060#post5373060)

---

### Post by adldesigner on 2008-07-12
> **falcon61102 said:**
> The card may be seeing a router but depending on how it was configured, it may not be getting the name of the router.  The way that it says ""Nickname:.."" it looks like it may be trying to access the router but is getting messed up with router interface.

Agreed. So then it could be that it's an encrypted network, thus the router might be obfuscating any info regarding connection to it.

Tinkel, did you check into your Network Manager the settings for the network's access point?

---

