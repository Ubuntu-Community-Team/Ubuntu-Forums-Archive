---
title: "ubuntu 14.04 - wireless only works once ... needs reboot to re-enable it"
date: 2014-10-01
forum: Networking &amp; Wireless
---

### Post by nicolasdiogo on 2014-10-01
hello


it is really unusual to have aproblem like this with Linux.

my wireless on a ThinkPad X1 Carbon Ultrabook works fine at first
as soon as the system is suspended - it will not work again

i have used the system for months without this problem
i can only wonder that it was introduced following a system update

could i please ask for advice on how to troubleshoot this problem?

below is the description of the hardware
> 

# lspci 
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 7 Series/C210 Series Chipset Family KT Controller (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QS77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 System peripheral: Ricoh Co Ltd MMC/SD Host Controller (rev 07)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 96)




loaded modules:

> 

# lsmod 
Module                  Size  Used by
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
pci_stub               12622  1 
btusb                  32412  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
cdc_mbim               13176  0 
cdc_ncm                24511  1 cdc_mbim
usbnet                 43913  2 cdc_mbim,cdc_ncm
videobuf2_memops       13362  1 videobuf2_vmalloc
mii                    13934  1 usbnet
videobuf2_core         40664  1 uvcvideo
cdc_wdm                19053  2 cdc_mbim
cdc_acm                28803  0 
videodev              134688  2 uvcvideo,videobuf2_core
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391136  11 bnep,btusb,rfcomm
snd_hda_codec_hdmi     46368  1 
thinkpad_acpi          81013  1 
nvram                  14411  1 thinkpad_acpi
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12608  2 
snd_hda_codec_realtek    65580  1 
snd_rawmidi            30144  1 snd_seq_midi
iwldvm                232285  0 
mac80211              630653  1 iwldvm
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
snd_hda_intel          56451  3 
coretemp               13435  0 
kvm_intel             143109  0 
kvm                   451511  1 kvm_intel
binfmt_misc            17468  1 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mei_me                 18627  0 
snd_timer              29482  2 snd_pcm,snd_seq
mei                    82276  1 mei_me
snd                    69322  18 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
parport_pc             32701  0 
ppdev                  17671  0 
mac_hid                13205  0 
intel_smartconnect     12619  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
dm_crypt               23177  1 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  2879 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
i915                  783805  4 
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  1442 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse               106678  0 
i2c_algo_bit           13413  1 i915
ahci                   25819  2 
drm_kms_helper         53081  1 i915
sdhci_pci              23172  0 
libahci                32716  1 ahci
drm                   303102  5 i915,drm_kms_helper
sdhci                  43015  1 sdhci_pci
video                  19476  1 i915
wmi                    19177  0



please let me know if i should provide more info.
i have tried to use the script mentioned for the wireless questions - but it is no longer available from dropbox.

thanks,

---

### Post by varunendra on 2014-10-01
Please check this post out : [http://ubuntuforums.org/showthread.php?t=2234178&p=13085936#post13085936](http://ubuntuforums.org/showthread.php?t=2234178&p=13085936#post13085936)

Let us know if it works for you. If not, please post a wireless_script report as mentioned in this post : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

**PS:**
You should use 'Code' tags to post the outputs. You are currently using 'Quote' tags instead, it can't preserve the formatting as code tags can. Please follow the link in my signature if need to see an example.

---

### Post by nicolasdiogo on 2014-10-04
Thanks Varunendra


i had tried to remove and load the driver for the wireless card - as it used to work in that way many years ago

your suggested script did the trick - reloading the whole of network-manager

I am adding this to my list of necessary hacks (!) to make linux work.


I have rebooted, suspended, and wireless works as expected.


regards,

---

### Post by varunendra on 2014-10-04
Awesome! Thanks for the confirmation. :)

---

### Post by nicolasdiogo on 2014-10-21
well ..

in the end i had to add commands to remove and reload the module


thanks,

---

