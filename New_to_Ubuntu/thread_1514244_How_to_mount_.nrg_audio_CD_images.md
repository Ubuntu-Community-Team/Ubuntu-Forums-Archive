---
title: "How to mount .nrg audio CD images"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by damnated on 2010-06-20
I have a bunch of Nero audio CD images on my hard drive, and I can't mount them. I've tried nrg2iso, but the created ISO is corrupted, I can't mount it. The exact error is ```
 $ sudo mount CD1.iso /media/isoimage/ -t iso9660 -o loop
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
I don't have a general issue with mounting ISOs, just in these particular cases. I've found this is a common error in the case of audio CDs, but the help threads always died out before a solution emerged. Is this because there is none? Please advise!

---

### Post by qyot27 on 2010-06-20
A) The ISO image format doesn't support the data modes to properly store Audio CDs, as far as I know/have ever tested.  You have to use BIN/CUE or WAV/CUE - I wish I knew of an open format that could store audio data and CD Text/multisession data in a single file like NRG can, but I've not found one yet.  Likewise, I'm not aware of what programs I'd need to use on Linux to create BIN/CUE files...on Windows I use ImgBurn to do that (but ImgBurn does not seem to want to get along with Wine).

A secondary idea would be to rip to WAV/CUE and then mux into Matroska with [MKVToolNix](http://www.bunkus.org/videotools/mkvtoolnix/index.html), as IIRC it supports reading CUE files for chapter info and can definitely store the PCM audio data for you (or for kicks, you could compress the WAV into FLAC or TTA or some other lossless audio format first to save a good portion of space).  I haven't vetted this option too much, however.

B) To properly mount NRG Audio CD images, you can use CDemu (which I actually was testing for the very purpose of mounting audio NRGs last night).  The PPA for it is here:
[https://launchpad.net/~cdemu/+archive/ppa](https://launchpad.net/~cdemu/+archive/ppa)

sudo add-apt-repository ppa:cdemu/ppa
sudo apt-get update
sudo apt-get install gcdemu
gnome-session-properties

Log out and then log back in.

Add the GCDemu applet to the panel.  Left-clicking on it will give you the option to mount image files to the virtual drives it handles.

---

### Post by damnated on 2010-06-20
What exactly should I add to the start-up app list? GCDemu? I added it like that, but there's no option to mount when I right click a file. I've logged off. 

But your talking about left clicking, so maybe I'm missing something. On what should I left click after I logged in again? Sorry for being slow.

EDIT: right, I left click on the file twice and it mounts. The mounted drive is empty, though :( do I need to add something extra?

---

### Post by qyot27 on 2010-06-20
After running those commands I listed earlier and logging out/back in...

Right click on the Gnome Panel, and choose the 'Add to Panel' option.  Select 'gCDemu Applet' from the list so that the icon for it appears on the Panel.  Then, left click that icon - the menu that appears should say:
```
Device 00: Empty
Device 01: Empty
```

Click on 'Device 00: Empty' and you'll get a file selection dialog, which you can use to load an NRG file.

---

### Post by damnated on 2010-06-20
Works like a charm. Thank you!

---

### Post by qyot27 on 2010-06-21
Following up, I *did* actually discover how to make ImgBurn work.  I used it to convert the mounted NRG to BIN/CUE and to WAV/CUE.  On the I/O tab in the Settings dialog, you have to change the Interface to 'ASPI - WNASPI32.DLL' and possibly also check the 'Show All Devices' option.  As long as it recognizes the device, use Read mode to do the disc copying.

---

### Post by damnated on 2010-06-21
I'm ripping all these NRGs to FLAC myself. I have no idea why I ripped to NRGs in the first place :(.

---

### Post by VeterinaryPathologist on 2011-01-01
Nero audio .NRG files can not be converted to ISO, nor can they be mounted with a regular ISO mounter like AcetoneISO, but they can be mounted easily with [CDemu]("http://cdemu.sourceforge.net/project.php#binary"). 

The easy way to install CDemu is to update your system with unsupported packages from this untrusted PPA by adding ppa:cdemu/ppa to your system's Software Sources. Then use Synaptic package manager to add "gcdemu, cdemu-daemon & cdemu-client". After reboot, you can mount any audio image .NRG by right-clicking (in Nautilus file navigator) and choosing "open with CDEmu client".

I have many Nero .NRG images from my previous Windows days. The data .NRG images can be converted to standard ISO files with nrg2iso but the audio .NRG files can be mounted with CDemu and the mounted image can then be used for ripping.

---

### Post by ganesh.swarup on 2011-01-05
hi..i'm new to LINUX world... i'm trying to convert my windows7.nrg to iso
swarup@swarup-desktop:~$ nrg2iso "/home/swarup/Desktop/windows7/Windows7UltimateEdition.nrg" windows7ultimate.iso
this is wat i did and the output was 

"It seems that /home/swarup/Desktop/windows7/Windows7UltimateEdition.nrg is already an ISO 9660 image 
[Aborting conversion]"

Pls help me asap in converting..!!

---

### Post by bulletxt on 2011-01-12
> **ganesh.swarup said:**
> hi..i'm new to LINUX world... i'm trying to convert my windows7.nrg to iso
swarup@swarup-desktop:~$ nrg2iso "/home/swarup/Desktop/windows7/Windows7UltimateEdition.nrg" windows7ultimate.iso
this is wat i did and the output was 

"It seems that /home/swarup/Desktop/windows7/Windows7UltimateEdition.nrg is already an ISO 9660 image 
[Aborting conversion]"

Pls help me asap in converting..!!

It means it's already an ISO-9660 image. Rename it to .iso and then mount it. You can use AcetoneISO or anything else.

---

