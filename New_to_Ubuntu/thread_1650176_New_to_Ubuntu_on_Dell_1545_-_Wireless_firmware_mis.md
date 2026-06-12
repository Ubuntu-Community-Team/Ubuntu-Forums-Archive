---
title: "New to Ubuntu on Dell 1545 - Wireless firmware missing"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by aroonchand on 2010-12-21
Hi folks,
I recently decided to move from Vista to Ubuntu.
So, I am completely new to Ubuntu and linux and i am not a techie.
The problem is:
After installing Ubuntu 10.10 on Dell inspiron 1545, I cannot connect to wireless network.
The wireless connection option (on the right hand top corner says "Firmware missing").
I read about this problem in google, but I cannot understand what they ask me to do...
One information I can give you is, when i type "lspci" in terminal, the last line says:

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

I have access to internet through Macbook. I do not have wired internet connection...

Can someone help me fix this problem?
I tried several links, including the broadcom... But the language they used and codes they provided, as a beginner, are frustrating to me :confused:

Thanks for your help.

---

### Post by Sealbhach on 2010-12-21
Go to the menu and look in System/Administration/Hardware Drivers. If there is a driver available there, activate it.

.

---

### Post by aroonchand on 2010-12-21
> **Sealbhach said:**
> Go to the menu and look in System/Administration/Hardware Drivers. If there is a driver available there, activate it.

.
Thank you for replying me...
I went there and it has no drivers listed :(

---

### Post by Sealbhach on 2010-12-21
Are you connected to the internet with a wired connection?

.

---

### Post by amsterdamharu on 2010-12-21
Your BCM4312 has a package available for it but I think it will try to get drivers from the internet at is depends on wget.

What version of Ubuntu did you Install (This one is for maverick)?

[http://packages.ubuntu.com/maverick/kernel/firmware-b43-lpphy-installer](http://packages.ubuntu.com/maverick/kernel/firmware-b43-lpphy-installer)

---

### Post by amsterdamharu on 2010-12-21
Ok, I see now it does try to connect to the internet. Download the package for your version (I assume you have maverick). Copy it to your Ubuntu machine and double click it. Don't install it but look if you get any dependency errors.

If you don't then download the following:
[http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
Copy that to your desktop of the Ubuntu machine and copy and paste the following commands in a terminal:
```
cd ~/Desktop
sudo tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```

---

### Post by aroonchand on 2010-12-21
Thank you... I will try this now.
I dont have access to wired internet connection :(

---

### Post by aroonchand on 2010-12-21
> **amsterdamharu said:**
> Your BCM4312 has a package available for it but I think it will try to get drivers from the internet at is depends on wget.

What version of Ubuntu did you Install (This one is for maverick)?

[http://packages.ubuntu.com/maverick/kernel/firmware-b43-lpphy-installer](http://packages.ubuntu.com/maverick/kernel/firmware-b43-lpphy-installer)

Yes, I am using Ubuntu 10.10...
In the above link, which one should I install?

---

### Post by amsterdamharu on 2010-12-21
This link will work, download the file, copy to Ubuntu and double click on it to see if you get any errors (don't install the installer tries to download something from the internet)

The link will open a mirror list, any link on that page should give you the same file.

[http://packages.ubuntu.com/maverick/all/firmware-b43-lpphy-installer/download](http://packages.ubuntu.com/maverick/all/firmware-b43-lpphy-installer/download)

---

### Post by aroonchand on 2010-12-21
> **amsterdamharu said:**
> This link will work, download the file, copy to Ubuntu and double click on it to see if you get any errors (don't install the installer tries to download something from the internet)

The link will open a mirror list, any link on that page should give you the same file.

[http://packages.ubuntu.com/maverick/all/firmware-b43-lpphy-installer/download](http://packages.ubuntu.com/maverick/all/firmware-b43-lpphy-installer/download)


I took the one from:
mirror.pnl.gov/ubuntu/
and copied it to ubuntu desktop.

I ran all the commands, when I run the below one:
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o

i get error:

sudo: b43-fwcutter: command not found

---

### Post by amsterdamharu on 2010-12-21
This link will work, download the file, copy to Ubuntu and [COLOR=Red]double click  on it to see if you get any errors[/COLOR] (don't install the installer tries to  download something from the internet)

The link will open a mirror list, any link on that page should give you the same file.

[http://packages.ubuntu.com/maverick/...aller/download]("http://packages.ubuntu.com/maverick/all/firmware-b43-lpphy-installer/download")


[COLOR=Red]If it doesn't give any errors [/COLOR]

....


So does double clicking on the .deb file give you any errors or not?

---

### Post by aroonchand on 2010-12-21
> **amsterdamharu said:**
> This link will work, download the file, copy to Ubuntu and [COLOR=Red]double click  on it to see if you get any errors[/COLOR] (don't install the installer tries to  download something from the internet)

The link will open a mirror list, any link on that page should give you the same file.

[http://packages.ubuntu.com/maverick/...aller/download]("http://packages.ubuntu.com/maverick/all/firmware-b43-lpphy-installer/download")


[COLOR=Red]If it doesn't give any errors [/COLOR]

....


So does double clicking on the .deb file give you any errors or not?


I copied the file "**firmware-b43-lpphy-installer_4.174.64.19-4_all.deb"**


to ubuntu desktop and double clicked.
It tried to install something and I get the message "An unhandled error occured
there seems to be a programming error in aptdaemon, the dftware that allows you to install/remove software and t perform other package management related tasks. please report this error at [http://launchpad.net/aptdae,om/+filebug](http://launchpad.net/aptdae,om/+filebug) and retry"

---

### Post by Sealbhach on 2010-12-21
Weird.

do 
```

sudo dpkg -i firmware-b43-lpphy-installer_4.174.64.19-4_all.deb
```

.

---

### Post by migs73 on 2010-12-21
> **amsterdamharu said:**
> Ok, I see now it does try to connect to the internet. Download the package for your version (I assume you have maverick). Copy it to your Ubuntu machine and double click it. Don't install it but look if you get any dependency errors.

If you don't then download the following:
[http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
Copy that to your desktop of the Ubuntu machine and copy and paste the following commands in a terminal:
```
cd ~/Desktop
sudo tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```

ARRONCHAD, **do not do this** I am making a suggestion that may not be correct, please wait on amterdamharu's response*******

**Amsterdamharu**; Should there not be a 'make' command after cd'ing to the 'broadcom-wl-4.178.10.4/linux', before trying to run b43-fwcutter?

Mike

---

### Post by aroonchand on 2010-12-21
> **Sealbhach said:**
> Weird.

do 
```

sudo dpkg -i firmware-b43-lpphy-installer_4.174.64.19-4_all.deb
```.

                 fidu@fidu:~$ cd ~/Desktop
fidu@fidu:~/Desktop$ sudo dpkg -i firmware-b43-lpphy-installer_4.174.64.19-4_all.deb
(Reading database ... 118297 files and directories currently installed.)
Preparing to replace firmware-b43-lpphy-installer 4.174.64.19-4 (using firmware-b43-lpphy-installer_4.174.64.19-4_all.deb) ...
Unpacking replacement firmware-b43-lpphy-installer ...
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ...
--2010-12-21 14:29:47--  [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing firmware-b43-lpphy-installer (--install):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 firmware-b43-lpphy-installer

---

### Post by amsterdamharu on 2010-12-21
aroonchand, you really should work on your reading skills. Here it is again ..

This link will work, download the file, copy to Ubuntu and [COLOR=Red]double click  on it to see if you get any errors[/COLOR] ([SIZE=2][COLOR=Red]**don't install**[/COLOR][/SIZE] the installer tries to  download something from the internet)

The link will open a mirror list, any link on that page should give you the same file.

[http://packages.ubuntu.com/maverick/...aller/download]("http://packages.ubuntu.com/maverick/all/firmware-b43-lpphy-installer/download")


[COLOR=Red]If it doesn't give any errors [/COLOR]

....


So does double clicking on the .deb file give you any errors or not?

---

### Post by amsterdamharu on 2010-12-21
@[migs73]("http://ubuntuforums.org/member.php?u=749318")

If you download the deb file and open it in gdebi package installer you will see in the tab "included files" under postinst a script getting a gz file, extracting it and executing b43-fwcutter, no make there. Looks like all the other files included in the deb are not crucial to the driver install but that package assumes working internet when it's installed.

I need the OP to open it so when there is [COLOR=Red]red text[/COLOR] next to Status we know some dependencies have not been satisfied and we need to download more debs, once down that street we can have a long thread waiting for us here.

If there is no [COLOR=Red]red text[/COLOR] next to status we can proceed downloading the gz file on a computer with internet and run the script as the deb package would have run it.

---

### Post by migs73 on 2010-12-21
> **amsterdamharu said:**
> @[migs73]("http://ubuntuforums.org/member.php?u=749318")

If you download the deb file and open it in gdebi package installer you will see in the tab "included files" under postinst a script getting a gz file, extracting it and executing b43-fwcutter, no make there. Looks like all the other files included in the deb are not crucial to the driver install but that package assumes working internet when it's installed.

I need the OP to open it so when there is [COLOR=Red]red text[/COLOR] next to Status we know some dependencies have not been satisfied and we need to download more debs, once down that street we can have a long thread waiting for us here.

If there is no [COLOR=Red]red text[/COLOR] next to status we can proceed downloading the gz file on a computer with internet and run the script as the deb package would have run it.

Just checking as I think the last time I did this (a while ago!!) I had to use 'make'. Wasn't entirely sure, hence all the 'do not do this' stuff!!
Oh, to have the OP be able to get a wired connection!!

---

### Post by aroonchand on 2010-12-21
> **amsterdamharu said:**
> aroonchand, you really should work on your reading skills. Here it is again ..

This link will work, download the file, copy to Ubuntu and [COLOR=Red]double click  on it to see if you get any errors[/COLOR] ([SIZE=2][COLOR=Red]**don't install**[/COLOR][/SIZE] the installer tries to  download something from the internet)

The link will open a mirror list, any link on that page should give you the same file.

[http://packages.ubuntu.com/maverick/...aller/download]("http://packages.ubuntu.com/maverick/all/firmware-b43-lpphy-installer/download")


[COLOR=Red]If it doesn't give any errors [/COLOR]

....


So does double clicking on the .deb file give you any errors or not?
ok... now sorry for installing it.
double clicking didnot give any errors...
what should i do next?

---

### Post by amsterdamharu on 2010-12-21
@aroonchand

No problem, I think you got overexcited and pressed the install button as would I probably have done. It doesn't do anything so no harm done.

The "Install package" button would have been disabled and also and you would not be able to try and install it if there were any unsatisfied dependencies (meaning the deb will check if there is any software missing that this software depends on).

Before installing the driver we should make sure that you have your wireless enabled. Are there any key combinations to switch your wireless on or off? If so make sure it's turned on.
I once went back with my laptop because I could not find any available network, even in a place with wireless service. Turns out I have to press some key combination to turn it on.

Assuming it's turned on we can proceed to download and install the driver.
Go to your mac and download the following file:
[http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
Copy that file to your Ubuntu desktop and open a terminal (press alt + F2 and type gnome-terminal).
Copy and paste the following commands in the terminal (all the lines at once and use the mouse to paste because control + v doesn't work in terminal but right click gives you paste option).
```
cd ~/Desktop
tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```

When that is done and you have any errors could you please copy and paste that from the terminal to this forum so we can see what's going on?

I assume there is no error so maybe you can reboot to see any changes.

---

### Post by aroonchand on 2010-12-21
> **amsterdamharu said:**
> @aroonchand

No problem, I think you got overexcited and pressed the install button as would I probably have done. It doesn't do anything so no harm done.

The "Install package" button would have been disabled and also and you would not be able to try and install it if there were any unsatisfied dependencies (meaning the deb will check if there is any software missing that this software depends on).

Before installing the driver we should make sure that you have your wireless enabled. Are there any key combinations to switch your wireless on or off? If so make sure it's turned on.
I once went back with my laptop because I could not find any available network, even in a place with wireless service. Turns out I have to press some key combination to turn it on.

Assuming it's turned on we can proceed to download and install the driver.
Go to your mac and download the following file:
[http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
Copy that file to your Ubuntu desktop and open a terminal (press alt + F2 and type gnome-terminal).
Copy and paste the following commands in the terminal (all the lines at once and use the mouse to paste because control + v doesn't work in terminal but right click gives you paste option).
```
cd ~/Desktop
tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```When that is done and you have any errors could you please copy and paste that from the terminal to this forum so we can see what's going on?

I assume there is no error so maybe you can reboot to see any changes.

thanks amsterdamharu ;)
here is the output:
fidu@fidu:~/Desktop$ tar xjf broadcom-wl-4.178.10.4.tar.bz2
fidu@fidu:~/Desktop$ cd broadcom-wl-4.178.10.4/linux
fidu@fidu:~/Desktop/broadcom-wl-4.178.10.4/linux$ sudo b43-fwcutter -w
"$FIRMWARE_INSTALL_DIR" wl_apsta.o
[sudo] password for fidu:
This file is recognised as:
ID : FW15
filename : wl_apsta.o
version : 478.104
MD5 : bb8537e3204a1ea5903fe3e66b5e2763
Extracting b43/ucode5.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/ucode9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/ucode13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/ucode14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/ucode16.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/n0initvals16.fw
Extracting b43/lp0initvals16.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/lp0bsinitvals16.fw
fidu@fidu:~/Desktop/broadcom-wl-4.178.10.4/linux$
-------
I restarted the system, but it is not connected to internet yet...
still "Firmware missing"

---

### Post by amsterdamharu on 2010-12-21
Could you show me where you get that error "Firmware missing"? (print screen or something)

Just guessing here but:
When you click on the network icon there is no wireless available?

Maybe you should check your bios for extra wireless settings.

Maybe you had some kernel parameters at boot that switches off hardware, could you post /boot/grub/grub.cfg?

Could you post the result of this command:
```
lsmod
```

I am off to bed so hope someone else has any ideas, you should have installed and are using the driver.

---

### Post by amsterdamharu on 2010-12-21
Oh sorry, its a bit late here. I see there are some extra lines in the setup code I missed.

Try to execute this code (assuming the extracted gz file is still on your desktop and you didn't delete it)
```
cd ~/Desktop/broadcom-wl-4.178.10.4/linux
sudo b43-fwcutter -w "/lib/firmware" wl_apsta.o
```

---

### Post by aroonchand on 2010-12-21
> **amsterdamharu said:**
> Could you show me where you get that error "Firmware missing"? (print screen or something)

Just guessing here but:
When you click on the network icon there is no wireless available?

Maybe you should check your bios for extra wireless settings.

Maybe you had some kernel parameters at boot that switches off hardware, could you post /boot/grub/grub.cfg?

Could you post the result of this command:
```
lsmod
```I am off to bed so hope someone else has any ideas, you should have installed and are using the driver.
Thank you...

The output:

                 fidu@fidu:~$ lsmod
  
  Module                  Size  Used by
  
  parport_pc             26058  0 
  
  ppdev                   5556  0 
  
  binfmt_misc             6599  1 
  
  snd_hda_codec_idt      54887  1 
  
  joydev                  8735  0 
  
  snd_hda_intel          22107  2 
  
  arc4                    1165  2 
  
  i915                  290938  3 
  
  snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
  
  snd_hwdep               5040  1 snd_hda_codec
  
  snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
  
  drm_kms_helper         30200  1 i915
  
  snd_seq_midi            4588  0 
  
  snd_rawmidi            17783  1 snd_seq_midi
  
  drm                   168054  4 i915,drm_kms_helper
  
  b43                   168681  0 
  
  snd_seq_midi_event      6047  1 snd_seq_midi
  
  snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
  
  mac80211              231541  1 b43
  
  snd_timer              19067  2 snd_pcm,snd_seq
  
  snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
  
  uvcvideo               55847  0 
  
  dell_laptop             5730  0 
  
  dell_wmi                2852  0 
  
  snd                    49006  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
  
  cfg80211              144470  2 b43,mac80211
  
  intel_agp              26360  2 i915
  
  dcdbas                  5402  1 dell_laptop
  
  videodev               43098  1 uvcvideo
  
  psmouse                59033  0 
  
  v4l1_compat            13359  2 uvcvideo,videodev
  
  soundcore                880  1 snd
  
  serio_raw               4022  0 
  
  led_class               2633  1 b43
  
  snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
  
  agpgart                32011  2 drm,intel_agp
  
  i2c_algo_bit            5168  1 i915
  
  video                  18712  1 i915
  
  output                  1883  1 video
  
  lp                      7342  0 
  
  parport                31492  3 parport_pc,ppdev,lp
  
  ahci                   19013  0 
  
  usb_storage            40172  0 
  
  ssb                    39288  1 b43
  
  libahci                21667  3 ahci
  
  sky2                   45127  0 
  
  [FONT=&quot]fidu@fidu:~$ [/FONT]   ------
Image is in attachment.

---

### Post by amsterdamharu on 2010-12-21
[http://ubuntuforums.org/showpost.php?p=10264421&postcount=23](http://ubuntuforums.org/showpost.php?p=10264421&postcount=23)

---

### Post by Atreideskid on 2011-02-09
> **amsterdamharu said:**
> Oh sorry, its a bit late here. I see there are some extra lines in the setup code I missed.

Try to execute this code (assuming the extracted gz file is still on your desktop and you didn't delete it)
```
cd ~/Desktop/broadcom-wl-4.178.10.4/linux
sudo b43-fwcutter -w "/lib/firmware" wl_apsta.o
```

I've been following this thread.  I have just put in the last missed lines, now what?  Is there more?

---

### Post by Atreideskid on 2011-02-09
> **amsterdamharu said:**
> Oh sorry, its a bit late here. I see there are some extra lines in the setup code I missed.

Try to execute this code (assuming the extracted gz file is still on your desktop and you didn't delete it)
```
cd ~/Desktop/broadcom-wl-4.178.10.4/linux
sudo b43-fwcutter -w "/lib/firmware" wl_apsta.o
```

I've been following thread.  What next?

---

### Post by amsterdamharu on 2011-02-09
What is the output of the following command?

```
lsmod
lspci -v
```

For the lspci especially the part where it shows your broadcom card.

To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by Atreideskid on 2011-02-10
> **amsterdamharu said:**
> What is the output of the following command?

```
lsmod
lspci -v
```For the lspci especially the part where it shows your broadcom card.

To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: ```
[COLOR=Red]Your pasted stuff[/COLOR]
```

Thank you, I figured it out.

---

