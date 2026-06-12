---
title: "No wired connection after suspend"
date: 2013-10-09
forum: Networking &amp; Wireless
---

### Post by Melhisedek on 2013-10-09
Well I have this problem where after suspend my wired connection won't work (have no wireless) and only a restart fixes it. I did some searches and found a thread where people instructed one should run following command

lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv'

and here is the output from that:

```
snd_usb_audio         119227  3 
snd_usbmidi_lib        24326  1 snd_usb_audio
snd_hwdep              13272  2 snd_usb_audio,snd_hda_codec
snd_pcm                89488  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_rawmidi            25094  2 snd_usbmidi_lib,snd_seq_midi
snd                    60790  29 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mac_hid                13037  0 
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87192  2 hid_generic,usbhid
ahci                   25579  2 
libahci                26554  1 ahci
```

I hope there is a solution for this :)
Thank you for your time!

---

### Post by Toz on 2013-10-09
Unfortunately, that command doesn't show your network card. What does the following command show:
```
lspci -k | grep -iA3 NETWORK
```

Once you determine the kernel module that is being used by your network card, you can create (with root privledges) the file **/etc/pm/config.d/modules** with the following content:
```
SUSPEND_MODULES="<the_kernel_module_for_your_network_card>"
```
...replace <the_kernel_module_for_your_network_card> with the actual kernel module being used by your network card.

This will unload the module during the suspend process and reload during resume.

---

### Post by Melhisedek on 2013-10-09
Just to make sure I'll create file "modules"

```
Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard
    Kernel driver in use: e1000e
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
```

and add 
> SUSPEND_MODULES="e1000e"


 
in it... correct? As that is only thing with kernel in it :)

---

### Post by Toz on 2013-10-09
Yes, thats correct. Create the file and try suspending again.

If it still doesn't work, post back /var/log/pm-suspend.log and the results of:
```
cat /var/log/syslog | grep PM:
```

---

### Post by Melhisedek on 2013-10-09
So far so good. I'll report back if anything changes.

---

### Post by Shoalster on 2013-10-19
I have the same problem since upgrade to saucy.  However , when I try the code 
lspci -k | grep -iA3 NETWORK  nothing comes up.   ?????

---

### Post by Toz on 2013-10-20
> **Shoalster said:**
> I have the same problem since upgrade to saucy.  However , when I try the code 
lspci -k | grep -iA3 NETWORK  nothing comes up.   ?????
Before or after suspend? Try the command both before and after suspend. Also, post back the results of just:
```
lspci
```
What is the make and model of your computer?

---

### Post by Shoalster on 2013-10-20
My PC is a HP Pavilion a1250n   I tried the command before suspend.  I have turned off suspend in settings.   Here are results of above command:

shoalster@shoalster-EG194AA-ABA-A1250N:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS480/RS482/RS485 Host Bridge (rev 10)
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx]
00:12.0 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 Serial ATA Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller (rev 11)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge
00:14.5 Multimedia audio controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS480 [Radeon Xpress 200 Series]
02:01.0 Communication controller: LSI Corporation Lucent V.92 Data/Fax Modem
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
shoalster@shoalster-EG194AA-ABA-A1250N:~$

---

### Post by Toz on 2013-10-20
Can you try instead:
```
lspci -k | grep -iA3 ethernet
```

---

### Post by Shoalster on 2013-10-20
Okay.  I think we're getting somewhere  :

shoalster@shoalster-EG194AA-ABA-A1250N:~$ lspci -k | grep -iA3 ethernet
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Hewlett-Packard Company Device 2a24
    Kernel driver in use: 8139too
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
shoalster@shoalster-EG194AA-ABA-A1250N:~$


But no results after entering :  shoalster@shoalster-EG194AA-ABA-A1250N:~$ SUSPEND_MODULES=8139too
shoalster@shoalster-EG194AA-ABA-A1250N:~$


UPDATE:   After reboot, Network Card woke from suspend.  Appears issue is solved.

        THANKS MUCH TOZ

---

### Post by Toz on 2013-10-20
Okay, try:
```
SUSPEND_MODULES="8139too"
```

If it doesn't work, post back:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated...

and

the results of:
```
cat /var/log/syslog | grep PM:
```

---

### Post by Shoalster on 2013-10-21
shoalster@shoalster-EG194AA-ABA-A1250N:~$ pastebinit /var/log/pm-suspend.log
 Whoops.  Same problem today.  No results for code :
SUSPEND_MODULES="8139too"
   


The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>
shoalster@shoalster-EG194AA-ABA-A1250N:~$ 

shoalster@shoalster-EG194AA-ABA-A1250N:~$ cat /var/log/syslog | grep PM:
Oct 21 10:59:06 shoalster-EG194AA-ABA-A1250N kernel: [ 8231.380150] PM: Syncing filesystems ... done.
Oct 21 10:59:06 shoalster-EG194AA-ABA-A1250N kernel: [ 8231.485522] PM: Preparing system for mem sleep
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8231.783311] PM: Entering mem sleep
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8231.898812] PM: suspend of devices complete after 115.281 msecs
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8231.899049] PM: late suspend of devices complete after 0.232 msecs
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8231.912149] PM: noirq suspend of devices complete after 13.096 msecs
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8231.912347] PM: Saving platform NVS memory
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8232.016325] PM: Restoring platform NVS memory
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8232.076229] PM: noirq resume of devices complete after 47.875 msecs
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8232.076397] PM: early resume of devices complete after 0.133 msecs
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8240.528062] PM: resume of devices complete after 8451.660 msecs
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8240.528348] PM: Finishing wakeup.
Oct 21 11:35:34 shoalster-EG194AA-ABA-A1250N kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 21 11:35:34 shoalster-EG194AA-ABA-A1250N kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
Oct 21 11:35:34 shoalster-EG194AA-ABA-A1250N kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
Oct 21 11:35:34 shoalster-EG194AA-ABA-A1250N kernel: [    0.164284] PM: Registering ACPI NVS region [mem 0xbbef0000-0xbbef2fff] (12288 bytes)
Oct 21 11:35:34 shoalster-EG194AA-ABA-A1250N kernel: [    0.890860] PM: Hibernation image not present or could not be loaded.
shoalster@shoalster-EG194AA-ABA-A1250N:~$

---

### Post by Toz on 2013-10-21
> The program 'pastebinit' can be found in the following packages:
* pastebinit
* pastebinit
Try: sudo apt-get install <selected package>Can you either install the **pastebinit** program and rerun the command, or copy/paste back the contents of /var/log/pm-suspend.log within **[noparse]```
 
```[/noparse]** blocks.

Can you post back the contents of /etc/pm/config.d/modules?

And can you try the following procedure:
1. Unload 8139too:
```
sudo modprobe -r 8139too
```
2. Suspend:
```
sudo pm-suspend
```
3. Resume the computer from suspend

4. Reload the module:
```
sudo modprobe 8139too
```
5. Test the network connection.

---

### Post by Shoalster on 2013-10-21
shoalster@shoalster-EG194AA-ABA-A1250N:~$ sudo apt-get install pastebinit
[sudo] password for shoalster: 
Sorry, try again.
[sudo] password for shoalster: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python-configobj
The following NEW packages will be installed:
  pastebinit python-configobj
0 upgraded, 2 newly installed, 0 to remove and 14 not upgraded.
Need to get 254 kB of archives.
After this operation, 1,744 kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy/main python-configobj all 4.7.2+ds-5 [238 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy/main pastebinit all 1.3-4ubuntu1 [15.9 kB]
Fetched 254 kB in 2s (124 kB/s)       
Selecting previously unselected package python-configobj.
(Reading database ... 199676 files and directories currently installed.)
Unpacking python-configobj (from .../python-configobj_4.7.2+ds-5_all.deb) ...
Selecting previously unselected package pastebinit.
Unpacking pastebinit (from .../pastebinit_1.3-4ubuntu1_all.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up python-configobj (4.7.2+ds-5) ...
Setting up pastebinit (1.3-4ubuntu1) ...
shoalster@shoalster-EG194AA-ABA-A1250N:~$ pastebinit /var/log/pm-suspend.log
[http://paste.ubuntu.com/6278854/](http://paste.ubuntu.com/6278854/)

shoalster@shoalster-EG194AA-ABA-A1250N:~$ cat /var/log/syslog | grep PM:
Oct 21 10:59:06 shoalster-EG194AA-ABA-A1250N kernel: [ 8231.380150] PM: Syncing filesystems ... done.
Oct 21 10:59:06 shoalster-EG194AA-ABA-A1250N kernel: [ 8231.485522] PM: Preparing system for mem sleep
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8231.783311] PM: Entering mem sleep
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8231.898812] PM: suspend of devices complete after 115.281 msecs
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8231.899049] PM: late suspend of devices complete after 0.232 msecs
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8231.912149] PM: noirq suspend of devices complete after 13.096 msecs
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8231.912347] PM: Saving platform NVS memory
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8232.016325] PM: Restoring platform NVS memory
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8232.076229] PM: noirq resume of devices complete after 47.875 msecs
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8232.076397] PM: early resume of devices complete after 0.133 msecs
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8240.528062] PM: resume of devices complete after 8451.660 msecs
Oct 21 11:32:21 shoalster-EG194AA-ABA-A1250N kernel: [ 8240.528348] PM: Finishing wakeup.
Oct 21 11:35:34 shoalster-EG194AA-ABA-A1250N kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 21 11:35:34 shoalster-EG194AA-ABA-A1250N kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
Oct 21 11:35:34 shoalster-EG194AA-ABA-A1250N kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
Oct  21 11:35:34 shoalster-EG194AA-ABA-A1250N kernel: [    0.164284] PM:  Registering ACPI NVS region [mem 0xbbef0000-0xbbef2fff] (12288 bytes)
Oct 21 11:35:34 shoalster-EG194AA-ABA-A1250N kernel: [    0.890860] PM: Hibernation image not present or could not be loaded.
shoalster@shoalster-EG194AA-ABA-A1250N:~$

---

### Post by Shoalster on 2013-10-21
```
http://paste.ubuntu.com/6278949/
```

---

### Post by Toz on 2013-10-21
Can you post back the contents of **/etc/pm/sleep.d/50unload_alx** and **/etc/pm/config.d/modules**?

Did the unload process from my post #13 work?

---

### Post by pompel9 on 2013-10-21
That worked for me, thanks :)

Just one odd thing, the kernel drive in use was RTL8723AE and now it has changed to alx.
I don't care about that, as long as it works. But I am curious why the kernel drive changed. This happened when I used the procedure in post #13.

I used the command to unload with 8139too, instead of RTL8723AE. That didn't do anything. So I checked the kernel drive again, and now it said it used kernel drive alx. When I used alx on those commands, it worked.

---

### Post by Shoalster on 2013-10-21
Yes post 13 worked.  As to the contents requested above " no such file or directory"

---

### Post by Toz on 2013-10-21
> **pompel9 said:**
> That worked for me, thanks :)

Just one odd thing, the kernel drive in use was RTL8723AE and now it has changed to alx.
I don't care about that, as long as it works. But I am curious why the kernel drive changed. This happened when I used the procedure in post #13.

I used the command to unload with 8139too, instead of RTL8723AE. That didn't do anything. So I checked the kernel drive again, and now it said it used kernel drive alx. When I used alx on those commands, it worked.
On a fresh boot, which kernel driver is in use? 
What is the complete "lsmod" listing?

---

### Post by Toz on 2013-10-21
> **Shoalster said:**
> Yes post 13 worked.  As to the contents requested above " no such file or directory"
?? I don't understand.

Please post back:
```
cat /etc/pm/sleep.d/50unload_alx
```
...and
```
/etc/pm/config.d/modules
```

---

### Post by Shoalster on 2013-10-21
"No such file or directory"  to both.

---

### Post by Toz on 2013-10-22
Do this:

1. Create the file:
```
sudo -i gedit /etc/pm/config.d/modules
```
...enter your password when prompted.

2. Copy/paste the following information into the gedit window:
```
SUSPEND_MODULES="8139too"
```

3. Save the file.

4. Try a suspend/resume cycle.

5. Does the network work after resume?

---

### Post by pompel9 on 2013-10-22
> **Toz said:**
> On a fresh boot, which kernel driver is in use? 
What is the complete "lsmod" listing?

Still alx.

Here is the output for lsmod.

```
Module                  Size  Used by
nvram                  14362  0 
btusb                  28267  0 
parport_pc             32701  0 
ppdev                  17671  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
rts5139               331166  0 
rfcomm                 69070  12 
bnep                   19564  2 
bluetooth             371874  22 bnep,btusb,rfcomm
binfmt_misc            17468  1 
joydev                 17377  0 
nls_iso8859_1          12713  1 
kvm_amd                59958  0 
kvm                   431315  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
microcode              23518  0 
arc4                   12608  2 
psmouse                97626  0 
serio_raw              13413  0 
ip6t_REJECT            12910  1 
xt_hl                  12521  6 
ip6t_rt                13507  3 
k10temp                13126  0 
nf_conntrack_ipv6      18938  7 
nf_defrag_ipv6         34616  1 nf_conntrack_ipv6
shpchp                 37032  0 
i2c_piix4              22106  0 
ipt_REJECT             12541  1 
xt_LOG                 17718  10 
rtl8723ae              86524  0 
rtl_pci                26641  1 rtl8723ae
rtlwifi                63229  2 rtl_pci,rtl8723ae
xt_limit               12711  13 
mac80211              596969  3 rtl_pci,rtlwifi,rtl8723ae
xt_tcpudp              12884  18 
cfg80211              479757  2 mac80211,rtlwifi
xt_addrtype            12635  4 
ohci_pci               13561  0 
snd_hda_codec_realtek    51465  1 
nf_conntrack_ipv4      15012  7 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_conntrack           12760  14 
toshiba_bluetooth      12852  0 
ip6table_filter        12815  1 
ip6_tables             27025  1 ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12741  0 
nf_nat                 26653  1 nf_nat_ftp
nf_conntrack_ftp       18608  1 nf_nat_ftp
nf_conntrack           91736  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
x_tables               34059  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
snd_hda_codec_hdmi     41276  1 
snd_hda_intel          48171  5 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
mac_hid                13205  0 
fglrx                6732934  163 
video                  19318  0 
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
amd_iommu_v2           19025  1 fglrx
soundcore              12680  1 snd
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
sdhci_pci              18985  0 
sdhci                  42630  1 sdhci_pci
alx                    32255  0 
ahci                   25819  3 
libahci                31898  1 ahci
mdio                   13807  1 alx

```

---

### Post by Toz on 2013-10-22
> **pompel9 said:**
> Still alx.

Here is the output for lsmod.

```
Module                  Size  Used by
nvram                  14362  0 
btusb                  28267  0 
parport_pc             32701  0 
ppdev                  17671  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
rts5139               331166  0 
rfcomm                 69070  12 
bnep                   19564  2 
bluetooth             371874  22 bnep,btusb,rfcomm
binfmt_misc            17468  1 
joydev                 17377  0 
nls_iso8859_1          12713  1 
kvm_amd                59958  0 
kvm                   431315  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
microcode              23518  0 
arc4                   12608  2 
psmouse                97626  0 
serio_raw              13413  0 
ip6t_REJECT            12910  1 
xt_hl                  12521  6 
ip6t_rt                13507  3 
k10temp                13126  0 
nf_conntrack_ipv6      18938  7 
nf_defrag_ipv6         34616  1 nf_conntrack_ipv6
shpchp                 37032  0 
i2c_piix4              22106  0 
ipt_REJECT             12541  1 
xt_LOG                 17718  10 
rtl8723ae              86524  0 
rtl_pci                26641  1 rtl8723ae
rtlwifi                63229  2 rtl_pci,rtl8723ae
xt_limit               12711  13 
mac80211              596969  3 rtl_pci,rtlwifi,rtl8723ae
xt_tcpudp              12884  18 
cfg80211              479757  2 mac80211,rtlwifi
xt_addrtype            12635  4 
ohci_pci               13561  0 
snd_hda_codec_realtek    51465  1 
nf_conntrack_ipv4      15012  7 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_conntrack           12760  14 
toshiba_bluetooth      12852  0 
ip6table_filter        12815  1 
ip6_tables             27025  1 ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12741  0 
nf_nat                 26653  1 nf_nat_ftp
nf_conntrack_ftp       18608  1 nf_nat_ftp
nf_conntrack           91736  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
x_tables               34059  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
snd_hda_codec_hdmi     41276  1 
snd_hda_intel          48171  5 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
mac_hid                13205  0 
fglrx                6732934  163 
video                  19318  0 
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
amd_iommu_v2           19025  1 fglrx
soundcore              12680  1 snd
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
sdhci_pci              18985  0 
sdhci                  42630  1 sdhci_pci
alx                    32255  0 
ahci                   25819  3 
libahci                31898  1 ahci
mdio                   13807  1 alx

```

rtl8723ae is your wireless network driver while alx is your wired network driver.

---

### Post by pompel9 on 2013-10-22
> **Toz said:**
> rtl8723ae is your wireless network driver while alx is your wired network driver.

Then why does I get this?

```
01:00.0 Ethernet controller: Qualcomm Atheros AR8162 Fast Ethernet (rev 10)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: alx
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter

```

---

### Post by Toz on 2013-10-22
> **pompel9 said:**
> Then why does I get this?

```
01:00.0 Ethernet controller: Qualcomm Atheros AR8162 Fast Ethernet (rev 10)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: alx
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter

```

The grep command is returning one line too many. You could try:
```
lspci -k | grep -iA2 network
```
...and
```
lspci -l | grep -iA2 ethernet
```
...for wireless and wired respectively.

---

### Post by Shoalster on 2013-10-22
It works if I wake from suspend within 2 or 3 minutes.  If I wait longer, then network will not resume.  Also, must do hard reboot as shutdown or restart will not work when network doesn't resume.

---

### Post by Toz on 2013-10-22
> **Shoalster said:**
> It works if I wake from suspend within 2 or 3 minutes.  If I wait longer, then network will not resume.  Also, must do hard reboot as shutdown or restart will not work when network doesn't resume.
What does the following command return:
```
cat "/sys/bus/pci/devices/0000:02:03.0/power/control"
```

If it returns "auto", try:
```
echo "on" | sudo tee "/sys/bus/pci/devices/0000:02:03.0/power/control"
```
...then try suspend, wait for 5 minutes, then resume and see if it works now.

---

### Post by Shoalster on 2013-10-22
The first command returned: on

  I did suspend and waited 5 minutes and it worked .    I'll suspend and check in about an hour as I need to leave for that long.   Will post then.

 After nearly two hours network will not wake.

---

### Post by Toz on 2013-10-22
I think you're best next step is to create a bug report. To start the reporting process:
```
ubuntu-bug linux
```

---

### Post by Shoalster on 2013-10-22
Ok  Thanks.

---

### Post by pompel9 on 2013-10-23
> **Toz said:**
> The grep command is returning one line too many. You could try:
```
lspci -k | grep -iA2 network
```
...and
```
lspci -l | grep -iA2 ethernet
```
...for wireless and wired respectively.

Thanks. It shows correctly when I use the first command.



```
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter
    Subsystem: Realtek Semiconductor Co., Ltd. Device 0724
    Kernel driver in use: rtl8723ae
```

---

