---
title: "[SOLVED] Broadcom Wireless card problems"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by CasPol on 2008-05-18
Hi there;

I hope anyone can help me out here ...

I have a Broadcom wireless card. Did a clean install of Hardy Heron. Donwloaded the bcm43-fwcutter, and the wireless light is now on (Acer aspire 3000). 

When trying to connect to home network it will not connect. SSID, and password all correct.

Used to work flawless with Gutsy ...

What's going wrong here ?

Thanks.

---

### Post by Ayuthia on 2008-05-18
> **CasPol said:**
> Hi there;

I hope anyone can help me out here ...

I have a Broadcom wireless card. Did a clean install of Hardy Heron. Donwloaded the bcm43-fwcutter, and the wireless light is now on (Acer aspire 3000). 

When trying to connect to home network it will not connect. SSID, and password all correct.

Used to work flawless with Gutsy ...

What's going wrong here ?

Thanks.
Are you using b43 or bcm43xx?  If it is bcm43xx, there is most likely a conflict with the new b43 driver and ssb.  If you are using b43, then you might try to see if it will work without encryption.  If it does, then we need to see what is happening with the encryption portion.  

If none of this makes sense, from the Terminal please post the results of:
```

ls /lib/firmware
lshw -C network
```
The b43 drivers have their own folder in /lib/firmware and bcm43xx has its firmware in /lib/firmware.  lshw -C network will show what driver it is trying to use.

---

### Post by CasPol on 2008-05-18
This is the output ..

2.6.24-16-generic     bcm43xx_initval05.fw    bcm43xx_microcode2.fw
b43		      bcm43xx_initval06.fw    bcm43xx_microcode4.fw
b43legacy	      bcm43xx_initval07.fw    bcm43xx_microcode5.fw
bcm43xx_initval01.fw  bcm43xx_initval08.fw    bcm43xx_pcm4.fw
bcm43xx_initval02.fw  bcm43xx_initval09.fw    bcm43xx_pcm5.fw
bcm43xx_initval03.fw  bcm43xx_initval10.fw
bcm43xx_initval04.fw  bcm43xx_microcode11.fw


What next ?

---

### Post by CasPol on 2008-05-18
Have now spent the whole day trying to resolve this, Got lucky at some point, had to remove something and then re-install b43-fwcutter. Stopped working after a while and cannot find the trick again, I will go back to Gutsy broadcom card worked flawless with Gutsy, untill this bug is resolved.

---

### Post by linthusiast on 2008-05-18
I have a BCM4303 card and last night did a clean install of 8.04. On previous version of Ubuntu I was able to use ndiswrapper to get the card up and running in a short amount of time. With Hardy Heron, it seems to be a different story.

**What I keep seeing**
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)

In the above it doesn't matter if I use the bcmwl5 or bcmwl5a windows driver. I still get "driver installed device (14E4:4320) present (alternate driver: ssb)".

I have noted and applied the several tutorials people have generously posted online on blacklisting ssb, b43, b44, b43legacy, etc. Along with rmmod(ing) aforementioned drivers. I notice that even if I have blacklisted ssb, it's still loaded by the kernel during startup. So I have tried loading ndiswrapper before ssb and still it doesn't fix the problem. Initually I had a problem with the following

**sudo modprobe ndiswrapper**

as it was telling me it could not be loaded with a fatal error, but when I completely removed ndiswrapper from my system, downloaded latest source from sourceforge and compiled, installed, it then loaded fine. Except when I perform a

**ndiswrapper -l**

I still get the "(alternate driver: ssb)" message. Also as you can imagine when I do a

**lshw -C network**

I still see the module=ssb, when it shoudl be module=ndiswrapper.

When I read other people's tutorials I was certain that the missing piece of the puzzle was they they should have removed the offending driver modules from the kernel before trying the "ndiswrapper -i [/path/to/.inf]" command. So what I did was unload everything and so that nothing related to the problem shows up with a

**lsmod**

Then did an install using "ndiswrapper -i [/path/to/.inf]", and unfortunately it's still telling me that it has loaded with ssb. I can't understand this because how I can I make it more clear how I want the driver to load. 

Is the Drivers applet causing problems here? Why do I feel like some of these new "user friendly" additions to ubuntu are becoming more hassle than they are worth.

Please help, anyone?. I am days trying to get this working.

PS: Let's hope that my Nvidia 8800GTS 512MB card doesn't give me as much trouble (because I notice that the nvidia_new driver that comes with 8.04, will not enable).

---

### Post by Ayuthia on 2008-05-18
> **CasPol said:**
> Have now spent the whole day trying to resolve this, Got lucky at some point, had to remove something and then re-install b43-fwcutter. Stopped working after a while and cannot find the trick again, I will go back to Gutsy broadcom card worked flawless with Gutsy, untill this bug is resolved.
Sorry, I was spending the day with my family.

From your results of you /lib/firmware, you did install the bcm43xx firmware.  You could have used it by just blacklisting b43 and verify that bcm43xx is not blacklisted in /etc/modprobe.d/blacklist.

The other option was to install b43-fwcutter which is what I think you have done also.  You would have had to make sure that bcm43xx was blacklisted in /etc/modprobe.d/blacklist.

---

### Post by Ayuthia on 2008-05-19
> **linthusiast said:**
> I have a BCM4303 card and last night did a clean install of 8.04. On previous version of Ubuntu I was able to use ndiswrapper to get the card up and running in a short amount of time. With Hardy Heron, it seems to be a different story.

**What I keep seeing**
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)

In the above it doesn't matter if I use the bcmwl5 or bcmwl5a windows driver. I still get "driver installed device (14E4:4320) present (alternate driver: ssb)".
This is usually ok.  Mine has it that way and I am still able to use it.

> I have noted and applied the several tutorials people have generously posted online on blacklisting ssb, b43, b44, b43legacy, etc. Along with rmmod(ing) aforementioned drivers. I notice that even if I have blacklisted ssb, it's still loaded by the kernel during startup. So I have tried loading ndiswrapper before ssb and still it doesn't fix the problem.
What have you done to accomplish this?  There are several posts on how to unload/load ssb.  Have you already tried:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
```
If so, what are the results?  If it does not say anything, what does the end of dmesg say after you do this?

---

### Post by CasPol on 2008-05-19
Thanks very much for all the replies. I have by now done a clean install of Hardy. Wireless is not ( yet ) working. How do I get the Broadcom 4318 working? I know from previous attemps that installing b43-fwcutter with the help of hardware manager did NOT work ....

---

### Post by linthusiast on 2008-05-19
Thanks for the replies guys. Right my update is that the module being loaded is still ssb, but I switched the windows driver that used to work with older versions of ubuntu with the one listed in step 2b of the tutorial. Even though the module is still ssb, I can bring up my wlan0 interface, and do a

**sudo iwlist scan**

Which lists my access point amongst others. So then using the System -> Administration -> NetworkManager, I enter my WPA key, and static IP details. When I do this and I do a

**iwconfig**

I can see that my card has associated with my AP. However when I try to do anything like ping my router, I keep getting "destination unreachable". My understanding is that I now have the kernel talking to my card and I've probably got a WPA / Ndiswrapper issue.

It's great that my card is actually working, but if I could just get it working at the higher network layers that would be excellent.

Any help you can offer would be greatly appreciated!

---

### Post by kevdog on 2008-05-19
The best broadcom tutorial I know (for ndiswrapper) is here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Notice however the 4303 is not specifically listed -- meaning that you need to supply your own bcmwl5.inf and .sys files (perhaps from the cd of website).

If you get it up and running with the remainder of the steps, please notify so the specific driver can be uploaded to the site so others can download it.

---

### Post by Ayuthia on 2008-05-19
> **CasPol said:**
> Thanks very much for all the replies. I have by now done a clean install of Hardy. Wireless is not ( yet ) working. How do I get the Broadcom 4318 working? I know from previous attemps that installing b43-fwcutter with the help of hardware manager did NOT work ....
What did you use in Gutsy?  If you used bcm43xx-fwcutter, we could go that route and see if it works.  We could try using b43 again and see if there is an issue with the driver on your computer (it could be possible that bcm43xx was not blacklisted and was causing conflicts).  The other option is to try NDISwrapper.  

If you are looking for my opinion, you now say that you have a fresh install.  If you are willing, I would try installing the b43 drivers on it again.  A fresh install of Hardy has bcm43xx blacklisted.  We can see if it works or not.  If it does not work, we will blacklist b43 and b43legacy.

Then we can try bcm43xx.  We would just install bcm43xx-fwcutter and remove the blacklist for bcm43xx.  If it worked in Gutsy, it should work again in Hardy.  If we can't get it working, we can then blacklist the bcm43xx driver again and try NDISwrapper.

However, I do understand the frustration of getting your wireless to work and would like it to work as quickly as possible.  I am going to say, that the 4318 card does work, but it has been difficult to get it running.

If you want to just go the NDISwrapper route, I would recommend that you install ndiswrapper-common and ndiswrapper-utils-1.9.  Find an XP wireless driver from Acer for your computer and then let us know that you have it ready and also post your lspci -nn.  There are a lot of guides that do work out here, but with the new drivers being used now, I would prefer that people try to get NDISwrapper working before they go through the steps of configuring the computer to make it permenant (blacklisting drivers, adding modules, and possibly adding scripts).

---

### Post by linthusiast on 2008-05-19
I have gotten that far already. As I said I used step 2b from that tutorial. I am dual booting with XP, so I downloaded [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe) in XP. Extracted to folder, then in ubuntu mounted that NTFS partition and then had access to my .inf and .sys files. It still says it's using ssb when I do a

**ndiswrapper -l**

But when I **sudo iwlist scan**, I get a list of APs, including my own.

**iwconfig** shows that I have associated (we'll it shows a MAC address, as opposed to saying "Not Associated"), but I still can't ping any other devices on the network.

Hope this info helps, any ideas?

---

### Post by Ayuthia on 2008-05-19
> **linthusiast said:**
> I have gotten that far already. As I said I used step 2b from that tutorial. I am dual booting with XP, so I downloaded [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe) in XP. Extracted to folder, then in ubuntu mounted that NTFS partition and then had access to my .inf and .sys files. It still says it's using ssb when I do a

**ndiswrapper -l**

But when I **sudo iwlist scan**, I get a list of APs, including my own.

**iwconfig** shows that I have associated (we'll it shows a MAC address, as opposed to saying "Not Associated"), but I still can't ping any other devices on the network.

Hope this info helps, any ideas?


Do you have encryption?  If not, we can try to configure it manually.
```
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid <name>
sudo dhclient wlan0
```
Replace <name> with the essid of your access point (Example: sudo iwconfig wlan0 essid my_router.

If it does not connect (says that it is sleeping), try another channel on your router.  It could just be interference.  Also make sure that your wireless is set to roaming in Ubuntu.

---

### Post by linthusiast on 2008-05-19
I'm actually using static address (not DHCP) on my network. I find that my interfaces come up a lot quicker in Windows when I don't have to wait for addresses to be handed out. I am also using WPA-SPK (TKIP).

When I do an **ifconfig**, the output looks fine, with the static IP in place.

Also when I do an **iwconfig**, all seems to be in order, with an association in place.

Now something that I didn't mention before...during my attempts to get *module=ndiswrapper* as opposed to *module=ssb* I created the wirelessfix.sh script and registered it with inet.d to load during startup. The script as you know unloads all relevant modules, and then reloads them with ndiswrapper before ssb, etc. When I enabled this script my machine did a "soft lockup" during boot, showing (NdisWriteErrorLogEntry:...) lines every 11 seconds. Not until I commented out the lines in wirelessfix.sh, did I get a bootable system back.

Can I disregard this as I seem to have the card talking (in that it is giving me scan results at least)

---

### Post by Ayuthia on 2008-05-19
> **linthusiast said:**
> I'm actually using static address (not DHCP) on my network. I find that my interfaces come up a lot quicker in Windows when I don't have to wait for addresses to be handed out. I am also using WPA-SPK (TKIP).

When I do an **ifconfig**, the output looks fine, with the static IP in place.

Also when I do an **iwconfig**, all seems to be in order, with an association in place.

Now something that I didn't mention before...during my attempts to get *module=ndiswrapper* as opposed to *module=ssb* I created the wirelessfix.sh script and registered it with inet.d to load during startup. The script as you know unloads all relevant modules, and then reloads them with ndiswrapper before ssb, etc. When I enabled this script my machine did a "soft lockup" during boot, showing (NdisWriteErrorLogEntry:...) lines every 11 seconds. Not until I commented out the lines in wirelessfix.sh, did I get a bootable system back.

Can I disregard this as I seem to have the card talking (in that it is giving me scan results at least)

For now, I would not use the script.  There is a good chance that you don't need it.  You only need it if ssb is needed.  What we could do is:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
```

That will clear out the Broadcom drivers and ssb for now.  It is kinda like blacklisting the drivers but it only works for this session.

As for the ssb showing up in ndiswrapper -l, that is not too big of a deal.  I currently have it in mine and it works fine.

EDIT:
I forgot that you mentioned that you have a static ip.  If it is configured in /etc/network/interfaces, please restart your network after doing the sudo modprobe commands:
```
sudo /etc/init.d/networking restart
```

---

### Post by linthusiast on 2008-05-19
OK I did that, ssb still shows up on ndiswrapper -l (but as you say, that's not too much of a big deal). When I restart my network services, I still have my static info in place, but can't ping the router (or anything else for that matter).

Thank you very much for your help btw, I really appreciate it.

---

### Post by Ayuthia on 2008-05-19
> **linthusiast said:**
> OK I did that, ssb still shows up on ndiswrapper -l (but as you say, that's not too much of a big deal). When I restart my network services, I still have my static info in place, but can't ping the router (or anything else for that matter).

Thank you very much for your help btw, I really appreciate it.

Can you post your lshw -C network?  I just want to make sure that we have the right drivers.  Thanks!

---

### Post by linthusiast on 2008-05-19
Right I'm posting from Ubuntu 8.04 with my wireless setup nearly working.

From my last post the only thing I needed to do to get rid of the "host unreachable" ping error messages was to modify my /etc/network/interfaces and set it to the following...
[I]
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.2.3
netmask 255.255.255.0
gateway 192.168.2.1
wpa-driver wext
wpa-ssid MyEssid
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk my_key_value_in_hex[/I]

Then when I did a **sudo /etc/init.d/networking restart**, it worked! and I could ping the network and go online. Where it's still not working is when I reboot, I have to go through the same process again. How can I get it to keep the settings and use them during next boot?

---

### Post by Ayuthia on 2008-05-19
> **linthusiast said:**
> Right I'm posting from Ubuntu 8.04 with my wireless setup nearly working.

From my last post the only thing I needed to do to get rid of the "host unreachable" ping error messages was to modify my /etc/network/interfaces and set it to the following...
[I]
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.2.3
netmask 255.255.255.0
gateway 192.168.2.1
wpa-driver wext
wpa-ssid MyEssid
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk my_key_value_in_hex[/I]

Then when I did a **sudo /etc/init.d/networking restart**, it worked! and I could ping the network and go online. Where it's still not working is when I reboot, I have to go through the same process again. How can I get it to keep the settings and use them during next boot?

Do you have the wirelessfix.sh script still or is it all commented out?  It sounds like the ndiswrapper module is being loaded after /etc/init.d/networking has already started.

---

### Post by kevdog on 2008-05-19
To your interfaces file, you could add various preup lines that would unload and then reload the various modules you need to make it work.  You could also add postdown statements that would unload the ndiswrapper module (if you wanted).

---

### Post by CasPol on 2008-05-21
I have managed to resolve it, with a tip from another forum.

Only works after a fresh install of Hardy, and with Broadcom 4318.

Do not use the "Driver Manager".

open Terminal

1. Sudo bash

2. apt-get install b43-fwcutter

3. Wait for install to complete

4. rmmod b43 ( ignore "not loaded" message)

5. modprobe b43

6. ifconfig wlan0 up

That was all I needed, up and running immediatly, and still working.

Thanks to everyone who tried to help. I hope the above will help anyone else struggling with the same problem.

---

