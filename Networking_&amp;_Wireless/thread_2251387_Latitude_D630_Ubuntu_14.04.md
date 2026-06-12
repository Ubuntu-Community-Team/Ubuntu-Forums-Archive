---
title: "Latitude D630 Ubuntu 14.04"
date: 2014-11-04
forum: Networking &amp; Wireless
---

### Post by russell10 on 2014-11-04
I have had this laptop for a few years. It used to run wireless just fine. It took me awhile to configure it when I first loaded Ubuntu, but I finally figured it out, and it ran fine until 14.04. I somehow, after HOURS, I managed to get it to work for a few days, but then automatic updates loaded and it quit again. I have tried all the forums and web-sites I can, but I cannot seem to get it right again. My wireless indicator is gone, and there is no indicator of a wireless card in my network settings...my wired works fine.

I ran [COLOR=#000000][FONT=Ubuntu Mono]lspci -nn -d 14e4: and this is the print out.

[/FONT][/COLOR]russell@russell-Latitude-D630:~$ lspci -nn -d 14e4:
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Please help!

---

### Post by Hadaka on 2014-11-04
Hi, please post the output of..
```
uname -r && cat /etc/issue
lspci -nnk | grep -iA3 net
rfkill lst all
lsmod
```
thanks.

---

### Post by russell10 on 2014-11-04
Thanks!

russell@russell-Latitude-D630:~$ uname -r && cat /etc/issue 
3.13.0-39-generic
Ubuntu 14.04.1 LTS \n \l


russell@russell-Latitude-D630:~$ lspci -nnk | grep -iA3 net 
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
	Subsystem: Dell Device [1028:01f9]
	Kernel driver in use: tg3
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
	Kernel driver in use: b43-pci-bridge
russell@russell-Latitude-D630:~$ rfkill lst all
Usage:	rfkill [options] command
Options:
	--version	show version (0.5-1ubuntu1 (Ubuntu))
Commands:
	help
	event
	list [IDENTIFIER]
	block IDENTIFIER
	unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
	<idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm nfc
russell@russell-Latitude-D630:~$ lsmod 
Module                  Size  Used by
nvram                  14027  0 
cuse                   13213  3 
gpio_ich               13229  0 
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
snd_hda_codec_idt      48942  1 
dell_laptop            17808  0 
dcdbas                 14448  1 dell_laptop
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342208  10 bnep,rfcomm
kvm_intel             132620  0 
kvm                   388270  1 kvm_intel
nfsd                  247797  2 
binfmt_misc            13140  1 
auth_rpcgss            48979  1 nfsd
nfs_acl                12733  1 nfsd
nfs                   205101  0 
lockd                  78518  2 nfs,nfsd
sunrpc                242738  6 nfs,nfsd,auth_rpcgss,lockd,nfs_acl
fscache                56756  1 nfs
joydev                 17101  0 
serio_raw              13230  0 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
pcmcia                 51828  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
parport_pc             31981  0 
ppdev                  17391  0 
snd                    60939  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                16864  0 
yenta_socket           40201  0 
pcmcia_rsrc            18319  1 yenta_socket
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
b43                   356470  0 
ssb_hcd                12749  0 
bcma                   42043  1 b43
soundcore              12600  1 snd
mac80211              546051  1 b43
i915                  709887  4 
drm_kms_helper         48868  1 i915
mac_hid                13037  0 
drm                   244037  5 i915,drm_kms_helper
cfg80211              409394  2 b43,mac80211
i2c_algo_bit           13197  1 i915
video                  18903  1 i915
wmi                    18673  1 dell_wmi
coretemp               13195  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
psmouse                91357  0 
firewire_ohci          35529  0 
firewire_core          61867  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
usbhid                 47070  0 
hid                    87604  3 hid_generic,usbhid
tg3                   152132  0 
ptp                    18445  1 tg3
ssb                    51854  2 b43,ssb_hcd
pps_core               18799  1 ptp
russell@russell-Latitude-D630:~$

---

### Post by Hadaka on 2014-11-04
Hi please run this script for more detail diagnostics
```
http://ubuntuforums.org/showthread.php?t=370108
```
thanks

---

### Post by russell10 on 2014-11-04
Is this what you mean?

russell@russell-Latitude-D630:~$ [http://ubuntuforums.org/showthread.php?t=370108bash:](http://ubuntuforums.org/showthread.php?t=370108bash:) [http://ubuntuforums.org/showthread.php?t=370108:](http://ubuntuforums.org/showthread.php?t=370108:) No such file or directory
russell@russell-Latitude-D630:~$ 

I'm not sure what you mean by "run this thread".

---

### Post by russell10 on 2014-11-04
OK, I got it...go to that site and follow the instructions...got it.

---

### Post by russell10 on 2014-11-04
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise Release
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main Translation-en
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Ign [http://download.videolan.org](http://download.videolan.org)  InRelease                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed InRelease                     
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://download.videolan.org](http://download.videolan.org)  Release.gpg                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb InRelease                          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [59.7 kB]             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://download.videolan.org](http://download.videolan.org)  Release                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed Release.gpg [933 B]         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps i386 Packages                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://download.videolan.org](http://download.videolan.org)  Sources                                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [62.0 kB]            
Hit [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/games i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://download.videolan.org](http://download.videolan.org)  Packages                                     
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [48.6 kB]        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed Release [110 kB]            
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:9 [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en [4,434 B]    
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [11.2 kB]   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [698 B]   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:12 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en [3,919 B]    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [145 kB]  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [50.3 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Ign [http://download.videolan.org](http://download.videolan.org)  Translation-en_US                            
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1,401 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Ign [http://download.videolan.org](http://download.videolan.org)  Translation-en                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [134 kB]       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [1,408 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [89.3 kB]  
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [3,517 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [346 kB] 
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps Translation-en_US             
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps Translation-en                
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [5,820 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [216 kB]
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/games Translation-en_US            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [9,546 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/games Translation-en               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/restricted i386 Packages [14 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/main i386 Packages [129 kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/multiverse i386 Packages [14 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/universe i386 Packages [20.4 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 1,455 kB in 8s (169 kB/s)                                              
W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


E: Some index files failed to download. They have been ignored, or old ones used instead.
russell@russell-Latitude-D630:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libbit-vector-perl libcarp-clan-perl libclass-data-inheritable-perl
  libclass-method-modifiers-perl libcrypt-openssl-bignum-perl
  libcrypt-openssl-rsa-perl libdata-random-perl libdate-calc-perl
  libdate-calc-xs-perl libgd-perl libgnome2-gconf-perl libmouse-perl
  libnet-dropbox-api-perl libnet-oauth-perl
Use 'apt-get autoremove' to remove them.

---

### Post by russell10 on 2014-11-04
russell@russell-Latitude-D630:~$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2014-11-03 22:49:32--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 107.20.203.119
Connecting to dl.dropbox.com (dl.dropbox.com)|107.20.203.119|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script) [following]
--2014-11-03 22:49:32--  [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script)
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 54.225.187.78, 54.221.224.104, 50.16.204.87, ...
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|54.225.187.78|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Cookie coming from dl.dropboxusercontent.com attempted to set domain to dropbox.com
Cookie coming from dl.dropboxusercontent.com attempted to set domain to dropbox.com
Location: [https://dl.dropboxusercontent.com/u/57264241/wireless_script](https://dl.dropboxusercontent.com/u/57264241/wireless_script) [following]
--2014-11-03 22:49:33--  [https://dl.dropboxusercontent.com/u/57264241/wireless_script](https://dl.dropboxusercontent.com/u/57264241/wireless_script)
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|54.225.187.78|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13362 (13K) [text/plain]
Last-modified header missing -- time-stamps turned off.
--2014-11-03 22:49:33--  [https://dl.dropboxusercontent.com/u/57264241/wireless_script](https://dl.dropboxusercontent.com/u/57264241/wireless_script)
Reusing existing connection to dl.dropboxusercontent.com:443.
HTTP request sent, awaiting response... 200 OK
Length: 13362 (13K) [text/plain]
Saving to: &#8216;wireless_script&#8217;


100%[======================================>] 13,362      --.-K/s   in 0s      


2014-11-03 22:49:33 (252 MB/s) - &#8216;wireless_script&#8217; saved [13362/13362]

---

### Post by Hadaka on 2014-11-04
almost..you are close...please open a terminal
then copy and paste this..
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
to the terminal, follow the directions and it will build a file called wireless-info-text
then copy and paste that file...info-text file...here
thanks.,

---

### Post by russell10 on 2014-11-04
########## wireless info START ##########


Report from: 03 Nov 2014 23:33 PST -0800


Booted last: 03 Nov 2014 00:00 PST -0800


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:31:23 UTC 2014 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


GNOME


##### lspci #############################


09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
	Subsystem: Dell Device [1028:01f9]
	Kernel driver in use: tg3


0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
	Kernel driver in use: b43-pci-bridge


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


##### rfkill ############################


0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
dell_laptop            17808  0 
dcdbas                 14448  1 dell_laptop
b43                   356470  0 
ssb_hcd                12749  0 
bcma                   42043  1 b43
mac80211              546051  1 b43
cfg80211              409394  2 b43,mac80211
wmi                    18673  1 dell_wmi
ssb                    51854  2 b43,ssb_hcd


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fedc:21fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:145788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:193954390 (193.9 MB)  TX bytes:9648652 (9.6 MB)
          Interrupt:17 


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/MissionSpringsGuest]] (600 root)
[connection] id=MissionSpringsGuest | type=802-11-wireless
[802-11-wireless] ssid=MissionSpringsGuest | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/MissionSprings 1]] (600 root)
[connection] id=MissionSprings 1 | type=802-11-wireless
[802-11-wireless] ssid=MissionSprings | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/PCOE-Guest]] (600 root)
[connection] id=PCOE-Guest | type=802-11-wireless
[802-11-wireless] ssid=PCOE-Guest | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Auto ATT688]] (600 root)
[connection] id=Auto ATT688 | type=802-11-wireless
[802-11-wireless] ssid=ATT688 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ATT688]] (600 root)
[connection] id=ATT688 | type=802-11-wireless
[802-11-wireless] ssid=ATT688 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Hotspot]] (600 root)
[connection] id=Hotspot | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=russell-Latitude-D630 | mac-address=<MAC address>
[ipv4] method=shared
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Auto sheraton_lobby]] (600 root)
[connection] id=Auto sheraton_lobby | type=802-11-wireless
[802-11-wireless] ssid=sheraton_lobby | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Westminster]] (600 root)
[connection] id=Westminster | type=802-11-wireless
[802-11-wireless] ssid=Westminster | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MidtownMicro4G]] (600 root)
[connection] id=MidtownMicro4G | type=802-11-wireless
[802-11-wireless] ssid=MidtownMicro4G | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SureWest-55]] (600 root)
[connection] id=SureWest-55 | type=802-11-wireless
[802-11-wireless] ssid=SureWest-55 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MissionSpringsGuest 1]] (600 root)
[connection] id=MissionSpringsGuest 1 | type=802-11-wireless
[802-11-wireless] ssid=MissionSpringsGuest | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/PSAV_Event_Solutions]] (600 root)
[connection] id=PSAV_Event_Solutions | type=802-11-wireless
[802-11-wireless] ssid=PSAV_Event_Solutions | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/MissionSprings]] (600 root)
[connection] id=MissionSprings | type=802-11-wireless
[802-11-wireless] ssid=MissionSprings | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/MSStaff]] (600 root)
[connection] id=MSStaff | type=802-11-wireless
[802-11-wireless] ssid=MSStaff | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

---

### Post by russell10 on 2014-11-04
##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


##### module infos ######################


[b43]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     7ABBDDCA84C087640B27AE6
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A6:96:31:EE:84:32:BD:22:00:4B:A4:DA:A9:78:CF:D9:2C:D5:5E:69
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

---

### Post by russell10 on 2014-11-04
[ssb_hcd]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     2A4C0EB5791EE9A11133FCB
depends:        ssb
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A6:96:31:EE:84:32:BD:22:00:4B:A4:DA:A9:78:CF:D9:2C:D5:5E:69
sig_hashalgo:   sha512

---

### Post by russell10 on 2014-11-04
[bcma]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A6:96:31:EE:84:32:BD:22:00:4B:A4:DA:A9:78:CF:D9:2C:D5:5E:69
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A6:96:31:EE:84:32:BD:22:00:4B:A4:DA:A9:78:CF:D9:2C:D5:5E:69
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

---

### Post by russell10 on 2014-11-04
[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A6:96:31:EE:84:32:BD:22:00:4B:A4:DA:A9:78:CF:D9:2C:D5:5E:69
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A6:96:31:EE:84:32:BD:22:00:4B:A4:DA:A9:78:CF:D9:2C:D5:5E:69
sig_hashalgo:   sha512

---

### Post by russell10 on 2014-11-04
##### module parameters #################


[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp


coretemp
b43

---

### Post by russell10 on 2014-11-04
##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (prism2_usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[   18.047111] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   18.047167] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.


########## wireless info END ############

---

### Post by russell10 on 2014-11-04
Got it...sorry about all the pieces...it was too big.

---

### Post by Hadaka on 2014-11-04
Hi, nothing is really standing out as to why you have a problem.
i noticed you were not able to get the entire wireless report on
ide like to see the bottom end of it if possible,.
also please do...
```
sudo apt-get update
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe b43
```
you might also try powering every thing down...includeing the router
and let everyting reset,

[   18.047111] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found  <- yup the reload of the firmware should fix this

---

### Post by russell10 on 2014-11-04
Thank you SOOOOO much! I write you this thanks wirelessly! I have tried all those commands at various times, but obviously not in the right order.

---

### Post by Hadaka on 2014-11-04
Glad that worked !!
Please mark your thread SOLVED
How to ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks

---

