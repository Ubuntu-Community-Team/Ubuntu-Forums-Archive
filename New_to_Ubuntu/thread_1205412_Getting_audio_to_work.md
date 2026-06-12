---
title: "Getting audio to work"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by NaeturVindur on 2009-07-06
So I'm completely new (as you could have guesses), as in I installed Ubuntu six hours ago, and have never handled a linux OS before.  I'm using a new Asus N90Sv laptop.  I haven't changed any hardware, nor really done anything with the drivers besides originally setting them up.  I think the sound card would be Realtek HD (I'm not that tech savvy, and I tried to get that info out of Vista, so I'm not even certain that *is* a sound card).  I have seen a couple threads around here with the same problem, but what's said in those threads go completely over my head.  I have tried turing the volume all the way up while playing music.  Gone into the Sound prefrences and played around with all variety of combinations of settings (I don't really think the specific combination would do anyhing, but it was worth a try) and tested them all.  I've gone to the realtek site and downloaded the driver, and clicked the install file (it seemed to do something, but what, idk), restarted the computer after that. continued to play around with the sound settings.  Through it all, I haven't gotten anything out of my speakers.  When I go back to Vista (I'm doing a doul boot for compatibility's sake), the speakers still work.

As I mentioned before, I'm not that tech savvy, but I was raised by an Electrical engineer, and I do (mostly) know my way around a computer, so don't get a bad impression of me.  However, for this, it may be best if you treated my like someone who had just began to grasp the basic concept of keyboard, mouse, and a user interface.

---

### Post by NaeturVindur on 2009-07-06
Update: I just had someone mention lspci to me, and this is what it gave me:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: nVidia Corporation Device 0652 (rev a1)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```
I've never heard of SiS Azailia Audio Controller in my life.

---

### Post by prshah on 2009-07-06
> **NaeturVindur said:**
> I haven't gotten anything out of my speakers.  


As a first step, let's see if your sound card is recognized and loaded in Ubuntu. Open a terminal (Applications-Accessories-Terminal) and give the commands as below and post back the output.```
aplay -l
lsmod | grep snd
```

This will tell us what sound devices are available on your computer, as well as what modules (drivers, in windows-speak) are loaded for it.

---

### Post by esalnoj on 2009-07-06
Welcome to the community.

What file extension was the driver in?

Files ending in .tar.gz and .tar.bz2 are the most difficult to install.

.deb files should install easily with just double-clicking the file. You may have to download additional dependencies, but you will be notified of those when file is opened.

-Esalnoj

---

### Post by NaeturVindur on 2009-07-06
> **prshah said:**
> As a first step, let's see if your sound card is recognized and loaded in Ubuntu. Open a terminal (Applications-Accessories-Terminal) and give the commands as below and post back the output.```
aplay -l
lsmod | grep snd
```This will tell us what sound devices are available on your computer, as well as what modules (drivers, in windows-speak) are loaded for it.
```
ben@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SIS966 [HDA SIS966], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SIS966 [HDA SIS966], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ben@ubuntu:~$ lsmod | grep snd
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

```

> **esalnoj said:**
> Welcome to the community.

What file extension was the driver in?

Files ending in .tar.gz and .tar.bz2 are the most difficult to install.

.deb files should install easily with just double-clicking the file. You may have to download additional dependencies, but you will be notified of those when file is opened.

-Esalnoj
it was .tar.bz2 (so no wonder, right?)

---

### Post by prshah on 2009-07-06
> **NaeturVindur said:**
> 
card 0: SIS966 [HDA SIS966], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


OK your sound card is detected and correctly setup, and the relevant modules are loaded.

Then it may be a problem with the speaker configuration. Right click your volume icon, and choose "Open Volume Control". Choose "Preferences" and check everything shown.

Max out all volumes, and unmute everything.

Open the "Switches" tab, and, if you have a setting "External Amplifier", please check it.

Now check the sound.

If it works, try muting the various audio sliders one by one to find out which one is being used. For example, you may find that to get speaker output, you may have to use the "Headphone" volume slider. This happens because of a mis-compiled installation (only possible in the case of .tar / .bz2 installation) 

Post back with your results for further recommendations. If it doesn't work, a couple of screenshots of your Volume Control app showing all the sliders may be helpful.

---

### Post by NaeturVindur on 2009-07-06
ok, I did that, and the test sound works (in system>sound), but I try to play any sort of music, all I get are faint hisses and cracks.  Plus, it only works with headphones, it still wont use the on board speakers.  The screen shots are attached.  I tried muting what I found to be the extraneous stuff (most of the mics), but it didn't help the sound quality.

---

### Post by NaeturVindur on 2009-07-06
GAH! Too many bugs for me to deal with.  The internet is shacky (it seems to have trouble connecting and staying on the wireless network), it keeps crashing (seems to be connected with the internet thing) and the sound still doesn't work.  I have decided to uninstall Jaunty and install Intrepid.  If I still have he same problems, I'll post all the new stuff from Terminal here.

---

