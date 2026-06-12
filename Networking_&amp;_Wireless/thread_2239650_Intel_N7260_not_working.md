---
title: "Intel N7260 not working"
date: 2014-08-15
forum: Networking &amp; Wireless
---

### Post by mmcl26554 on 2014-08-15
I have 2 HP laptops (G6 & Envy) one has Win 8.1 (Envy) the other has win 7 (G6).   Both now have Ubuntu 14.04.1 and both have the same WiFi cards.   The Envy works fine, but the G6 does not activate the card.   I have checked /lib/firmware in the G6 and the driver for the card is there.   I have no idea why and I am new to Ubuntu (But learning). So could someone please point me in the right direction to get the card in the G6 to work but please don't assume I know a lot as I don't but I do want to learn.
Michael

---

### Post by mikewhatever on 2014-08-15
How about [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo?](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo?)

---

### Post by varunendra on 2014-08-15
I suggest posting a detailed report to let us see your overall wireless setup. Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by mmcl26554 on 2014-08-15
mikewhatever: I did find out the driver is loaded but the card is disabled there were no solutions given



[COLOR=#DD4814][B]varunendra  

[/B][/COLOR]It didn't work gave the message:

```
unable to resolve host address "[COLOR=#000000][FONT=Ubuntu Mono]dl.dropbox.com"[/FONT][/COLOR]
```
I did verify I typed it correctly so what is plan "B"?
Thanks for help
Michael

---

### Post by varunendra on 2014-08-15
> **mmcl26554 said:**
> so what is plan "B"?

Plan "B" is also mentioned in the same post -
> If you have no way to connect the machine to internet....

---

### Post by mmcl26554 on 2014-08-16
Oh NUTS!  I forgot to connect it to the eithernet cable.   It doesn't get better as you get older.   I'm using the learning of Linux as an exercise for my old brain, I need more work!
Michael

---

### Post by mmcl26554 on 2014-08-16
> **varunendra said:**
> I suggest posting a detailed report to let us see your overall wireless setup. Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.
Here is the results, I just noticed I posted it also on the thread you linked me to so where would you like me to continue on here or there?

---

### Post by chili555 on 2014-08-16
> iwlwifi 0000:01:00.0: RF_KILL bit toggled to disable radio.My buddy Varun wonders if you'd flip the wireless switch to 'On.'

---

### Post by mmcl26554 on 2014-08-16
Additional information and background.   The WiFi card is not the original card for this laptop (I still have the original and it works fine).   When I first installed this N7260 card I was running Ubuntu 12.04.  To get the card to work I had to backport the drivers into the kernel and this worked.   There was an upgrade to the kernel and I had to run backport again and it also worked.   Then there was a very recent kernel upgrade and I had to run backport a 3rd time that didn't work.    I have another hp laptop with this same WiFi card and Ubuntu 14.04 running a dual boot with win8.1 WiFi works fine in that install.  So I dumped 12.04 and did a fresh install of 14.04, but the N7260 card still doesn't work.  Just to make certain it wasn't the card I did a swap of the 2 cards but that didn't help.   The strange thing to me is I have a USB WiFi adapter that doesn't work when the N7260 card is installed but works if I remove it.   I don't understand that at all.
Michael

---

### Post by mmcl26554 on 2014-08-16
> **chili555 said:**
> My buddy Varun wonders if you'd flip the wireless switch to 'On.'
There is no mechanical switch, but there is a button on the F12 key which shows (off) but pressing it makes no difference.   I noticed there is both a hard and soft "Off" but I don't know a way to change it.
Michael

---

### Post by chili555 on 2014-08-16
> **mmcl26554 said:**
> There is no mechanical switch, but there is a button on the F12 key which shows (off) but pressing it makes no difference.   I noticed there is both a hard and soft "Off" but I don't know a way to change it.
MichaelMay we see:```
lsmod
```

---

### Post by mmcl26554 on 2014-08-16
Here it is:

```
Module                  Size  Used bybnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391196  10 bnep,rfcomm
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_idt      54645  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
arc4                   12608  2 
iwlmvm                189774  0 
mac80211              630653  1 iwlmvm
snd_hda_intel          52355  6 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
cryptd                 20359  1 ghash_clmulni_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
rtsx_pci_ms            18151  0 
memstick               16966  1 rtsx_pci_ms
joydev                 17381  0 
iwlwifi               169932  1 iwlmvm
snd                    69238  23 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
serio_raw              13462  0 
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
mei_me                 18627  0 
lpc_ich                21080  0 
soundcore              12680  1 snd
mei                    82276  1 mei_me
wmi                    19177  1 hp_wmi
hp_accel               26012  0 
i915                  783805  3 
lis3lv02d              20156  1 hp_accel
input_polldev          13896  1 lis3lv02d
video                  19476  1 i915
drm_kms_helper         53081  1 i915
hp_wireless            12637  0 
drm                   303102  4 i915,drm_kms_helper
mac_hid                13205  0 
i2c_algo_bit           13413  1 i915
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         23274  0 
psmouse               106678  0 
ahci                   25819  2 
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
libahci                32560  1 ahci
r8169                  67581  0 
mii                    13934  1 r8169



```

---

### Post by chili555 on 2014-08-16
Let's unload one module and see if it helps or hurts:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```If it helps, we'll blacklist it.

---

### Post by mmcl26554 on 2014-08-16
After running:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r hp-wmi[/FONT][/COLOR]
```

The light turned on and it connected so does this need to be blacklisted and how do I do it.   I didn't run the remainder of the commands as the card turn on immediatly.
Michael

---

### Post by mmcl26554 on 2014-08-16
To blacklist it would i go into:  

 ```
[FONT=Ubuntu Mono]/etc/modprobe.d/blacklist.conf[/FONT]
```

And then enter:

```
blacklist [FONT=Ubuntu Mono, Ubuntu Beta Mono A, Consolas, Bitstream Vera Sans Mono, Courier New, Courier, monospace]hp-wmi[/FONT]
```

---

### Post by chili555 on 2014-08-16
> **mmcl26554 said:**
> To blacklist it would i go into:  

 ```
[FONT=Ubuntu Mono]/etc/modprobe.d/blacklist.conf[/FONT]
```

And then enter:

```
blacklist [FONT=Ubuntu Mono, Ubuntu Beta Mono A, Consolas, Bitstream Vera Sans Mono, Courier New, Courier, monospace]hp-wmi[/FONT]
```Exactly! You should be all set.

---

### Post by mmcl26554 on 2014-08-16
Yea!  I'm learning, google is certainly my friend.   I'll do the change after dinner and report back and if all goes as expected mark this thread as solved.    Can you tell me what the hp-wmi to prevent the card from turning on?
Michael

---

### Post by mmcl26554 on 2014-08-16
Nuts!  didn't work and none of the commands you suggested work now and the hard block is back on

---

### Post by chili555 on 2014-08-16
After you rebooted or...what? Let's see:```
cat /etc/modprobe.d/blacklist.conf | tail -n3
lsmod | grep wmi
```

---

### Post by mmcl26554 on 2014-08-16
After I setup the blacklist I rebooted and now it isn't working again, here are the results:
```
# really needed.blacklist amd76x_edac
blacklist hp-wmi
michael@G6:~$ lsmod | grep wmi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    69238  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
wmi                    19177  0 
```

---

### Post by chili555 on 2014-08-16
Hmmmm, looks good so far. Now how about:```
rfkill list all
sudo rfkill unblock all
rfkill list all
dmesg | grep iwl
```

---

### Post by mmcl26554 on 2014-08-16
Here we are:

```
michael@G6:~$ rfkill list all0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
michael@G6:~$ sudo rfkill unblock all
[sudo] password for michael: 
michael@G6:~$ dmesg | grep iwl
[   14.146796] iwlwifi 0000:01:00.0: irq 45 for MSI/MSI-X
[   14.337667] iwlwifi 0000:01:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[   14.354743] iwlwifi 0000:01:00.0: Detected Intel(R) Wireless N 7260, REV=0x144
[   14.354826] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[   14.355097] iwlwifi 0000:01:00.0: RF_KILL bit toggled to disable radio.
[   14.355120] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[   14.367919] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
michael@G6:~$ 



```

---

### Post by chili555 on 2014-08-16
This is crazy, but, then again, you have a crazy problem:```
sudo modprobe hp-wmi
sudo modprobe -r hp-wmi
rfkill list all
```

---

### Post by mmcl26554 on 2014-08-16
No change still hard blocked=yes

---

### Post by mmcl26554 on 2014-08-16
What about this copy of an ask ubuntu post?

 ```
[COLOR=#333333][FONT=UbuntuRegular]Although you didn't confirm it from dmesg, it appears you need and lack the required firmware. Here is a link from my Dropbox: [/FONT][/COLOR][https://dl.dropboxusercontent.com/u/58267392/iwlwifi-7260-7.ucode.zip](https://dl.dropboxusercontent.com/u/58267392/iwlwifi-7260-7.ucode.zip)[COLOR=#333333][FONT=UbuntuRegular] Please download it to your desktop. Right-click and select 'Extract Here.' Now open a terminal and do:[/FONT][/COLOR]sudo cp Desktop/iwlwifi-7260-7.ucode /lib/firmware/
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
[COLOR=#333333][FONT=UbuntuRegular]Do you have a wireless interface now?[/FONT][/COLOR]
iwconfig
[COLOR=#333333][FONT=UbuntuRegular]Does it connect? Are there any informative messages here?[/FONT][/COLOR]
[FONT=Ubuntu Mono]dmesg | grep iwl[/FONT]
```

---

### Post by chili555 on 2014-08-16
Please remove the blacklist and reboot. Then:```
sudo modprobe -r hp-wmi
```I wonder if we must unload it after it is first loaded during boot. I love/hate a mystery!

---

### Post by chili555 on 2014-08-16
> **mmcl26554 said:**
> What about this copy of an ask ubuntu post?

 ```
[COLOR=#333333][FONT=UbuntuRegular]Although you didn't confirm it from dmesg, it appears you need and lack the required firmware. Here is a link from my Dropbox: [/FONT][/COLOR][https://dl.dropboxusercontent.com/u/58267392/iwlwifi-7260-7.ucode.zip](https://dl.dropboxusercontent.com/u/58267392/iwlwifi-7260-7.ucode.zip)[COLOR=#333333][FONT=UbuntuRegular] Please download it to your desktop. Right-click and select 'Extract Here.' Now open a terminal and do:[/FONT][/COLOR]sudo cp Desktop/iwlwifi-7260-7.ucode /lib/firmware/
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
[COLOR=#333333][FONT=UbuntuRegular]Do you have a wireless interface now?[/FONT][/COLOR]
iwconfig
[COLOR=#333333][FONT=UbuntuRegular]Does it connect? Are there any informative messages here?[/FONT][/COLOR]
[FONT=Ubuntu Mono]dmesg | grep iwl[/FONT]
```As you can see, it found and loaded the required firmware:```
michael@G6:~$ dmesg | grep iwl
[   14.146796] iwlwifi 0000:01:00.0: irq 45 for MSI/MSI-X
[   14.337667] iwlwifi 0000:01:00.0: [COLOR="#FF0000"]loaded firmware version 22.24.8.0 op_mode iwlmvm[/COLOR]
[   14.354743] iwlwifi 0000:01:00.0: Detected Intel(R) Wireless N 7260, REV=0x144
[   14.354826] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[   14.355097] iwlwifi 0000:01:00.0: RF_KILL bit toggled to disable radio.
[   14.355120] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[   14.367919] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
```

---

### Post by mmcl26554 on 2014-08-16
I commented out the blacklist with (#) shut down the computer, rebooted and then ran the
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r hp-wmi[/FONT][/COLOR]
```
Nothing!

---

### Post by chili555 on 2014-08-16
Please tell me more about the computer. I understand it's an HP, but what is the exact model?

---

### Post by mmcl26554 on 2014-08-16
Pavilion G6 Win 7 dual boot with Ubuntu 14.04.  Before I had 12.04 on in and the last kernel and the one before that the card worked fine after I did a back port with backports-3.11-rc3-1 but the most recent kernel the backporting has error messages and the card doesn't work.  I have copied from the service manual some info about what it has, but the WiFi card is not what originally came with the laptop.

---

### Post by chili555 on 2014-08-16
> but the most recent kernel the backporting has error messages and the 7260 card doesn't work. I don't understand. In the kernel version in 14.04, the card should work without building any backports package. Doesn't it?

Is this the only wireless control? [http://h30434.www3.hp.com/t5/image/serverpage/image-id/64315i172085DB57D2F4AB/image-size/medium?v=mpbl-1&px=-1](http://h30434.www3.hp.com/t5/image/serverpage/image-id/64315i172085DB57D2F4AB/image-size/medium?v=mpbl-1&px=-1)  With hp-wmi removed, does the button press do anything or change this?```
rfkill list all
```What was wrong with the original wireless card?

---

### Post by mmcl26554 on 2014-08-16
Well actually there is nothing wrong with the original card except this one has bluetooth also should I want to use it.   Right now I am under win7 to get the additional info so can't run the command you want.  I'll reboot and go back to ubuntu and give you the answer.

---

### Post by mmcl26554 on 2014-08-16
```
michael@G6:~$ rfkill list all0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes



```
The only reason I tried the backporting on 14.04 is the card didn't work and that had fixed it on the previous kernels.    I suppose I could go back to an older kernel, as there must be something wrong with the driver in this one.   If you think a reinstall of 14.04 would work I can do it as this is just an experimental OS at the moment, or I could go back to 12.04.

---

### Post by chili555 on 2014-08-16
> **mmcl26554 said:**
> ```
michael@G6:~$ rfkill list all0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes



```
The only reason I tried the backporting on 14.04 is the card didn't work and that had fixed it on the previous kernels.    I suppose I could go back to an older kernel, as there must be something wrong with the driver in this one.   If you think a reinstall of 14.04 would work I can do it as this is just an experimental OS at the moment, or I could go back to 12.04.Backports was required to get the device working in older kernels because this relatively new device wasn't covered in older kernels. In other words, the 12.04 kernel was built before Intel ever breathed the words '7260 AC.' However, in the latest kernels, it is covered and so backports is unnecessary and, possibly, a hindrance. Didn't the 7260 work out of the box in 14.04?

Does the old card suffer rfkill issues?

Please see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1342703](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1342703)

Off for the evening. I will study this tomorrow after a nights sleep.

---

### Post by mmcl26554 on 2014-08-17
It has not worked since the latest kernel update, I don't know the number but I was running 12.04 at the time I think the last kernel was 3.11 or possibly the one before that.  In any case I had to do backport and that made it work.   All I know is I did get a kernel update, the card stopped working and I did backport and it worked.  Then there was another update and it didn't work, I did the backport and it still didn't work.  When I booted with the old kernel it worked again.    You may be confused by the fact that I have another HP laptop an Envy.   It has the same card and it worked fine out of the box, but the G6 doesn't work.  The thing that is even stranger to me is if I plug in my USB wireless card it won't work either, unless I remove the 7260 card then it works fine.   I don't understand that.   It seems the 7260 causes a block to all wireless cards.    I'll watch for a post from you.   This issue is not an urgent one as this is my backup computer and I don't use it much, so this is a curiosity more than anything else.   I'd like to find out what is going on and fix it instead of just putting the old card in.   The 7260 works ok with win7 and win 8.1 and on the HP Envy with Ubuntu 14.04 and at one time worked with the G6 with 12.04 and backporting.   So it must work!   I suppose I could roll back to a kernel that worked and use that with 14.04 of that is possible, but again that is a workaround and not a solution.
Thank you for taking the time to help me out with this, I hope the satisfaction of success will make it all worth while for you.
Michael

---

### Post by mmcl26554 on 2014-08-17
I did a fresh install of Ubuntu 14.04 just in case my attempt at backporting messed things up.  But it still will not turn on.
Michael

---

### Post by jeremy31 on 2014-08-17
Have you done any BIOS updates/modifications on the G6?  I am asking that because a search for that model shows a lot of them that have whitelisted BIOS and if you don't use the right hardware, it won't work

---

### Post by varunendra on 2014-08-17
> **mmcl26554 said:**
> I did a fresh install of Ubuntu 14.04....

Then please also post a fresh report of the wireless_script, to show us the fresh status to work on. This one of course : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by mmcl26554 on 2014-08-17
> **jeremy31 said:**
> Have you done any BIOS updates/modifications on the G6?  I am asking that because a search for that model shows a lot of them that have whitelisted BIOS and if you don't use the right hardware, it won't work

I have only done bios updates that HP has recommended as the win7 OS has their management software and will notify me if there are any.
However, the N7260 card works fine under Win7, although I had to install the latest driver for it from Intel.  Just an aside here, my other HP laptop which came natively with this card had problems of the card shutting down when inactive for a while, all settings were set to prevent this but it would still do it after a few hours.  I installed the same newer driver from Intel and it cured that problem.   The card did work under Ubuntu 12.04 with an older kernel that was backported with the driver for the 7260 card.  So not long ago it worked fine, until the most recent kernel was updated to 12.04.   I think there is something wrong with the driver in the most recent kernel.   If I could delete the driver from the recent kernel and then backload (or something like that) the driver that works that may resolve the issue, but I am certainly not Ubuntu savvy enough to do that or don't even know if it can be done.   Maybe there is something else in the kernel that is turning the card off.
Michael

---

### Post by varunendra on 2014-08-17
Please post the script report I asked for in my post above, plus the output of -
```
sudo lshw -C network | grep firmware
```
..so we can see which version of the firmware you have. There is a recommended combination of driver/firmware versions as mentioned here : [http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm](http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm)

---

### Post by mmcl26554 on 2014-08-17
> **varunendra said:**
> Please post the script report I asked for in my post above, plus the output of -
```
sudo lshw -C network | grep firmware
```
..so we can see which version of the firmware you have. There is a recommended combination of driver/firmware versions as mentioned here : [http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm](http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm)
I have attached the new file and here is the info:
```
michael@G6:~$ sudo lshw -C network | grep firmware       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-32-generic firmware=22.24.8.0 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.0.62 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s



```

---

### Post by jeremy31 on 2014-08-18
Looks like you should be able to unplug the ethernet cable and connect with wifi

---

### Post by chili555 on 2014-08-18
> **jeremy31 said:**
> Looks like you should be able to unplug the ethernet cable and connect with wifiYes, indeed! Notice the wireless is no longer blocked:> rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no
2: hci0: Bluetooth         no            no
     

---

### Post by mmcl26554 on 2014-08-18
> **chili555 said:**
> Yes, indeed! Notice the wireless is no longer blocked:

That was the good news, but now for the bad news.  I rebooted the computer and it is now blocked again.   I ran rfkill unblock all and it is still blocked.   I ran the script again and it is attached. By the way how do I clear out old attachments?

---

### Post by varunendra on 2014-08-19
> **mmcl26554 said:**
> That was the good news, but now for the bad news.  I rebooted the computer and it is now blocked again.
But in the report you are connected via ethernet again. Reboot without the Ethernet plugged in, and if it remains hard-blocked, run the script without plugging in the Ethernet. (simply run "./wireless_script" in a terminal if you used the commandline method earlier).

> **mmcl26554 said:**
> By the way how do I clear out old attachments?
If you mean the attachments in the older posts, you shouldn't. They serve as a record of progress and are helpful to track and 'learn' the progress later. Clearing (deleting) them would confuse users and troubleshooters who may try to follow the thread at later dates. Older posts should be edited ONLY if really necessary (to correct mistakes, or to update them IF they are guide/tutorial posts).

However, if you mean those in your computer, simply delete them?

If the wireless remains blocked even after disconnecting the Ethernet and rebooting, I would try some blind shots (probably stupid shots), like trying an older firmware ([this one]("http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-7260-ucode-22.15.8.0.tgz") or some others if available) and "power_scheme=1" parameter with "iwlmvm" module. Basically this would be the procedure -

Try the less drastic option first, that is, using the driver parameter -
```
echo "options iwlmvm power_scheme=1" | sudo tee /etc/modprobe.d/iwlmvm.conf
```
Reboot and see if it did the miracle. If not, try the more drastic one (also including steps to safely revert if it doesn't work) -

[indent]**1)** Download this firmware from Intel's site : [http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-7260-ucode-22.15.8.0.tgz](http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-7260-ucode-22.15.8.0.tgz)

**2)** Copy/move it to your Desktop > Right-click it > Extract here.

**3)** Open a terminal, and backup your current firmware in your Home directory with this command -
```
sudo mv **[COLOR="#0000FF"]/lib/firmware/iwlwifi-7260-7.ucode[/COLOR] iwlwifi-7260-7.ucode.bak**
```

**4)** Copy the new firmware downloaded and extracted in step 2 above -
```
sudo cp **Desktop/iwlwifi-7260-ucode-22.15.8.0/iwlwifi-7260-8.ucode [COLOR="#0000FF"]/lib/firmware/iwlwifi-7260-[COLOR="#FF0000"]7[/COLOR].ucode[/COLOR]**
```
Note that we also changed the name iwlwifi-7260-**[COLOR="#0000FF"]8[/COLOR]**.ucode to "iwlwifi-7260-**[COLOR="#FF0000"]7[/COLOR]**.ucode" while copying it, because the driver expects "7" in the version number. So we are kinda fooling the driver which it may not like, in which case, we'll have to restore the original firmware we backed up in step 3 above.[/indent]

Reboot, and see if the situation becomes any better or worse. If worse, simply restore the older firmware with -
```
sudo rm /lib/firmware/iwlwifi-7260-7.ucode
sudo cp **iwlwifi-7260-7.ucode.bak [COLOR="#0000FF"]/lib/firmware/iwlwifi-7260-7.ucode[/COLOR]**
```

Since we can revert both these changes easily, I suggest you try them and report back as soon as you get the chance, so we can move forward when dr. chili comes back.

---

### Post by mmcl26554 on 2014-08-20
I will do these things within the next 2 days I have another home project to complete (honey-do)
michael

---

### Post by mmcl26554 on 2014-08-22
No luck made no difference!  I have also included the wireless script results without the Ethernet.  And before I made any changes.  I'll send another reply with it after the changes.

---

### Post by mmcl26554 on 2014-08-22
Here is the after changes.

---

### Post by jeremy31 on 2014-08-22
Last ditch effort is ```
sudo modprobe -rv hp_wmi
``` and see if it works

I have 2 different 7260 cards working on Linux mint 17 and/or Ubuntu 14.04 so it almost has to be an issue with a model specific module

---

### Post by mmcl26554 on 2014-08-22
> **jeremy31 said:**
> Last ditch effort is ```
sudo modprobe -rv hp_wmi
``` and see if it works

I have 2 different 7260 cards working on Linux mint 17 and/or Ubuntu 14.04 so it almost has to be an issue with a model specific module

Jeremy,
Actually that was done, one time it worked, turned the WiFi light white and activated the card, then did a reboot and the card was disabled and  the command didn't fix it and hasn't done so since.   I also have another HP laptop with this same card in and Ubuntu 14.04 and it works fine.   The strangest part of this is that the card worked fine with Ubuntu 12.04 and an older kernel that was backported.  Then the kernel was updated and it stopped working.   Since the card was working on my other laptop with 14.04 I did a fresh install of 14.04 fully expecting it to work, it didn't.   I even tried swapping the cards between the 2 computer in the chance it was a card problem, it wasn't.    So I have to think there is something about the recent kernel and my HP G6 laptop.   In addition to this a USB WiFi card won't work either unless I remove the N7260.   I am by no way any kind of expert with Ubuntu, Linux or Windows.   But I'm learning this all seems very strange to me.
Michael

---

### Post by mmcl26554 on 2014-08-22
> **jeremy31 said:**
> Last ditch effort is ```
sudo modprobe -rv hp_wmi
``` and see if it works

I have 2 different 7260 cards working on Linux mint 17 and/or Ubuntu 14.04 so it almost has to be an issue with a model specific module
Jeremy,
I just noticed the command you proposed was slightly different from the one chilli had me do. Yours has ```
-rv
```
and the other has just ```
-r
```
What is the difference?   I'll try yours and see what happens.
Michael

---

### Post by varunendra on 2014-08-22
> **mmcl26554 said:**
> Jeremy,
I just noticed the command you proposed was slightly different from the one chilli had me do. Yours has ```
-rv
```
and the other has just ```
-r
```
What is the difference?
No difference in what it does, only difference in what it shows. Without the "-v", it does its job silently in the background. With -v, it shows on the terminal what it is doing (v=verbose).

You can always check the 'manpage' (manual page) of commands to see what options are available and what they do. For example -
```
man modprobe
```

As for the problem, no further ideas, at least not right now. :|

---

### Post by mmcl26554 on 2014-08-22
Do you expect Dr Chilli have more ideas or are we at an end?    Is it possible to go back to a kernel what it worked with using backport?   Or is that not possible with 14.04, or just a bad idea?    I think it was working with 3.11 but not with 3.13.   I do have a backup of 12.04 with the older kernel and just install it.   Or put the original WiFi card which it does work with.   But I'm really curious just what the problem is.    
Michael

---

### Post by jeremy31 on 2014-08-23
It could be some weird issue with BIOS.  I would be interested to know if toggling wifi off in windows would make it work in Ubuntu

Or you could try a kernel parameter in grub ```
sudo gedit /etc/default/grub
```
Find the line that should be ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` And change it to  ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
```
Save, exit gedit and ```
sudo update-grub
``` reboot

It is possible to use a different kernel but there are a few downsides

---

### Post by chili555 on 2014-08-23
> Do you expect Dr Chilli have more ideas or are we at an end? HP are well-known to whitelist wireless cards, however, if an unauthorized card is inserted, the OS won't even load, as here: [http://www.prolixium.com/images/mynews/1802.jpg](http://www.prolixium.com/images/mynews/1802.jpg)

[http://h30434.www3.hp.com/t5/Hardware-Upgrades-Replacements/HP-notebook-wifi-whitelist-card-upgrade/td-p/902429](http://h30434.www3.hp.com/t5/Hardware-Upgrades-Replacements/HP-notebook-wifi-whitelist-card-upgrade/td-p/902429)

Since the old card works well and the new Intel 7260 won't unblock no matter what we try, I am beginning to suspect that the whitelist process is at work here. 

The only three ideas I have are to try resetting the BIOS to defaults, to try an updated BIOS version and, if both fail, put the old card back in.

Jeremy, Varun and I try to solve 99% of all problems 99% of the time, but there is always that 1%. I'm sorry I have no other suggestions.

---

### Post by mmcl26554 on 2014-08-23
> **jeremy31 said:**
> It could be some weird issue with BIOS.  I would be interested to know if toggling wifi off in windows would make it work in Ubuntu

Or you could try a kernel parameter in grub ```
sudo gedit /etc/default/grub
```
Find the line that should be ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` And change it to  ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
```
Save, exit gedit and ```
sudo update-grub
``` reboot

It is possible to use a different kernel but there are a few downsides


When I was using 12.04 I could choose one of the older kernels which was backported and the current one which was not.  The card worked with the older kernel and not with the new one.   I noticed there was a new kernel released recently which I haven't yet done with that computer  It might be possible that somewhere down the road the thing will begin to work.    Jeremy, I'll try what you suggest and disable the card under windows first Michael.

---

### Post by mmcl26554 on 2014-08-23
> **chili555 said:**
> HP are well-known to whitelist wireless cards, however, if an unauthorized card is inserted, the OS won't even load, as here: [http://www.prolixium.com/images/mynews/1802.jpg](http://www.prolixium.com/images/mynews/1802.jpg)

[http://h30434.www3.hp.com/t5/Hardware-Upgrades-Replacements/HP-notebook-wifi-whitelist-card-upgrade/td-p/902429](http://h30434.www3.hp.com/t5/Hardware-Upgrades-Replacements/HP-notebook-wifi-whitelist-card-upgrade/td-p/902429)

Since the old card works well and the new Intel 7260 won't unblock no matter what we try, I am beginning to suspect that the whitelist process is at work here. 

The only three ideas I have are to try resetting the BIOS to defaults, to try an updated BIOS version and, if both fail, put the old card back in.

Jeremy, Varun and I try to solve 99% of all problems 99% of the time, but there is always that 1%. I'm sorry I have no other suggestions.

Well I guess there's more than one way ($$$$) to be a member of the 1%.    I have found out that HP really makes poor quality Laptops.   Under warranty  they have sent me 5 different model computers to replace ones that had unresolvable problems.   The current one (not the one I am having problems with) still has some problems.    So I have just given up on them.   The one I am having problems with is one they replaced but never sent me a box to ship it back so it turned out to be a gift so I guess I cannot complain.    The card works fine under windows7 .    So if I want to use Ubuntu and have WiFi I'll have to use an older kernel.  So for this I see 2 options.   Install the backup of 12.04 or just install an older kernel with 14.04.   Which is best?   And of course there is always the option of going back to the original card.
Michael

---

### Post by chili555 on 2014-08-23
My suggestion is to download the iso for 12.04 which is the earliest that I think is available. Run a live session and see if the wireless works. Check:```
rfkill list all
```If it is not hard blocked, then the wireless can be coaxed to life.

I will be fascinated to hear your report.

[http://old-releases.ubuntu.com/releases/12.04.0/](http://old-releases.ubuntu.com/releases/12.04.0/)

---

### Post by mmcl26554 on 2014-08-23
I can answer that question now.   The N7260 card did work under 12.04 with an older Kernel, but I had to load a backport here is the forum which had the backport data:

[HTML]http://askubuntu.com/questions/322511/no-wireless-with-intel-centrino-advanced-n-7260[/HTML]

With the older kernel I think prior to 3.11 it worked just fine, only after kernel 3.13 was loaded did it stop working and backporting didn't work.  So there is a way to get it to work under Ubuntu, but not with the most current kernels.
Michel

---

### Post by chili555 on 2014-08-23
> **mmcl26554 said:**
> I can answer that question now.   The N7260 card did work under 12.04 with an older Kernel, but I had to load a backport here is the forum which had the backport data:

[HTML]http://askubuntu.com/questions/322511/no-wireless-with-intel-centrino-advanced-n-7260[/HTML]

With the older kernel I think prior to 3.11 it worked just fine, only after kernel 3.13 was loaded did it stop working and backporting didn't work.  So there is a way to get it to work under Ubuntu, but not with the most current kernels.
MichelWho was the genius that wrote that? Isn't he a bit suspect??

I suggest you try 3.11.1 here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.1-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.1-saucy/) Be sure to install the linux-image, headers and headers-all. Reboot, grab the GRUB menu with the Shift key as you are booting and arrow down to 3.11.1 and select it. [http://www1.khax.net/wp-content/uploads/2009/02/grub-image-menu.png](http://www1.khax.net/wp-content/uploads/2009/02/grub-image-menu.png) Yes, these are different kernel versions, but I hope you get the process.

See if the wireless works. If not, run:```
lspci -nn | grep 0280
```Find out the pci.id, like mine:```
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [[COLOR="#FF0000"]8086:4239[/COLOR]] (rev 35)
```Then run:```
modinfo iwlwifi | grep 4239
```Of course, substitute your ID as it is surely not 4239. We want to see if the version of iwlwifi in 3.11.1 covers your exact device.

This is all a bit experimental. Your mileage may vary. Don't try this at home. I am not a lawyer. You have been disclaimered!!!

---

### Post by jeremy31 on 2014-08-23
> **mmcl26554 said:**
> 

With the older kernel I think prior to 3.11 it worked just fine, only after kernel 3.13 was loaded did it stop working and backporting didn't work.  So there is a way to get it to work under Ubuntu, but not with the most current kernels.
Michel
The likely reason it worked by backporting when it did is because the needed module(iwlmvm) and firmware was included in kernels 3.10 and newer

I would file a bug report on this because it won't be fixed if nobody knows it is broken.
Your laptop didn't originally have a wifi card with WiMax?

---

### Post by mmcl26554 on 2014-08-23
I was wondering about a bug report myself,   The original card was an: RAlink RT5390,   I don't know what WiMax is though.    I'm going to install an older kernel as Dr Chilli has suggested and if that fixed most certainly do a bug report.
Michael

---

### Post by mmcl26554 on 2014-08-25
My laptop has been on suspension since my last post, when I woke it up the wireless light was white (meaning it is working).   I haven't  rebooted it but I suspect it won't survive.  But I will try it now just to see what happens.

---

### Post by mmcl26554 on 2014-08-25
> **chili555 said:**
> Who was the genius that wrote that? Isn't he a bit suspect??

I suggest you try 3.11.1 here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.1-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.1-saucy/) Be sure to install the linux-image, headers and headers-all. Reboot, grab the GRUB menu with the Shift key as you are booting and arrow down to 3.11.1 and select it. [http://www1.khax.net/wp-content/uploads/2009/02/grub-image-menu.png](http://www1.khax.net/wp-content/uploads/2009/02/grub-image-menu.png) Yes, these are different kernel versions, but I hope you get the process.

See if the wireless works. If not, run:```
lspci -nn | grep 0280
```Find out the pci.id, like mine:```
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [[COLOR=#FF0000]8086:4239[/COLOR]] (rev 35)
```Then run:```
modinfo iwlwifi | grep 4239
```Of course, substitute your ID as it is surely not 4239. We want to see if the version of iwlwifi in 3.11.1 covers your exact device.

This is all a bit experimental. Your mileage may vary. Don't try this at home. I am not a lawyer. You have been disclaimered!!!

Well nothing worked!  I even installed 3.08 Kernel and backported it but that didn't work.   So I'll guess I install the original card and report a possible bug.
Thank you all for your kind assistance.
Michael

---

