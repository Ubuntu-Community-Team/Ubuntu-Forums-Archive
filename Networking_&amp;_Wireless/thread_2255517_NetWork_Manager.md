---
title: "NetWork Manager"
date: 2014-12-05
forum: Networking &amp; Wireless
---

### Post by AUROBINDO MAJUMDAR on 2014-12-05
When I last upgraded to 12.04 LTS ,  net working was lost, and it could only be restored by going back to the previous versions of the 5 Network Management files (version 0.9.4.0-0ubuntu3). I have so far resisted updating these files.  For upgrading  to 14.04 LTS should I update the 5 Network Management files to version: 0.9.4.0-0ubuntu4.4.1 first?

---

### Post by Hadaka on 2014-12-05
Hi, unless you have some very unusal exotic network cards, they
should be able to upgrade with the os. Lets have a look at what they
are..please do and post...
```
uname -a
cat /etc/issue
lspci -nnk | grep -iA3 net
rfkill list all
lsmod
```
thanks.

---

### Post by AUROBINDO MAJUMDAR on 2014-12-06
Hi Hadaka. First of all thanks for responding.
Please have a look at the output :-
$ uname -a
Linux aurobindo-desktop 3.2.0-54-generic #82-Ubuntu SMP Tue Sep 10 20:09:12 UTC 2013 i686 i686 i386 GNU/Linux
$ cat /etc/issue
Ubuntu 12.04.5 LTS \n \l
$ lspci -nnk | grep -iA3 net
01:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167] (rev 10)
	Subsystem: Gigabyte Technology Co., Ltd GA-MA69G-S3H Motherboard [1458:e000]
	Kernel driver in use: r8169
	Kernel modules: r8169
$ rfkill list all
$ lsmod
Module                  Size  Used by
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158447  10 rfcomm,bnep
binfmt_misc            17292  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
dm_crypt               22528  0 
ppdev                  12849  0 
snd_hda_codec_realtek   174313  1 
parport_pc             32114  1 
psmouse                96744  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
serio_raw              13027  0 
snd_timer              28931  2 snd_pcm,snd_seq
mac_hid                13077  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
r8169                  56396  0 
i915                  428021  2 
drm_kms_helper         45466  1 i915
drm                   197641  3 i915,drm_kms_helper
floppy                 60184  0 
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
Please let me know,
Thanks again.

---

### Post by Hadaka on 2014-12-06
Hi, it looks like you have no wireless card. is this correct?
Im not sure what you mean about the 5 network files, it is
usually better to install the os new rather than update as well.
also, please learn to use code tags.
thanks.

---

### Post by chili555 on 2014-12-06
>  previous versions of the 5 Network Management filesWhat are the names of the files, exactly?>  For upgrading to 14.04 LTS should I update the 5 Network Management files to version: 0.9.4.0-0ubuntu4.4.1 first?I would just upgrade and I suspect all will go well. If not, post back and we'll help you.

---

