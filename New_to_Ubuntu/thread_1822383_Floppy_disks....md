---
title: "Floppy disks..."
date: 2011-08-10
forum: New to Ubuntu
---

### Post by MG&amp;TL on 2011-08-10
Could somebody give me a step-by-step handholding approach to using floppy disks please?

Not something I usually ask for, but floppy disk aren't my era ( I wasn't born ) and I've tried everything on the web and I fear I am missing something. Terminal commands are fine. Thanks!

---

### Post by ron999 on 2011-08-10
> **MG&TL said:**
> Could somebody give me a step-by-step handholding approach to using floppy disks please?
... Terminal commands are fine. Thanks!

Hi
This is how I go about it.

Put the disk in the drive then use command:-
```
udisks --mount /dev/fd0
```

To read from the disk use nautilus file manager (or similar) to browse in folder /media/floppy0.
Then you can open files or 'copy' to home folder.

To write to a disk needs to be root, so use [FONT="Courier New"]**[SIZE="4"]gksudo nautilus[/SIZE]**[/FONT] command and 'paste' files to the floppy.

When you've finished use command:-
```
udisks --unmount /dev/fd0
```

Then remove the disk.
(During unmount it should 'save' any files that you've written to floppy).

---

### Post by MG&amp;TL on 2011-08-10
```
Mount failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: mount point /mnt/floppy does not exist

```Any ideas? The 'read-only' switch is OFF.

Thanks for help BTW :D

Didn't think anyone still used floppy disks. My computer doesn't support USB and cds are getting expensive.

---

### Post by ron999 on 2011-08-10
> **MG&TL said:**
> ```
Mount failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: mount point /mnt/floppy does not exist

```Any ideas? 

Yes, look in the [SIZE="4"]**media**[/SIZE] directory.
Mine has an empty folder in there named **floppy0**.
You may need to create one yourself.

---

### Post by MG&amp;TL on 2011-08-10
The error message is from the terminal.

gksu nautilus > media > floppy 0 >paste

Problem with both pasting and mounting the floppy, apparently nothings there. It was previously ued on windows XP, but do I need to reformat?

---

### Post by MG&amp;TL on 2011-08-10
/mnt does not have anything in it. Does that help?

---

### Post by plucky on 2011-08-11
Is this an external or internal floppy?

Open a terminal and post output of ```
cat /etc/fstab
ls /media
lsmod
```

Use [noparse]```

```[/noparse] brackets to show the information from those commands.

---

### Post by MG&amp;TL on 2011-08-11
IDK, it's a 3.5 inch type, I pop it in a slot in the front of my machine, and it makes a clunk noise and I press a long thin button to get it out. :confused:

Cat /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c57821ba-b771-4698-8f60-0045d95a4bd4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5f949dad-bdcd-4355-aae4-a0831d1f2dc2 none            swap    sw              0       0
/dev/fd0 /mnt/floppy auto defaults,user,noauto 0 0

```

ls /media:

```
floppy  floppy0

```'floppy' is a shortcut to something.

lsmod:

```
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
snd_intel8x0           33213  3 
snd_ac97_codec        105614  1 snd_intel8x0
arc4                   12473  2 
ac97_bus               12642  1 snd_ac97_codec
nvidia               7098106  34 
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
rt73usb                26854  0 
crc_itu_t              12627  1 rt73usb
snd_seq_midi           13132  0 
rt2500usb              22621  0 
rt2x00usb              19693  2 rt73usb,rt2500usb
rt2x00lib              39075  3 rt73usb,rt2500usb,rt2x00usb
mac80211              257001  2 rt2x00usb,rt2x00lib
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
i915                  450934  1 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  2 rt2x00lib,mac80211
drm_kms_helper         40745  1 i915
snd                    55295  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                  12849  0 
psmouse                73312  0 
drm                   180037  2 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
serio_raw              12990  0 
shpchp                 32345  0 
parport_pc             32111  1 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
dcdbas                 14054  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
b44                    35301  0 
ssb                    45942  1 b44
floppy                 60032  0 

```Thanks for help so far. :)

---

### Post by plucky on 2011-08-11
> /dev/fd0 /mnt/floppy auto defaults,user,noauto 0 0

Did you add that line to fstab?

I think the line should be ```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Then reboot

You should now be able to use the command ```
udisks --mount /dev/fd0
``` to mount your floppy.

Good Luck

---

### Post by MG&amp;TL on 2011-08-11
Thank you-err...no, I didn't, but multiple people use it and they have they all have sudo password, so it gets a bit hectic. I'm thinking about pulling some of them down in rank, as I'm the only who actually 'administrates' the others just 'use'

Thread will be marked solved if I mount the floppy. cheers!

---

### Post by MG&amp;TL on 2011-08-11
Thank you very much! Even retrieved a few old files off one-fascinating stuff-word 2003 documents :D

Google was not working, so UF stepped into the breach. Thank you, you two! :D

---

### Post by MG&amp;TL on 2011-08-11
Thank you, major. :) That's helpful too. Made a file recovery floppy using tombstrt-great program.

[http://www.toms.net/rb/]("http://www.toms.net/rb/")

---

