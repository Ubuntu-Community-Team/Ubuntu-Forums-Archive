---
title: "Gstreamer issue in xubuntu"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by aditya.us on 2009-12-23
I just installed xubuntu on my desktop, but the the audio doesn't seem to work. Whenever I click on the speaker icon in the top-right corner, i get the following error: 

"GStreamer was unable to detect any sound devices. Some sound system specific GStreamer packages may be missing. It may also be a permissions problem."

What can I do to fix this?

---

### Post by Geoff918 on 2009-12-23
With a fresh install it should not be a user permission error.

What you may want to do is Alt-F2 (check run in terminal box)

sudo aptitude install xubuntu-restricted-extras

That would get a full compliment of gstreamer plugins that are not installed as a result of legal issues. If this doesn't work, we'll try something else.

---

### Post by aditya.us on 2009-12-23
I did that: here is what is says in the terminal box:

[sudo] password for aditya: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  xubuntu-restricted-extras 
The following packages will be REMOVED:
  libavdevice52{u} libavfilter0{u} linux-headers-2.6.31-14{u} 
  linux-headers-2.6.31-14-generic{u} 
0 packages upgraded, 1 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B/5,486B of archives. After unpacking 82.4MB will be freed.
Do you want to continue? [Y/n/?] 

should i press Y or N?

---

### Post by aditya.us on 2009-12-23
I took a chance and pressed Y, the restricted extras have been installed but i still get the error when i click the speaker icon....should i restart the computer?

---

### Post by bodhi.zazen on 2009-12-23
See this thread for advice on how to solve that problem :


[[ubuntu] No sound after upgrade to Karmic Koala 9.10 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1308550")

After trying one of the fixes on that thread you almost certainly will need to reboot.

this post [http://ubuntuforums.org/showpost.php?p=8435374&postcount=41](http://ubuntuforums.org/showpost.php?p=8435374&postcount=41)

has been most useful, although IMO it can be shortened to simply :

```
sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio
sudo reboot
```

---

### Post by aditya.us on 2009-12-23
I have no clue on what to type into terminal....that thread is very confusing....can you guys help me out....and that thread is for ubuntu, not xubuntu, will it still work?

---

### Post by aditya.us on 2009-12-23
i typed the code into terminal and rebooted, now when i click the speaker icon, a mixer comes up but if i try to play a youtube video or something the audio does not work.

---

### Post by bodhi.zazen on 2009-12-23
What code did you type ?

In terms of helping, the thread I gave you has tons of relevant advice.

At this point we need to know your hardware (what sound card) and what you have done to try to fix your problem. Without more detailed information we can not give you more specific answers.

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by aditya.us on 2009-12-23
i typed: sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio

 
and then after that i typed: sudo reboot
 
ill check those wikis out

---

### Post by aditya.us on 2009-12-27
> **bodhi.zazen said:**
> What code did you type ?

In terms of helping, the thread I gave you has tons of relevant advice.

At this point we need to know your hardware (what sound card) and what you have done to try to fix your problem. Without more detailed information we can not give you more specific answers.

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)


that thread just doesn't make sense to me
How do i figure out what soundcard i have?
so far all i have done to solve this problem is install xubuntu-restricted-extras and typed sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio into terminal

i'm gona look at the thread and wiki again...any other suggestions for me?

thanks

---

### Post by aditya.us on 2009-12-27
Here is some information, i typed some commands i saw in the other thread into terminal

```
aditya@aditya-desktop:~$  sudo aplay -l
aplay: device_list:223: no soundcards found...
``````
aditya@aditya-desktop:~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic
2.6.31-16-generic
``````
aditya@aditya-desktop:~$ cat /proc/asound/cards
--- no soundcards ---
``````
aditya@aditya-desktop:~$ lspci | grep -i audio
00:0b.0 Multimedia [COLOR=Red]audio[/COLOR] controller: Rockwell International Device 4310
``````
aditya@aditya-desktop:~$ lsmod | grep snd
snd_riptide            22216  0 
snd_ac97_codec        101216  1 snd_riptide
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_riptide,snd_ac97_codec,snd_pcm_oss
snd_opl3_lib           10396  1 snd_riptide
snd_hwdep               7200  1 snd_opl3_lib
snd_page_alloc          9156  2 snd_riptide,snd_pcm
gameport               11368  2 snd_riptide
snd_mpu401_uart         6940  1 snd_riptide
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          6920  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  13 snd_riptide,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
```--The word snd was written in the color red.

```
aditya@aditya-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 42)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 12)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 08)
00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 20)
00:09.0 Multimedia controller: Agere Systems Device 0464 (rev 01)
00:0a.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
00:0b.0 Multimedia audio controller: Rockwell International Device 4310
00:0b.1 Communication controller: Rockwell International Riptide HSF 56k PCI Modem
00:0b.2 Input device controller: Rockwell International Device 4312
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB12LV23 IEEE-1394 Controller
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)

```

---

### Post by bodhi.zazen on 2009-12-27
I am not sure there are any Linux drivers for your sound card :

[http://ubuntuforums.org/showthread.php?t=185642](http://ubuntuforums.org/showthread.php?t=185642)

---

### Post by aditya.us on 2009-12-28
so i guess i'm out of luck...but aren't there any drivers for this, like generic ones....drivers that work for all types of cards?

---

### Post by aditya.us on 2009-12-28
does this website help?
 
[http://www.linuxant.com/drivers/riptide/index.php](http://www.linuxant.com/drivers/riptide/index.php)

---

### Post by aditya.us on 2009-12-28
that website is saying something about open source driver or whatever...is that what we need?

---

### Post by BudBear on 2009-12-28
> **aditya.us said:**
> I just installed xubuntu on my desktop, but the the audio doesn't seem to work. Whenever I click on the speaker icon in the top-right corner, i get the following error: 

"GStreamer was unable to detect any sound devices. Some sound system specific GStreamer packages may be missing. It may also be a permissions problem."

What can I do to fix this?

i am getting the same error. i had the sound working flawlessly for a whole 2 days in mythbuntu after finally getting it to recognize all my hardware.  now no sound and it doesn't recognize any sound card, it also fails to automatically log in and i have to boot in recovery mode to get to the point where i can acutlaly log in.  then it seems like certain permissions are inaccessible, such as not being"authorized" to make user or group changes. i  also noticed an error in update manager stating the following:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

im not sure but i think this is bad.

any ideas how to fix this, besides a complete reinstall.
fyi  im runing Muythbuntu 9.10 64bit amd on an asus M3A78-EM
but it seems like this is a Xubuntu related issue.

---

### Post by aditya.us on 2010-01-13
oh well....since i guess the audio on xubuntu won't work...i just switched to puppy linux....way faster then xubuntu and the sound also works!

---

