---
title: "wireless is being a spaz!"
date: 2014-01-17
forum: Networking &amp; Wireless
---

### Post by james_adamik on 2014-01-17
Ok so i have spent the last 4 days on these forums, looking at every fix and trying everything i can. I loaded ubuntu 12.4 on an assus eeepc with an atheros AR242X / AR542X Wirelss Network Adapter (PCI EXpress). At first wireless would work, and ethernet would not. so i tried tons of different fixes on these baords. Then wirelss stopped working all together. couldnt get the manager to open at all. Then i got it to open doing god knows what in one of the fix's and it showed the wireless networks aviable .. yeah... then it "updated" 400+ files. then wallah wireless was gone again!. Im beyond frustrated at this point. IM usin my other Computer jut to send this mesage cause the asus will not connect in any way. below i will lst all the information i can.

nm- tool
> **(process:5052): warning **: could not initialise NMClient /org/freedesktop/networkmanager: the name org.freedesktop.networkmanager was not provided by any .service files

NetworkManager TOol

State: unknown

**(process:5052): warning **: error: could not detect NetworkManager

The above didnt happen last time i ran it *sigh*

lshw -c network
   > *-network DISABELED

 descrition :Wireless Interface
 Product: AR242X / AR542X Wirelss Network Adapter (PCI EXpress)
 Vender: Qualcom Atheros
 Physical id : 0
 bus info :[EMAIL="pci@0000"]pci@0000[/EMAIL]:01:00.0
 logical name: wlan0
 version: 01
 serial: 00:22:43:38:5a:2a
 width: 64bits
 clock: 33mhz
 capabilities: bus_,aster cap_list ethernet physical wireless
 Configuration: breadcast=yes driver=ath5k driverversion=3.5.0-45-generic firware=N/A latency=0 multicast=IEEE 802.11bg
 resources: irq:17 memory:fbff0000-fbffffff



   

 lsmod  

 > Module                  Size  Used by  

 coretemp               13362  0  
 joydev                 17394  0  
 arc4                   12474  2  
 snd_hda_codec_realtek    64959  1  
 snd_hda_intel          32983  3  
 microcode              18396  0  
 snd_hda_codec         116477  2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep              13277  1 snd_hda_codec  
 parport_pc             32115  0  
 rfcomm                 38104  0  
 bnep                   17791  2  
 ppdev                  12850  0  
 bluetooth             189742  10 rfcomm,bnep  
 snd_pcm                81124  2 snd_hda_intel,snd_hda_codec  
 uvcvideo               72249  0  
 videobuf2_core         32212  1 uvcvideo  
 videodev              100265  2 uvcvideo,videobuf2_core  
 videobuf2_vmalloc      12757  1 uvcvideo  
 snd_seq_midi           13133  0  
 psmouse                91408  0  
 videobuf2_memops       13213  1 videobuf2_vmalloc  
 lpc_ich                16993  0  
 serio_raw              13032  0  
 snd_rawmidi            25426  1 snd_seq_midi  
 snd_seq_midi_event     14476  1 snd_seq_midi  
 ath5k                 137284  0  
 ath                    19436  1 ath5k  
 snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event  
 snd_timer              28932  2 snd_pcm,snd_seq  
 mac80211              475546  1 ath5k  
 snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq  
 cfg80211              181041  3 ath5k,ath,mac80211  
 snd                    62675  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 i915                  479458  3  
 eeepc_laptop           19507  0  
 drm_kms_helper         47459  1 i915  
 sparse_keymap          13659  1 eeepc_laptop  
 soundcore              14636  1 snd  
 drm                   240443  4 i915,drm_kms_helper  
 i2c_algo_bit           13317  1 i915  
 snd_page_alloc         14109  2 snd_hda_intel,snd_pcm  
 video                  19117  1 i915  
 mac_hid                13078  0  
 lp                     17456  0  
 parport                40931  3 parport_pc,ppdev,lp



Iwconfig
    

 > wlan0     IEEE 802.11bg  ESSID:off/any  

           Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Encryption key:off  
           Power Management:on  

            
 lo        no wireless extensions.



iwlist scan
> wlan0        interface doesnt support scanning : network is down

lo             interface doesnt support scanning :


  	 	 	 	   Rfkill list
 

 > 0:  eeepc-wlan: Wireless LAN

 	Soft blocked: no
 	Hard blocked: no
 

 1:  phy0: Wireless LAN

 	Soft blocked: no
 	Hard blocked: no



   lshw -businfo  

 > Bus info          Device     Class       Description  

 ==================================================== 
                              system      900HA (90OAM0VB2A111131U21HQ)  
                              bus         900HA  
                              memory      64KiB BIOS  
 cpu@0                        processor   Intel(R) Atom(TM) CPU N270   @ 1.60GHz  
                              memory      24KiB L1 cache  
                              memory      512KiB L2 cache  
                              processor   Logical CPU  
                              processor   Logical CPU  
                              memory      1GiB System Memory  
                              memory      1GiB DIMM SDRAM Synchronous  
 cpu@1                        processor   Intel(R) Atom(TM) CPU N270   @ 1.60GHz  
                              processor   Logical CPU  
                              processor   Logical CPU  
 pci@0000:00:00.0             bridge      Mobile 945GSE Express Memory Controller  
 pci@0000:00:02.0             display     Mobile 945GSE Express Integrated Graphi  
 pci@0000:00:02.1             display     Mobile 945GM/GMS/GME, 943/940GML Expres  
 pci@0000:00:1b.0             multimedia  NM10/ICH7 Family High Definition Audio  
 pci@0000:00:1c.0             bridge      NM10/ICH7 Family PCI Express Port 1  
 pci@0000:00:1c.1             bridge      NM10/ICH7 Family PCI Express Port 2  
 pci@0000:01:00.0  wlan0      network     AR242x / AR542x Wireless Network Adapte  
 pci@0000:00:1d.0             bus         NM10/ICH7 Family USB UHCI Controller #1  
 pci@0000:00:1d.1             bus         NM10/ICH7 Family USB UHCI Controller #2  
 pci@0000:00:1d.2             bus         NM10/ICH7 Family USB UHCI Controller #3  
 pci@0000:00:1d.3             bus         NM10/ICH7 Family USB UHCI Controller #4  
 pci@0000:00:1d.7             bus         NM10/ICH7 Family USB2 EHCI Controller  
 pci@0000:00:1e.0             bridge      82801 Mobile PCI Bridge  
 pci@0000:00:1f.0             bridge      82801GBM (ICH7-M) LPC Interface Bridge  
 pci@0000:00:1f.2             storage     82801GBM/GHM (ICH7-M Family) SATA Contr  
                   scsi0      storage      
 scsi@0:0.0.0      /dev/sda   disk        160GB ST9160310AS  
 scsi@0:0.0.0,1    /dev/sda1  volume      148GiB EXT4 volume  
 scsi@0:0.0.0,2    /dev/sda2  volume      1014MiB Extended partition  
                   /dev/sda5  volume      1014MiB Linux swap / Solaris partition  
 

 


    ping -c 4 127.0.0.1  
 > PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.  

 64 bytes from 127.0.0.1: icmp_req=1 ttl=64 time=0.111 ms  
 64 bytes from 127.0.0.1: icmp_req=2 ttl=64 time=0.073 ms  
 64 bytes from 127.0.0.1: icmp_req=3 ttl=64 time=0.075 ms  
 64 bytes from 127.0.0.1: icmp_req=4 ttl=64 time=0.073 ms  
 

 --- 127.0.0.1 ping statistics ---  
 4 packets transmitted, 4 received, 0% packet loss, time 2997ms  
 rtt min/avg/max/mdev = 0.073/0.083/0.111/0.016 ms



That is all i can think to give you upfront... feel free to request a thousand different things if thats what it takes to fice this agrivating problem.

---

### Post by Tomtompiper on 2014-01-17
Hi, I don't have a solution to your immiediate problem but if you have an Android smartphone you can disable the data connection, turn on the wifi and plug it into the computer to get a working wired connection to help you troubleshoot the connection. Save you having to use another PC to send and recieve messages.

---

### Post by james_adamik on 2014-01-17
used sudo service network-manager start

now i have the manager open in the upper bar again but still nothing else

and no adroid device to use.

Yet another update..

I used my desktop to create a hotspot. Then created a manual connection on the eeepc laptop. typed in all the connectivity information and etc and now the laptop is connecting to the internet through the hot sport connection and even shows the other wireless networks in range. I am afriad however that if i disconnect the Hotspot on my desktop we will lose the wireless on the laptop. But at least now i dont have to relay information :)

---

