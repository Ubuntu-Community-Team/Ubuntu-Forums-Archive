---
title: "kernel panic caused by Ralink RT3072 USB wifi adapter Ubuntu 14.04"
date: 2015-04-06
forum: Networking &amp; Wireless
---

### Post by joe164 on 2015-04-06
Hello.  I need some help getting a USB wifi adapter with a Ralink RT3027 chipset in it to work on Ubuntu 14.04.  The pc is a 1 yr old laptop that is fully updated.  The USB adapter worked great on a 7 - 8 yr old Dell desktop running Ubuntu 12.? and currently runs great on an 8 yr old Toshiba laptop running Win XP.

If I plug in the adapter before booting 14.04, I get a kernel panic message pretty quick.  If I plug in the adapter after 14.04 is running, it takes about 10 seconds for the kernel panic black screen and message to appear.  During those 10 seconds, if I open the Network Manager drop down menu near the clock, the menu is erratic and flashes between showing the Ralink adapter and not showing it.  If I use the Network Manager menu to disable wifi before plugging in the adapter, the kernel panic doesn't happen and the menu is stable and shows the Ralink adapter.  But, enabling wifi then causes the kernel panic to occur.

I attached the "wireless-info.tar.gz" file.  Thanks for any help.

Joe

---

### Post by chili555 on 2015-04-06
Why, oh why would you ever want a USB wireless when you have a built-in wireless that works and connects perfectly according to the wireless-info you provided? If the built-in isn't performing as expected, let's fix it and throw away the crutch.

---

### Post by joe164 on 2015-04-06
@ Chili.  The back story:  I installed the USB wifi adapter in a weather proof enclosure and then temporarily mount it on top of my RV and connect to it with a USB extension cable while I'm parked for extended stays at an RV park with wifi.  The built in wifi adapter doesn't work very well through the aluminum framed walls of the RV (or at least that's why I think it doesn't work well).  The built in adapter works great at home and other places, just not in the RV.  Also, the USB wifi adapter is a "high power" unit that supposedly transmits at 1000mw and when it works, it works well, out to 50 - 100 yards.

So, I'd really like to get the USB adapter working.  If I can't get it working, then a recommendation on a different USB adapter that works with 14.04 and is "high power" would be much appreciated.  Right now, if I had to replace the USB adapter, I'm considering an Edimax EW-7811 UAC.  Thanks for the reply.

Joe

---

### Post by chili555 on 2015-04-06
> The built in wifi adapter doesn't work very well through the aluminum framed walls of the RV (or at least that's why I think it doesn't work well).I think that's true.

I strongly suspect the issue is the interaction between the two driver suites; cfg80211, mac80211, rtlwifi, et al. You might try blacklisting the internal as an experiment:```
sudo -i
echo "blacklist iwlwifi"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot with the USB plugged in and let's hear the result. If successful, we'll address the switch back and forth between internal and USB a bit later.

Reminds me of the time a few years ago when I assisted a pal with a similar project on his boat.

---

### Post by wildmanne39 on 2015-04-06
I park in RV parks often and I can tell you that none of the parks have very good wifi either so that is a lot of the issue, and not enough bandwith. Not saying that there is not a driver coflict as well, if chili says there is you can take that to the bank.

---

### Post by joe164 on 2015-04-06
No kernel panic on reboot after following the above instructions.  But, the Network Manager drop down menu still flashed back and forth, adding then subtracting about 4 lines.  Once or twice a wifi hotspot showed up.  After about 10 seconds, the flashing stopped, but no evidence of a wifi adapter showed in the menu.  The pc remained usable though.  I then disabled and re-enabled networking, but that made no difference.  I then unplugged the USB wifi adapter and plugged it back in after a few seconds and got an immediate kernel panic.

I agree with you Wild Man about RV parks having poor wifi.  Interesting how they advertise it, but don't really deliver it.  But, I have been able to use some of them via the outdoor mounted USB adapter when I couldn't with the built-in adapter.

---

### Post by chili555 on 2015-04-07
Will you please reboot with the USB inserted and run and post the wireless script again? Let's see what's not happening as expected.

---

### Post by joe164 on 2015-04-07
Here are the results of the wireless script.  The pc froze up a couple of times while I let it do it's flashing Network Manager menu thing.  That meant I couldn't run the script and had to hold down the power button to shut it down and try again.  So I used the Network Manager menu to disable wifi after letting it do it flashing menu thing for about a minute.  Hopefully there is useful info in the script results.

Chili, thanks for the help.

---

### Post by chili555 on 2015-04-07
I see this awful thing in your wireless script:> [   98.745414] ieee80211 phy24: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[   98.745417] ieee80211 phy24: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  100.363373] ieee80211 phy24: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]Googling the error results in little or no useful information. A few threads suggest a later kernel version than yours:> [COLOR="#FF0000"]3.13.0-46[/COLOR]-generic x86_64You could try running a live session from a 14.10 Ubuntu DVD or even 15.04 beta. If the wireless works and there is no alarming error in dmesg, then install it.

Otherwise, I'd proceed with this option:> if I had to replace the USB adapter, I'm considering an Edimax EW-7811 UAC.I believe it requires that you compile a driver from source code. It's not a difficult process; just an additional wrinkle.

There are several threads here about plug and play USB wireless devices; you may wish to check those also.

---

### Post by joe164 on 2015-04-07
@ Chili.  Thanks for checking the output and letting me know.

When you suggest installing if it works with a live session, do you mean installing a later kernel or a later version of Ubuntu?  If you mean kernel, does running a different kernel than what a release comes with cause other problems?

I'll check for plug and play threads if it comes to that.

Thanks - Joe

---

### Post by chili555 on 2015-04-07
I meant the entire later version of Ubuntu.>  If you mean kernel, does running a different kernel than what a release comes with cause other problems?I have done so several times with no ill effect but, as in all things related to computers, there is no guarantee.

---

### Post by joe164 on 2015-04-08
Chili, thanks for clarifying and helping.  I'll try your suggestions until I get one that works.

Joe

---

### Post by joe164 on 2015-04-25
Since my last post I have tried:

Some additional Ubuntu images, here are the results:

[TABLE="width: 300, align: left"]
[TR]
[TD]Tests on problem laptop[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]64 bit Ubuntu 15.04[/TD]
[TD]didn't work[/TD]
[/TR]
[TR]
[TD]64 bit Ubuntu 14.10[/TD]
[TD]didn't work[/TD]
[/TR]
[TR]
[TD]64 bit Ubuntu 12.04.5[/TD]
[TD]didn't work[/TD]
[/TR]
[TR]
[TD]32 bit Ubuntu 14.04.2[/TD]
[TD]didn't work[/TD]
[/TR]
[/TABLE]
[TABLE="width: 300"]
[TR]
[TD]Test on old laptop[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]32 bit Ubuntu 14.04.2[/TD]
[TD]worked fine[/TD]
[/TR]
[/TABLE]
So, my original post that the usb wifi adapter wouldn't work on 14.04 was wrong.  Thinking it might be a conflict with some aspect of the built in Intel 7260 wifi adapter, and maybe Chili's instructions

```
sudo -i
echo "blacklist iwlwifi"  >>  /etc/modprobe.d/blacklist.conf
exit

```
didn't completely turn off the Intel 7260, I removed the built in wifi adapter and tested by booting the installed Ubuntu 14.04.  Still got the flashing menu when I plugged in the usb adapter.  I removed the usb adapter before a kernel panic occurred.

Next I tried

```
 sudo ifconfig wlan0 down
```

This didn't seem to do anything.  Could still see and log onto wifi hotspots.  When I plugged in the usb adapter, the Network Manager menu did the flashing thing.  I removed the usb adapter before a kernel panic occurred.

Next I tried

editing /etc/network/interfaces  by adding the following line:

  ```
iface wlan0 inet manual
```

  and then restarting network manager with:

```
sudo service network-manager restart
```
   No longer saw any wifi hotspots, but when I plugged in the external wifi, the flashing of the menu started again and both of the wifi adapters appeared and disappeared in the network manager as it flashed.  I removed the usb adapter before a kernel panic occurred.

Do these clues mean anything to anyone?  If not, does anyone have a recommendation for a "high power" usb wifi adapter with one or two "rubber duck" type antennas, as opposed to a "directional" antenna?   The one I was considering, Edimax EW-7811 UAC, isn't "high power" and I would prefer a "high power" adapter.

Thanks for any additional help.

Joe

---

### Post by Keith_Helms on 2015-04-25
A bit off topic, but I also deal with crummy RV park wifi regularly.  I picked up a tablet from Verizon that has hotspot capability and I use it to connect to their cell network.   The hotspot makes it work like a wireless router and I can connect to that with my laptop.   The verizon 4g signal is usually better and far faster than the campground wifi.  The only places I haven't been able to use it are campgrounds in Yellowstone and The Grand Tetons that didn't have wifi anyway.

The verizon service for the tablet runs me $40 a month and gives me 4GB of data allowance.   As long as you're not downloading large files or streaming video, that is plenty.   Heck, you can't stream video over those campground networks anway.  Most of their latest cell phones also have hotspot capability, so if you need a new cell phone, it could do double-duty as your laptop's internet access.

---

### Post by joe164 on 2015-04-26
@Keith_Helms
Thanks for the advice Keith.  I think I will end up updating my cellphone to have that capability, but I'm hoping it will be my backup internet connection as opposed to the primary.  I guess if I use the cell phone access full time and don't use up the 4g allotment then I don't have a problem.  Time will tell.  For now, I will continue to try and fix the kernel panic issue.

---

### Post by chili555 on 2015-04-27
I do see this in your log:> rt2800usb_entry_txstatus_timeout: Warning - TX status timeoutA Google search leads me here: [https://forums.kali.org/showthread.php?23063-Please-help-with-rt2800usb-txpower-warning](https://forums.kali.org/showthread.php?23063-Please-help-with-rt2800usb-txpower-warning)

Evidently, there is a later firmware than the 0.29 version you are using. Let's try it:```
#Download:
wget media.cdn.ubuntu-de.org/forum/attachments/13/16/4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz
# Extract:
tar zxf 4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz
# Backup the old one
mv /lib/firmware/rt2870.bin /lib/firmware/rt2870.bin.bak
# And copy the new one:
cd Ralink_5370sta-2.5.0.3/src/common
cp rt2870.bin /lib/firmware/rt2870.bin
```Reboot and let us have a new wireless script as above.

---

### Post by joe164 on 2015-04-27
@ Chili.  Here is the latest wireless_script output.

Unfortunately, the pc acted the same when I plugged in the usb wifi adapter, no improvement.

Thanks for your help.

Joe

---

### Post by chili555 on 2015-04-28
It appears that the driver for the internal, iwlwifi, is still loading. Did you try blacklisting it and rebooting?

If the behavior is still the same, with the USB detached, let's compile the latest driver:```
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/04/24/backports-20150424.tar.xz
```Right-click the downloaded file on your desktop and select 'Extract Here.' Now continue:```
cd backports-20150424
make defconfig-wifi
make
sudo make install 
```Blacklist iwlwifi, reboot with the USB inserted and let us hear your report.

---

### Post by joe164 on 2015-04-28
I had un-done the blacklisting of iwlwifi.  I re-blacklisted it and rebooted.  The network Manager menu still did the flashing thing.  I let it continue for about 3 minutes and it never had a kernel panic.  Also, the usb adaptor never showed in the Network Manager menu, but occasionally one wifi hotspot did.

I followed the instructions in Chili's last post and all seemed to go well except I got a "Can't read private key" message after each module in the "sudo make install" part of the process.  Also, at the end of the "sudo make install" step, there was a message about maybe needing to update the initramfs if any of the modules are part of it.  I didn't update the initramfs.

When I plugged in the usb adaptor after re-installing the driver modules the Network Manager menu still flashed.  The only difference I detected was that the cycle of the flashes was shorter/faster.  Instead of the menu appearing for 1 - 2 seconds before flashing and re-appearing with different menu items visible, it only appears for about 1/2 a second now before flashing off then re-appearing.

I ran and uploaded the output of the wireless_script.

Thanks for the help.

Joe

---

### Post by chili555 on 2015-04-29
We have tried different versions of the driver, we have tried different kernels, we have tried different firmware files; it appears there are only two options remaining. First, this:> Test on old laptop 	
32 bit Ubuntu 14.04.2 	worked fineOr, second, get a different device altogether. I regret that I haven't any other suggestions.

---

### Post by joe164 on 2015-04-29
@Chili  Thanks so much for trying.  I really appreciate it.

---

### Post by Keith_Helms on 2015-05-19
Now, this is interesting.  I have an EtekCity USB high power wifi adapter that I keep in my fifth wheel.   I last used it back in 2014 when I was still on Xubuntu 12.04 and a 7 year old HP laptop and it worked fine.  I have a new laptop with 14.04 installed and I discovered that it also has that Ralink RT3072 chipset and I was also getting that kernel panic problem.  I had it plugged into a USB 2 port.  When I plugged it into a USB 3 port, lo and behold, it works!  I have no clue why.   I believe USB 3 ports supply a bit more power, so it could be that, or maybe having a combination of USB 2 and 3 ports on the same system is not correctly supported by the driver.

---

### Post by joe164 on 2015-05-19
That is interesting.  I tried both USB 2 and USB 3 ports, but no luck for me.

---

### Post by Keith_Helms on 2015-05-19
It worked for me under both Xubuntu 14.04, which has the 3.13 kernel and  Ubuntu 14.04 with the 3.16 kernel, so I think that establishes that  Ubuntu does support that chipset.  An excerpt from the lsusb command on my system shows:

```
Bus 003 Device 004: ID 148f:3072 Ralink Technology, Corp. RT3072 Wireless Adapter
```

So, maybe your device has something other than just a driver problem.  I wonder what would happen if you connected it to a powered USB hub and then connected that to your laptop.  It's possible it's power related.

---

### Post by joe164 on 2015-05-20
Keith, your hunch was right!  It seems to work fine when attached through a powered USB hub.

I have three "high power" USB wifi adapters.  All three cause kernel panics when attached directly to the pc.  I have only tried one through the powered hub, it's an EtkCity (same brand as Keith's).

It appears my new laptop is a bit skimpy on how much power it supplies to the USB ports.  Seems a bit wrong to me that a 9 yr old laptop can outperform a 1 yr old laptop in anything, but maybe something else is at play.

Thanks for the help Keith.  I consider this solved.

Joe

---

### Post by Keith_Helms on 2015-05-20
That's great news!  It's too bad you had to spend hours messing with drivers and blacklists and who knows what else!

It's just a coincidence that we discovered this.  Normally when I'm in a campground with poor wifi, I haul out my Nexus 7 tablet and use Verizon for internet access.  I just happened to end up at a campground where both the wifi was poor and it was also a "dead zone" for Verizon.   My tablet couldn't see any cell signal.  It was that combination that led me to pull out the external wifi adapter, try it, and discover it was prone to that kernel panic problem.  I also just happened to wonder what it would do if I plugged it into a USB 3 port.

---

### Post by joe164 on 2015-05-20
@Keith  I have spent a fair bit of time working/researching this problem, but I learned some things along the way and am pleased to have it resolved.

Your curiosity is another example of why there is the saying:  Nothing ventured, nothing gained.  Thanks again for the help.

---

### Post by joe164 on 2015-06-03
I just discovered that the USB wifi adapter works when I plug it into a non-powered USB hub as well as a powered hub.  I tried plugging the non-powered USB Hub into both a USB 2.0 port and a USB 3.0 port and the wifi worked great in both cases.  I don't know what that may mean as the cause of the original problem, but it appears that low power isn't the problem.

---

