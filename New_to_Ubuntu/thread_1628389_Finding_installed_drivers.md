---
title: "Finding installed drivers"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by grey1beard on 2010-11-22
I'm currently trying to get my G4010 scanner to run in Meerkat.

The current problem is do I have a "usb host controller driver installed ?"
I have two usb controllers listed if I use lspci - 

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
and I'm guessing that one controls the two ports on the front of the pc, and one for the four on the back.

I know what a driver is, but don't know what tool to use to find any specific driver.
I've tried Sysinfo, Synaptic Package Manager, and looked in Additional Drivers, all without success.

Grateful for a pointer on this general problem of finding what's where, before I get on to the next puzzle.

John

---

### Post by TeoBigusGeekus on 2010-11-22
Not too promising, but give [it]("http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-and-hp-scanjet-g4010-840103/") a shot.

---

### Post by fatharraxman on 2010-11-22
hello 
could you find the scanner packages in synaptic if you typed 
> sudo apt-get install libsane-extras ?
you can also try
[https://help.ubuntu.com/8.04/printing/C/scanning.html]("https://help.ubuntu.com/8.04/printing/C/scanning.html")

---

### Post by VraiChevalier on 2010-11-22
I thought something like <modprobe> or <lsmod> from the terminal would list the currently loaded drivers.

---

### Post by grey1beard on 2010-11-22
Hi TeoBigusGeekus.
I have come across that page before, so I was cautiously optomistic that I might follow the same route ;)
However, being well situated in the "Absolute Beginner" category, most of it went in one eye and out the other.

I've downloaded the backend from the Sane site, and have installed it via a terminal window, but don't know how to check that it was ok.
As I still can't get Simply Scan or Xsane to recognise it, I've started working backwards. 
Hence this thread.
John

---

### Post by TeoBigusGeekus on 2010-11-22
From my quick googling, it seems that your scanner is probably unsupported...

---

### Post by grey1beard on 2010-11-22
> **TeoBigusGeekus said:**
> From my quick googling, it seems that your scanner is probably unsupported...

No, it does have basic support.
Not good, but better than nothing.
John

---

### Post by TeoBigusGeekus on 2010-11-22
Well then, try to do what the page mentioned before advises:
go to the sane website, download the latest version of sane and build from source.

---

### Post by grey1beard on 2010-11-22
Hi fatharraxman.
I already have the latest version installed of libsane-extras.

VraiChevalier, the result of lsmod is 

Module                  Size  Used by
binfmt_misc             7984  1 
snd_intel8x0           31307  2 
snd_ac97_codec        125227  1 snd_intel8x0
ac97_bus                1474  1 snd_ac97_codec
snd_pcm                89104  2 snd_intel8x0,snd_ac97_codec
radeon                906714  3 
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
ttm                    68212  1 radeon
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         32836  1 radeon
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6804  0 
snd                    64117  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   206161  5 radeon,ttm,drm_kms_helper
psmouse                62080  0 
parport_pc             30086  1 
edac_core              46822  0 
soundcore               1240  1 snd
k8temp                  4064  0 
i2c_algo_bit            6208  1 radeon
serio_raw               4910  0 
edac_mce_amd            9387  0 
snd_page_alloc          8588  2 snd_intel8x0,snd_pcm
i2c_nforce2             6155  0 
lp                     10201  0 
parport                37032  3 ppdev,parport_pc,lp
usb_storage            50372  0 
floppy                 65299  0 
firewire_ohci          24679  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
forcedeth              55649  0 
sata_nv                23770  2 
pata_amd               12050  0 

But I don't know how to identify if any of the entries is what I'm looking for !!!

John

---

### Post by grey1beard on 2010-11-22
> **TeoBigusGeekus said:**
> Well then, try to do what the page mentioned before advises:
go to the sane website, download the latest version of sane and build from source.

I think that's what I'm trying to do. I've been to the Sane site, and to genesys to read as much as I can, and try to understand the process.
However the learning curve is strewn with rocks, and stumbling from one to the next is somewhat painful
Regards
John

---

### Post by TeoBigusGeekus on 2010-11-22
Download [this]("https://alioth.debian.org/frs/download.php/3258/sane-backends-1.0.21.tar.gz") file and extract it somewhere, let's say your desktop.
Navigate in the extracted folder
```
cd ~/Desktop/nameofthefolder
```
and give:
```
./configure
```
this will check if everything is ok with the source package and whether it satisfies dependencies.
Then give
```
make
```
to compile the package and finally
```
sudo make install
```
to install the package.
I hope you'll be lucky.

---

### Post by VraiChevalier on 2010-11-22
> **grey1beard said:**
> 
I have two usb controllers listed if I use lspci - 

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
and I'm guessing that one controls the two ports on the front of the pc, and one for the four on the back.


I may have misunderstood your original post. If <lspci> is showing the above, wouldn't that indicate that the drivers are indeed installed?

---

### Post by grey1beard on 2010-11-22
TeoBigusGeekus 
That's the route I am already on. I have done all that, but at the end of that stage, the scanner is not yet recognised.
As I had run sudo sane-find-scanner, and it questioned if I had the usb host controller driver installed, my next problem was to find out.
Being a beginner, I had no idea how to do that, so I came here and asked the specific question.

VraiChevalier
There you have me. I have no idea if it does !!
Perhaps someone could enlighten us both ;)

John

---

