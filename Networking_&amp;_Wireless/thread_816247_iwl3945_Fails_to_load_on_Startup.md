---
title: "iwl3945 Fails to load on Startup"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by fixedgear on 2008-06-02
Hey y'all.  I'm having this weird issue.

I successfully got myself off the ipw version of the intel wireless driver and onto the iwl.  Only this was my issue.  When I would start up the iwl driver wouldn't load.  No biggie, I could work around this by ```
sudo modprobe iwl3945
``` then after a few second I would do a ```
iwconfig
``` verify that the device is there then I would do a ```
iwlist wlan0 scan
```

And that would get me connected...kind of a round about, but right now work is more important, and if I can get that working and not futzing then cool.  But now I have a new problem. 

When booting I'm having a problem with the iwl driver being loaded. from dmesg:
```

[   12.752000] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.1.0
[   12.752000] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   12.752000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   12.752000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   12.752000] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   72.752000] iwl3945: iwlwifi-3945-1.ucode firmware file req failed: Reason -2
[   72.752000] iwl3945: Could not read microcode: -2
[   72.752000] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
[   72.752000] iwl3945: probe of 0000:0c:00.0 failed with error -2

```

Any help on getting this to load with out errors at startup would be GREAT or just a finger pointing in the right direction!

A side note, I booted into my windows partition, and noticed that the wifi switch was turned off.  I turned it back on connected just fine.  Then rebooted and tried to boot to Ubuntu (7.10) again, and still same problem.

I'm running a Dell XPS m1330.

Thanks

---

### Post by chili555 on 2008-06-02
Did you install iwl3945 in 7.10 from source, that is a .tar.gz file? Check here: [http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1486](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1486) especially: > Um, you need to install the new firmware package. For 3945, the latest is
iwlwifi-3945-ucode-2.14.1.5.tgzDoes that fix it, or did I guess wrong?

---

### Post by fixedgear on 2008-06-02
The drivers were already installed.  I just followed the instructions from the dell linux wiki page.

It was something about blacklisting the ipw3945 driver
adding iwl3945 to the /etc/modules file
and then verifying that the iwl3945 driver was being used with the following command:```
lsmod | egrep 'module|iwp|iwl'
```

I also had to delete the ```
/etc/udev/rules.d/70-something-something-file
```
so that it would recreate the rule so that it wlan0 would be using iwl3945

{update}looking into that link you sent me{update}

---

### Post by fixedgear on 2008-06-02
Alright Update:

So, I downloaded the updated firmware archive.  I copied the ucode file into my firmware directory.  Then reboot, no go.

So I renamed the ucode files. (per the workaround in the bug report)
iwlwifi-3945-1.ucode -> iwlwifi-3945-1.ucode.old
iwlwifi-3945.ucode -> iwlwifi-3945-1.ucode

Rebooted, no go.
Then I changed the file names back to their original names,
Then I did ```
sudo modprobe -r iwl3945
sudo modprobe iwl3945
```

Then```
ifconfig
```
And my wlan0 device was there!!
 
Weird...

I'm not sure what happened, it's working now, though I'm afraid this isn't a permanent solution. Ideas??

---

### Post by chili555 on 2008-06-02
> I'm afraid this isn't a permanent solution. Ideas?? Only one way to find out: reboot. If your interface doesn't come right up, search the logs for clues:```
dmesg | grep iwl
sudo cat /var/log/messages | grep iwl
```*messages* keeps a log for several days, so make note of the most recent entries, not from a few days ago, before you implemented the fix.

---

### Post by fixedgear on 2008-06-02
I, unfortuantly, have to get some work done while it's working.  I'm gonna play with it later today.  At least it's working now :)

Thanks for your help

---

### Post by Chilly_Willy on 2008-06-02
Install the linux-backports-modules-hardy package. It contains a later build of the iwlwifi drivers then the standard in Hardy.

---

### Post by fixedgear on 2008-06-02
I installed the linux-backports-modules-generic.

Hardy wasn't an option in my repository listings...

---

### Post by fixedgear on 2008-06-02
Ok So after lunch, I rebooted.

Startup was the same, error on reading the firmware file for iwlwifi.

tried to ```
sudo modprobe -r iwl3945
sudo modprobe iwl3945
```
No go

So then I renamed the ucode files like I did previously:
iwlwifi-3945-1.ucode -> iwlwifi-3945-1.ucode.old
iwlwifi-3945.ucode -> iwlwifi-3945-1.ucode

Then tried to modprobe again, still no go.

Then I replaced the iwlwifi-3945-1.ucode with the one I downloaded.
I then did a modprobe again, and voila!!  It works.  I rebooted the computer to see if it'd stick, and no! :(
But then after i logged in I was able to succesfully modprobe it again.

Thanks again for your guys help.

---

### Post by Chilly_Willy on 2008-06-03
Which version of ubuntu do you have? 8.04?

---

### Post by fixedgear on 2008-06-03
I'm running 7.10

---

### Post by fixedgear on 2008-06-03
UPDATE:

So far it's been pretty consistent with every reboot I do:```
sudo modprobe -r iwl3945
sudo modprobe iwl3945
iwlist wlan0 scan
```

And it works,

I'm lost when it comes to probing correctly on startup :(

Thanks

---

### Post by chili555 on 2008-06-03
I wonder if *iwl3945* is getting loaded at all when you boot. The next time you boot, please try:```
lsmod | grep iwl
```Is it listed? If not, let's give it a shove. *sudo gedit /etc/modules* and add a single term on its own line:```
iwl3945
```Reboot and see if it's fixed.

---

### Post by fixedgear on 2008-06-03
I have added iwl3945 already to /etc/modules

When I rebooted ```
lsmod | grep iwl3945
```
returned a result
So, I assume that means it loaded something.

I again removed the driver and reloaded it manually using modprobe...and it's working..but my startup still gives me that error I started with at the beginning of the post.

how do I verify that I'm using the latest version of the driver?
I imagine since I downloaded the archive with the ucode file from the website I got the later version.  And I copied it in there... that gives me the latest version...But I might have done something incorrectly.

---

### Post by fixedgear on 2008-06-03
The following is a series of outputs from ```
lsmod | grep iwl
```

Working-Before reboot
```
iwl3945                88168  0 
iwlwifi_mac80211      175112  1 iwl3945
cfg80211                7304  1 iwlwifi_mac80211
```

not working - After reboot
```
iwl3945                88168  0 
iwlwifi_mac80211      175112  1 iwl3945
cfg80211                7304  1 iwlwifi_mac80211
```

Working - After modprobe -r iwl3945 and modprobe iwl3945
```
iwl3945                88168  0 
iwlwifi_mac80211      175112  1 iwl3945
cfg80211                7304  1 iwlwifi_mac80211
```

---

### Post by chili555 on 2008-06-03
Instead of removing and installing a module that is already installed, let's try:```
sudo /etc/init.d/networking restart
```If that does it, you can *sudo gedit /etc/rc.local* and add:```
/etc/init.d/networking restart
```Sudo is not required here. Save and close gedit and reboot. Did your wireless come up?

---

### Post by fixedgear on 2008-06-03
Sorry Chili

That didn't work :(

---

### Post by Quantumstate on 2008-06-03
I had this exact problem with iwl4965. I even tried an ifdown/up in rc.local, which didn't work.

So like a fool, I dutifully reported this in detail on the intellinuxwireless.org bug tracker, along with the very slow communications and dropped connections,  earnestly hoping that the next driver release will fix things.  But the fact is, these same problems have been going on since August of last year! :mad:

Let's think about this for a second.  For as long as I have been fscking around with Intel's rinky-dink iwl4965 toy driver, It has never started the interface on boot, it is slow as Hell, often disconnects, and the fscking blue wireless light doesn't come on!

 Well I just went through the struggle of getting ndiswrapper installed, and what a difference! Everything suddenly works, it is rock-steady, and it is blazing fast! Steady 3.4MB/s, which is about max for G.

 The Linux driver can not be that much different than the Winduhs one. It can not be that much more difficult. It shouldn't be that much more broken. You mean they can't even make the fscking light work?! 

 This why I say Intel is sandbagging the Linux driver. They had made a putsch into becoming a big wifi supplier, but they looked around and saw what happened to Atheros. Atheros wouldn't open their driver for Linux, so some crafty developers came up with the madwifi project, and made it work open-source. It even had Monitor Mode. Well, Intel didn't want that happening to them, so they offered to provide a driver for us... what they don't say is that it is crippled. And those of us with HP or Dell have no choice for wireless card, as the OEM code in the card firmware must be right or the computer won't boot!  That's what we get with oligopolies.  We don't have a Free Market.

 Take my advice: use ndiswrapper and the Winduhs driver for this NIC. The only drawbacks are: 
 - Must set AP broadcast on to associate, in WPA mode, but I'll bet there's a Debian setting to fix that; 
 - Must recompile the ndiswrapper kernel module every time kernel is compiled. 

 To make ndiswrapper work, two differences from the official instructions: 
 - Do NOT put ndiswrapper in /etc/modules . It will load on boot without that.
If you put it in modules, it will hang the kernel. 
 - Edit /etc/modprobe.d/blacklist and add: 
 blacklist iwl4965 
 blacklist iwlwifi_mac80211

So, has anyone gotten ndiswrapper to associate when the AP's broadcast is off (cloaked)?  I have searched far and wide... and specifying wpa-pairwise, wpa-group, wpa-key-mgmt, and wpa-ap-scan... do not work.  

It will not associate with the AP cloaked.

---

### Post by fixedgear on 2008-06-04
Ahhh freaking brilliant!! :)  the ndiswrapper worked!!  It loads on start up and everything! :)

Only it's still trying to load the iwl3945 linux driver still :(  I commented out iwl3945 from /etc/modules 
Is there another spot I should look at for where it's trying to load this driver from?? (or should I just delete the files from /lib/firmware/2.6.22-14-generic


This is my output from dmesg:
```
[   11.736000] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.1.0
[   11.736000] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   11.736000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   11.736000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   11.736000] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   71.736000] iwl3945: iwlwifi-3945-1.ucode firmware file req failed: Reason -2
[   71.736000] iwl3945: Could not read microcode: -2
[   71.736000] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
[   71.736000] iwl3945: probe of 0000:0c:00.0 failed with error -2
[   72.108000] ndiswrapper version 1.45 loaded (smp=yes)
[   72.280000] ndiswrapper: driver netw4x32 (Intel,08/08/2007,11.1.1.22) loaded
[   72.280000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   72.280000] ndiswrapper (NdisWriteErrorLogEntry:192): log: 40001B7C, count: 2, return_address: f8aa55e2
[   72.280000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x56524457
[   72.280000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xe2
[   72.280000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   72.296000] ndiswrapper: using IRQ 17
[   72.572000] wlan0: ethernet device 00:1b:77:85:9c:1c using NDIS driver: netw4x32, version: 0x10016, NDIS version: 0x501, vendor: 'Intel(R) Wireless WiFi Link 3945ABG Driver', 8086:4222.5.conf
[   72.576000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   72.584000] usbcore: registered new interface driver ndiswrapper

```

---

### Post by chili555 on 2008-06-04
I'm very glad it's working for you!

With respect to our esteemed colleague Quantumstate, the original poster was not using the built-in iwl3945 driver. There is none for Ubuntu 7.10. So he installed some hopefully distribution-generic package from somewhere and had a firmware glitch that he had to hack. Perhaps the package developers could share some or all of the blame, rather than Intel.

Many of us have no issues at all with the built-in iwl3945. Mine works perfectly with no ugly hacks.

---

### Post by Quantumstate on 2008-06-04
fixedgear, please re-read the end of my post.

chili, please tell us
- The name, version, and source  of your iwl driver, and your distro?
- When downloading a large file on your LAN what's your speed?
- Does the radio light come on? (if you have one)
- Does the connection ever drop?

---

### Post by chili555 on 2008-06-04
> - The name, version, and source of your iwl driver, and your distro?
- When downloading a large file on your LAN what's your speed?
- Does the radio light come on? (if you have one)
- Does the connection ever drop?*modinfo iwl3945
filename:       /lib/modules/2.6.24-18-generic/updates/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
license:        GPL
author:         Copyright(c) 2003-2007 Intel Corporation
version:        1.2.25

The built-in, comes-with, box-stock version. My distro is Ubuntu Hardy.

*My download speed is the limit that my ISP is paid for. I have never tried to FTP a big file from my wife's machine.

*The radio light comes on but does not flicker with activity; it seems to be an on-off switch; connected=on and disconnected or switched off=off.

*No, unless my ISP is having yet another bad day. In such cases, I cannot blame iwl3945, because my wife, who is connected to the router by ethernet, usually yells, "Are you off line?"

To answer your other unasked questions, it scans, goes into monitor mode and works with Kismet.

I suspect quite a few of these work perfectly; however, people almost never post that things are working perfectly. I also suspect quite a few wireless problems are Network Manager problems. There are hundreds of posts, not just about iwl3945, that are variations of "I select my network, put in my key (I know it's correct, I used it for 900 years in Windows) and it just whirls and asks for my key again. What to do?' Then they go to who-knows-where and install a 2004 vintage driver and report it doesn't work either. The ugly side of me wants to say to them, "Go ask the package developers why it doesn't work. They must have a wiki."

---

### Post by Quantumstate on 2008-06-04
Well, I guess I can't use iwl3945 since I have a 4965, with no other choice.

Does the radio light go off with ifdown?  It shouldn't flicker with activity.

And there must be some mistake about monitor mode, because Intel does not allow that.

As to the package developers, yes they would be responsible to a good degree for install problems, but unlikely for the usability and performance problems that I've described.  If you can make a case otherwise, please do so.  Remember, these are software radios, where much of the functionality is in microcode which is loaded at boot.  Little is done by the actual driver these days.

---

### Post by chili555 on 2008-06-04
> Does the radio light go off with ifdown?No.> And there must be some mistake about monitor mode, because Intel does not allow that.> chili@LAPTOP60:~$ sudo iwconfig eth1 mode monitor
chili@LAPTOP60:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  Nickname:""
          Mode:Monitor  Frequency:2.462 GHz  Tx-Power=20 dBm I had to ifdown eth1 first, and then the only way to get back to Managed is to rmmod and modprobe iwl3945. And, yes, my interface is eth1.

---

### Post by Quantumstate on 2008-06-04
Wul, is the driver from Intel?

If so, why would Monitor be prohibited in iwl4965?

And why is iwl4965 such a mess?

---

### Post by fixedgear on 2008-08-09
Hi everyone again....So, the ndiswrapper thing seemed to work, but the problem I ended up having with the wrapper was that after a couple hours the wireless card would just die.  I ended up reverting back to the orginal "solution" of modprobe -r iwl3945 and modprobe iwl3945.

Basically it's been one of those things where I just deal with it, but I would generally really like to see this thing work from start up without having to unload and reload the driver.

Chilli I know you were helping me quite a bit before...any other ideas??

---

### Post by chmac on 2008-08-11
I've just acquired this problem.

Until I rebooted a few minutes ago, my wireless driver was working fine. I've been running Ubuntu 8.04 for about 3 months and it's been flawless.

From /var/log/messages it looks like I last rebooted on 29 July. I typically suspend / resume. I'm looking through /var/log/dpkg.log for anything suspicious since 29 July, but nothing jumps out at me. I've attached a copy of `grep -E "^[0-9 \:\-]*(upgrade|install)" dpkg.log`.

Any suggestions? Any other logs I should check?

Just to confirm, wifi works if I `sudo modprobe -r iwl3945; sudo modprobe iwl3945` after reboot.

---

### Post by arjmage on 2009-08-27
It looks like this issue is still not resolved. My machine is a dell xps running a wet-eared version of jaunty, with an intel 3945 card built-in.

The wireless was running out of the box in ubuntu, however I faced the said issues of connection dropping off every few minutes and network lag.

So I tried updating the drivers and installed the linux kernel module drivers etc. However, this did not change anything in the performance. Wireless light continued to blink.

So I tried ndiswrapper (via ndisgtk) and used my old XP driver file (which seems the right filename mentioned in some other forums). With/Without adding ndiswrapper to /etc/modules, this led to a system catastrophe -- the system would just freeze (leaving the indicator lights all blinking) and i'd have to force reboot the system. this also occurred with the regular iwl3945 file blacklisted in /etc/modprobe.d/blacklist.

so i turned off the radio switch, rebooted into ubuntu and got rid of the ndiswrapper add-ons. however, the conflict has left my system such that the iwl3945 driver does not load anymore at bootup. 

i have to ```
sudo modprobe iwl3945
``` each time i boot now, in order to enable my wireless.

So ...

1. could somebody tell me how to restore the iwl3945 to loading automagically at startup, without adding the modprobe command into /etc/modules. it wasn't there earlier, so what has changed?

2. can anybody throw some light on related issues  like the stuff in /etc/network/interfaces and modprobe.d

Help much appreciated, as this is only my second forum posting.

---

