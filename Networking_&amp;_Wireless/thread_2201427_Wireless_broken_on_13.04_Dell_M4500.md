---
title: "Wireless broken on 13.04 Dell M4500"
date: 2014-01-24
forum: Networking &amp; Wireless
---

### Post by ship22 on 2014-01-24
Networking is such a mess on this release I don't even know where to start. It was working fine on 12.10.

- First, the gui under System Settings is flaky. Half the time when I hit "network" it says "networking is not compatible with this release". The other half of the time, it works.
- /etc/init.d/networking restart, crashes Unity so badly I have to reboot.
- After adding wlan0 to /etc/network/interfaces (auto, inet, dhcp) the transmitter now comes, on but no networks are detected. My router is in the same room and other devices detect my desired network plus others.  The SSID is in the history, but every one of them say "out of range".  
- Connect to a hidden network does nothing.. So I can't re-add, even though the SSID and password is correct.

Any love from the clue fairy out there?

Really regretting upgrading.

I want to have both eth0 wired and wireless configured... if wired isn't plugged in, then wireless is active. Perhaps this is a bit too complicated for ubuntu? Searching for solutions either yeilds outdated or inadequate instructions.

---

### Post by praseodym on 2014-01-24
Lets check the outputs of
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
cat /etc/network/interfaces
```
Edit: You know that 13.04 is only supported until end of January?

---

### Post by ship22 on 2014-01-27
No I did not realize support was ending this week. Thanks. Even if I have something misconfigured below, this is acting so badly it's probably a good idea to upgrade (or downgrade) anyway.

 lspci -nnk |grep -iA2 net00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 05)
	Subsystem: Dell Device [1028:040c]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)
	Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1321]
	Kernel driver in use: iwlwifi

lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 002 Device 004: ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor

lsmod
Module                  Size  Used by
pci_stub               12550  1 
vboxpci                22896  0 
vboxnetadp             25636  0 
vboxnetflt             27291  0 
vboxdrv               299779  3 vboxnetadp,vboxnetflt,vboxpci
vmnet                  43097  13 
vsock                  39001  0 
vmci                   60394  1 vsock
vmmon                  62793  0 
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202069  10 bnep,rfcomm
nfsv4                 167012  4 
binfmt_misc            17260  1 
autofs4                27436  0 
nfsd                  208648  2 
auth_rpcgss            35160  2 nfsd,nfsv4
nfs_acl                12733  1 nfsd
nfs                   140032  3 nfsv4
lockd                  65628  2 nfs,nfsd
sunrpc                199123  16 nfs,nfsd,auth_rpcgss,lockd,nfsv4,nfs_acl
joydev                 17097  0 
nls_utf8               12493  0 
cifs                  391695  0 
fscache                50782  3 nfs,cifs,nfsv4
snd_hda_codec_hdmi     36185  4 
arc4                   12543  2 
iwldvm                220185  0 
pcmcia                 39544  0 
mac80211              526519  1 iwldvm
coretemp               13131  0 
kvm_intel             126842  0 
kvm                   376505  1 kvm_intel
aesni_intel            18156  0 
aes_i586               16995  1 aesni_intel
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
gf128mul               14503  2 lrw,xts
ablk_helper            13357  1 aesni_intel
cryptd                 15613  1 ablk_helper
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
dell_wmi               12601  0 
snd_rawmidi            25114  1 snd_seq_midi
sparse_keymap          13658  1 dell_wmi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
ppdev                  12817  0 
wmi                    18590  1 dell_wmi
parport_pc             27504  0 
snd_hda_codec_idt      63896  1 
video                  18894  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_hda_intel          38307  3 
yenta_socket           27095  0 
snd_hda_codec         117580  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
iwlwifi               155077  1 iwldvm
snd_hwdep              13272  1 snd_hda_codec
nvidia              10287297  54 
dell_laptop            17161  0 
mac_hid                13037  0 
cfg80211              436177  3 iwlwifi,mac80211,iwldvm
dcdbas                 14021  1 dell_laptop
pcmcia_rsrc            18191  1 yenta_socket
psmouse                81038  0 
microcode              18286  0 
lpc_ich                16925  0 
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
serio_raw              13031  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd                    56485  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
intel_ips              17666  0 
soundcore              12600  1 snd
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
ahci                   25507  3 
libahci                26108  1 ahci
firewire_ohci          35292  0 
sdhci_pci              18158  0 
firewire_core          61718  1 firewire_ohci
sdhci                  31824  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
e1000e                174519  0 

 iwconfig
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
   
vmnet8    no wireless extensions.


lo        no wireless extensions.


eth0      no wireless extensions.


vmnet1    no wireless extensions.





# rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 208.67.222.222
nameserver 208.67.220.220

cat interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto wlan0
iface wlan0 inet dhcp

---

### Post by mörgæs on 2014-01-27
> **ship22 said:**
> No I did not realize support was ending this week. Thanks. Even if I have something misconfigured below, this is acting so badly it's probably a good idea to upgrade (or downgrade) anyway.



If you downgrade then please remember that 12.10 is out of support in april.

---

### Post by praseodym on 2014-01-27
Re-set the interfaces and deactivate the N-mode of the driver (bug):
```

echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Reboot

---

### Post by ship22 on 2014-01-27
thank you, works like a champ now.

---

