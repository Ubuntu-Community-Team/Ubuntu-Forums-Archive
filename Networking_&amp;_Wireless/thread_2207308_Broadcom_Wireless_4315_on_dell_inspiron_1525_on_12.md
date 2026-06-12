---
title: "Broadcom Wireless 4315 on dell inspiron 1525 on 12.04 LTS"
date: 2014-02-23
forum: Networking &amp; Wireless
---

### Post by vvn2 on 2014-02-23
Hello,

I know this question has been handled many times, but I am asking 
it again with sadness after having tried all the suggestions. :(

My broadcom wireless on dell inspiron 1525 is not working.
I have searched the forums, and tried installing b43cutter, 
linux-nonfree-firware, bcwml-kernel-source, broadcom-sta-common.......


I followed many suggestions one by one hoping atleast one would work.
First tried the "restricted drivers" in ubuntu, it did not work. 
I could see other wireless networks but not the one in my house. I manually 
tried to connect to it by filling out the details but it did not connect.

Then tried the b43cutter, and same thing happened.<br>
Then did remove/purge of previous ones, and tried bcwml....same story..
Then did remove/purge of previous ones and tried broadcom, same story..
and finally tried the linux-nonfree-firware.... and now my wireless is dead.
The wifi light does not come on now.

Please help me fix this problem. 


 1. Laptop model
    Dell inspiron 1525

 2. Ubuntu release
    12.04.4 LTS (had the same problem in 12.04.3 as well)

 3. Wireless hardware 
      vvn@archangel:~$ lspci -vvnn | grep 14e4
        0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

 4. Modules 

        vvn@archangel:~$ lsmod 
        Module                  Size  Used by
        snd_hda_codec_idt      45116  1 
        snd_hda_codec_hdmi     40852  1 
        joydev                 17329  0 
        uvcvideo               72275  0 
        snd_hda_intel          43326  3 
        snd_hda_codec         169534  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
        i915                  615640  3 
        snd_hwdep              13276  1 snd_hda_codec
        videobuf2_core         39385  1 uvcvideo
        snd_pcm                94597  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
        videodev              107944  2 uvcvideo,videobuf2_core
        snd_seq_midi           13132  0 
        snd_rawmidi            25157  1 snd_seq_midi
        videobuf2_vmalloc      13048  1 uvcvideo
        snd_seq_midi_event     14475  1 snd_seq_midi
        drm_kms_helper         47306  1 i915
        r852                   17873  0 
        videobuf2_memops       13170  1 videobuf2_vmalloc
        sm_common              16772  1 r852
        nand                   59169  2 r852,sm_common
        mtd                    52875  2 sm_common,nand
        nand_ids                8547  1 nand
        snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
        nand_bch               13067  1 nand
        drm                   247722  4 i915,drm_kms_helper
        snd_timer              28930  2 snd_pcm,snd_seq
        snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
        rfcomm                 59026  0 
        bnep                   19210  2 
        gpio_ich               13278  0 
        r592                   17812  0 
        snd                    61270  17       snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
        bch                    21767  1 nand_bch
        dell_wmi               12665  0 
        sparse_keymap          13658  1 dell_wmi
        dell_laptop            17209  0 
        nand_ecc               13136  1 nand
        memstick               16051  1 r592
        psmouse                92648  0 
        dcdbas                 14456  1 dell_laptop
        lpc_ich                16987  0 
        i2c_algo_bit           13316  1 i915
        serio_raw              13189  0 
        soundcore              12600  1 snd
        snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
        mac_hid                13077  0 
        wmi                    18744  1 dell_wmi
        video                  19046  1 i915
        bluetooth             341971  10 rfcomm,bnep
        parport_pc             32114  0 
        ppdev                  17423  0 
        lp                     13359  0 
        parport                40930  3 parport_pc,ppdev,lp
        firewire_ohci          36064  0 
        firewire_core          62303  1 firewire_ohci
        sdhci_pci              18588  0 
        ahci                   25703  2 
        sdhci                  37958  1 sdhci_pci
        crc_itu_t              12627  1 firewire_core
        libahci                30834  1 ahci
        sky2                   53656  0 

 5. Kernel architecture
      vvn@archangel:~$ uname -mr
      3.11.0-15-generic i686


Please help me fix this problem.

---

### Post by praseodym on 2014-02-23
You need the firmware for the low-power chipset:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe -rfv b43
sudo modprobe -v b43
```

---

