---
title: "Nothing showing up in wireless menu"
date: 2018-01-24
forum: Networking &amp; Wireless
---

### Post by maddjak on 2018-01-24
Hello, I recently got a used Lenovo Thinkpad SL510 and I've noticed that I can't get the wifi to work.  Apparently, the wifi was acting up before I got it and it might be the reason the person sold this laptop.  I'm new to Linux so please have patience with me.

---

### Post by chili555 on 2018-01-25
Please start here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by maddjak on 2018-01-26
Done it and still have the problem.

---

### Post by Hadaka on 2018-01-26
Hi, the link chili555 posted is a guide on how to post a diagnostic report
so we may help find a solution to your wifi problem..
Try this method to post a report, Please open a terminal...ctrl/alt/t
then COPY and PASTE the following command...
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
``` 
Then do..
```
cat wireless-info.txt | nc termbin.com 9999
```
This will have an output that looks this...
[http://termbin.com/xxyy](http://termbin.com/xxyy) <- It wont say 'xxyy' it will be something else
copy and paste to your reply.
Thank you

---

### Post by maddjak on 2018-01-26
My computer can't find wireless-info.txt even though I can see the file.

---

### Post by jeremy31 on 2018-01-26
What directory do you see the file in?

---

### Post by Hadaka on 2018-01-26
Hi, let's try this a different way..we'll let the computer do most the work
all you have to do is COPY and PASTE.
please open a terminal ctrl/alt/t then copy and paste this command and press enter..
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
Then copy and paste this command...
```
wit=`sudo find  -name wireless-info.txt`
```
Then copy and paste this command..
```
cat "$wit" | nc termbin.com 9999
```
You will now see a link that looks like this...
[http://termbin.com/xxyy](http://termbin.com/xxyy) <- It wont say 'xxyy' it will be something else
copy and paste the link to your reply.
Thank you

---

### Post by maddjak on 2018-01-26
I got a pastebin link from the first code, but the last code said "cat: 'locate wireless-info.txt': No such file or directory"

The files are located in /home/maddjak/

---

### Post by Hadaka on 2018-01-26
> **maddjak said:**
> I got a pastebin link from the first code, but the last code said "cat: 'locate wireless-info.txt': No such file or directory"

The files are located in /home/maddjak/

Hi, I made a correction on that post, #7 it should work now..please try again.
Thanks

---

### Post by maddjak on 2018-01-26
Came back with "cat: 'sudo find -name wireless-info.txt': No such file or directory"

---

### Post by jeremy31 on 2018-01-26
Please post the results for ```
ls | grep wireless
```
Can you double click on the file and have it open in a text editor?

---

### Post by Hadaka on 2018-01-26
I just copied and pasted the commands from post # 7 and they work
like they are suppose to...please try again and do ALL the commands in post #7

---

### Post by maddjak on 2018-01-26
wireless-info
wireless-info.tar.gz
wireless-info.txt

Yes

---

### Post by maddjak on 2018-01-26
Oh, it worked this time.  No clue what was going wrong.

---

### Post by Hadaka on 2018-01-27
ok, now that you have the file we need..please Copy and paste
and post to us the output of...
```
cat wireless-info.txt | nc termbin.com 9999
```
Thanks

---

### Post by maddjak on 2018-01-27
[http://termbin.com/yeu4](http://termbin.com/yeu4)

---

### Post by Hadaka on 2018-01-27
Great ! data we can work with...thanks .

It looks like you have 2 wireless cards, unusual for a laptop.
There is an intel wireless and a broadcom wireless. Lenovo
usually performs best on the intel card..so let's remove the driver
for the broadcom card and see what happens.
PLEASE copy and paste...
```
sudo modprobe -rf b43
sudo apt-get remove --purge firmware-b43-installer 
```
Next we'll see if we can bring the intel card to life..
Please copy and paste...
```
sudo modprobe -rf iwlwifi
sudo modprobe -v iwlwifi
```
Then...
Unplug the wired connection...boot and test wireless.
Thanks

---

### Post by maddjak on 2018-01-27
Still can't find any networks

---

### Post by Hadaka on 2018-01-27
Hi Please open a terminal then Copy and Paste..
```
echo -e "blacklist b43\nblacklist ssb\nblacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist-broadcom.conf
```
Then do and post the output of..
```
dmesg | grep iwl
```
Thanks.

---

### Post by maddjak on 2018-01-27
[   27.866225] iwlwifi 0000:05:00.0: can't disable ASPM; OS doesn't have ASPM control
[   27.985134] iwlwifi 0000:05:00.0: loaded firmware version 39.31.5.1 build 35138 op_mode iwldvm
[   27.993409] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   27.993412] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   27.993414] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   27.993416] iwlwifi 0000:05:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   28.041922] ieee80211 phy1: Selected rate control algorithm 'iwl-agn-rs'
[   28.534891] iwlwifi 0000:05:00.0 wlp5s0: renamed from wlan0
[   33.252215] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[   33.317820] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[  634.946018] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[  635.010806] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[  636.193109] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[  636.257870] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[ 1043.444055] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[ 1046.388738] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[ 1046.454391] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[ 1715.178166] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[ 1717.939164] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[ 1718.003686] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[ 6950.092122] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[ 6953.035908] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[ 6953.103735] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[ 7050.407953] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[ 7053.196143] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[ 7053.263560] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[ 7080.912018] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[ 7083.782355] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[ 7083.848235] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[17379.002657] Modules linked in: msr uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core videodev media snd_hda_codec_hdmi coretemp kvm irqbypass arc4 iwldvm joydev input_leds serio_raw wmi_bmof b43 bcma lpc_ich mac80211 iwlwifi thinkpad_acpi nvram cfg80211 ssb_hcd snd_hda_codec_realtek snd_hda_codec_generic snd_seq_midi jmb38x_ms snd_hda_intel snd_hda_codec snd_seq_midi_event snd_hda_core snd_hwdep memstick snd_pcm shpchp snd_rawmidi snd_seq snd_seq_device snd_timer snd soundcore mac_hid parport_pc ppdev lp parport autofs4 btrfs xor raid6_pq dm_mirror dm_region_hash dm_log i915 psmouse i2c_algo_bit ahci drm_kms_helper libahci syscopyarea sysfillrect sysimgblt ssb r8169 fb_sys_fops sdhci_pci mii sdhci drm wmi video
[17382.517451] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[17385.349396] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[17385.414908] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[17421.585276] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[17424.341362] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[17424.405896] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[17452.521467] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[17455.307244] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[17455.375516] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[17483.894618] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[17486.740458] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[17486.807163] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[17605.709415] iwlwifi 0000:05:00.0: can't disable ASPM; OS doesn't have ASPM control
[17605.710688] iwlwifi 0000:05:00.0: loaded firmware version 39.31.5.1 build 35138 op_mode iwldvm
[17605.740326] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEBUG disabled
[17605.740329] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[17605.740331] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[17605.740333] iwlwifi 0000:05:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[17605.786335] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[17605.792466] iwlwifi 0000:05:00.0 wlp5s0: renamed from wlan0
[17605.843414] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[17605.910917] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[17643.928832] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[17643.993966] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[17645.445632] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[17645.510897] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[17937.465835] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[17937.529990] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[21660.501731] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[21663.353229] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3
[21663.422931] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x3

---

### Post by Hadaka on 2018-01-27
Thank you for the dmesg information,we are looking through it.
In the mean time, Let's do a little updating and clean up.
Please open a terminal then Copy and paste one command at a time.
This may take a little time if you have not updated lately please be patient.
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove
sudo apt-get autoclean
```
Thank you

---

### Post by maddjak on 2018-01-28
Done

---

### Post by Hadaka on 2018-01-28
Thanks, let's see how things are looking..
*First power the machine off..Let it sit with no power on for 3 minutes
then boot up into Ubuntu as usual. Does this computer have Windows also ?
Next..let's generate a new wireless report..
Please Copy and Paste..
```
sudo rm wireless-info*
```

```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```

```
cat wireless-info.txt | nc termbin.com 9999
```

This will have an output that looks this...
[http://termbin.com/xxyy](http://termbin.com/xxyy) <- It wont say 'xxyy' it will be something else
copy and paste to your reply.
Thank you

---

### Post by maddjak on 2018-01-28
[http://termbin.com/ucn2](http://termbin.com/ucn2)

---

### Post by Hadaka on 2018-01-29
Hi, please answer  a couple questions before we continue.

1. Are you dual booting with windows ?

2. Are you telling the computer to load the b43 module ?

3. Is this computer a laptop ?

4. Are you able to easily remove the broadcom wifi card ?

Thanks.

---

### Post by maddjak on 2018-01-29
1) No
2) I don't know
3) Yes
4) No

---

### Post by Hadaka on 2018-01-29
The b43 driver is loading and the usual suspect files arent doing it.
you say.."idunno"..which mean what ?..let me rephrase my question.
Do you issue a command,insert a disk,insert a usb or have someone
enter a command to load the b43 driver ?? All the b43 modules are
blacklisted so it shouldnt be loading. Please open a terminal and do..
```
sudo modprobe -rf ssb
```
then boot the computer.
and once again run all the commands from post #23
Thanks.

---

### Post by maddjak on 2018-01-29
I have no idea what a b43 driver is or how to use it.  Also, I haven't put anything in the computer yet and I'm the only person with access.

Before reboot:
modprobe: FATAL: Module ssb is in use.

[http://termbin.com/ywm8](http://termbin.com/ywm8)

---

### Post by chili555 on 2018-01-30
We are a bit puzzled as to how the laptop comes with two wireless devices. Did you add the card yourself because the Broadcom wasn't working well? Did it come that way when you bought it? And, scariest of all, did it come that way from the factory???

We see this in your termbin, this is a listing of (barely) available networks nearby.:> ATT5J4a4C3  <MAC 'ATT5J4a4C3' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  [COLOR="#FF0000"]29[/COLOR]      &#9602;___  WPA1 WPA2  no     I get a signal strength over 29 from my neighbor 1/4 mile away!! The low signal strength, no scan results, and no networks showing in Network Manager, while there are no other obvious problems in the logs, suggests to me that the antenna wires are not connected to the Intel card because, of course, they are still attached to the Broadcom!!!

Please help us understand this little puzzle a bit better.

---

### Post by maddjak on 2018-01-30
It came this way, second hand.  That's my houses Wifi, but it shouldn't be that weak.  My PC is using it right now and it isn't having any problems.

---

### Post by jeremy31 on 2018-01-30
Can you get access to the wifi cards and see if the Intel card has antenna wires connected to it?

---

### Post by maddjak on 2018-01-30
Here's a pic I took of my Wifi card:

[https://photos.app.goo.gl/BSiDajBSRpJOR5Mw1](https://photos.app.goo.gl/BSiDajBSRpJOR5Mw1)

---

### Post by chili555 on 2018-01-30
That's the Broadcom: BCM94311. I suggest that you abandon the Intel and get the Broadcom working.```
sudo -i
apt-get install firmware-b43-installer
rm /etc/modprobe.d/blacklist-broadcom.conf
echo "blacklist iwlwifi"  >>  /etc/modprobe.d/blacklist.conf
echo "blacklist iwldvm"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot.

---

### Post by maddjak on 2018-01-30
Rebooted and now my laptop is detecting Wifi.  I connected to my hoses system and disconnected my Ethernet before posting this.

---

### Post by chili555 on 2018-01-30
So, are we all good? Solved??

---

### Post by maddjak on 2018-01-30
Yup.  My guess is that the last owner tried replacing the Wifi card, but didn't set it up properly.  Thanks for all of the help.

---

