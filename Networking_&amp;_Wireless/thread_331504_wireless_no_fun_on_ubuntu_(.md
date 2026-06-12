---
title: "wireless no fun on ubuntu :("
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by jbeiter on 2007-01-04
I can't for the life of me get this wireless to sync up with my company's APs. They are using Cisco with a hidden SSID. EAP, PEAP with the rest of the alphabet soup added in.

It's a Dell D820 with an Intel 3945ABG. Ubuntu 6.10, fully updated.

I'm trying to use wpa_supplication... my config file:

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
        ssid="XV2245"
        scan_ssid=1
       stakey=1
       proto=RSN
       key_mgmt=WPA-EAP
       pairwise=TKIP CCMP
       group=TKIP
        eap=PEAP
       phase1="peapver=1"
        phase2="auth=MSCHAPV2"
        identity="ourdomain/myMSuid"
        password="myMSpw"
        ca_cert="/usr/local/ssl/mycert.pem"
#       priority=10
}



This is what is happening with wpa_supplicant in debug:

 wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant/wpa_supplicant.conf -ddd
Initializing interface 'eth1' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=2
Line: 6 - start of a new network block
ssid - hexdump_ascii(len=7):
     57 56 5c 43 3e 32 35                              XV2245         
scan_ssid=1 (0x1)
stakey=1 (0x1)
proto: 0x2
key_mgmt: 0x1
pairwise: 0x18
group: 0x8
eap methods - hexdump(len=16): 00 00 00 00 19 00 00 00 00 00 00 00 00 00 00 00
phase1 - hexdump_ascii(len=9):
     70 65 61 70 76 65 72 3d 31                        peapver=1       
phase2 - hexdump_ascii(len=13):
     61 75 74 68 3d 4d 53 43 48 41 50 56 32            auth=MSCHAPV2   
identity - hexdump_ascii(len=17):
     73 61 78 6f 6e 62 75 72 67 2f 6a 62 65 69 74 65   ourdomain/mymsuid
     72                                                r               
password - hexdump_ascii(len=8): [REMOVED]
ca_cert - hexdump_ascii(len=25):
     2f 75 73 72 2f 6c 6f 63 61 6c 2f 73 73 6c 2f 6d   /usr/local/ssl/m
     79 63 65 72 74 2e 70 65 6d                        ycert.pem       
Priority group 0
   id=0 ssid='XV2245'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=20 WE(source)=16 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:18:de:9c:33:7e
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth1
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'XV2245'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK CCMP
WPA: using KEY_MGMT 802.1X
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 01 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 60 sec 0 usec
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b1a len=16
------------------------------------------------------------------------------------------

It's not even getting to the authentication on the AP's (no username/password info in logging)

Any clues for me? I can't even see where it is breaking and it never associates:

-----------------------------------------------------------------
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"XV2245"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:19208   Missed beacon:0

------------------------------------------------------------------------------------------------

iwlist eth1 scanning

eth1      Scan completed :
          Cell 02 - Address: 00:0B:85:52:19:FF
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=79/100  Signal level=-55 dBm  Noise level=-55 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : TKIP CCMP 
                        Authentication Suites (1) : 802.1X  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : TKIP CCMP 
                        Authentication Suites (1) : 802.1X  
                    Extra: Last beacon: 9504ms ago
          Cell 03 - Address: 00:0B:85:52:A0:8F
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=45/100  Signal level=-82 dBm  Noise level=-82 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : TKIP CCMP 
                        Authentication Suites (1) : 802.1X  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : TKIP CCMP 
                        Authentication Suites (1) : 802.1X  
                    Extra: Last beacon: 1320ms ago

----------------------------------------------------------------------------------------

---

### Post by SugarDaddy on 2007-01-04
It's possible your variables are not quite right for your company's security settings. Click on [[COLOR=Sienna]**this link**[/COLOR]]("http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/wpa_supplicant.conf?rev=HEAD&content-type=text/plain"), which is the 'official' documentatin that is provided for  wpa_supplicant.conf, to see more detailed information on how to configure EAP, PEAP and the rest of the alphabet soup!

Also, one of the problems might be the multiple variables you have listed for proto in your wpa_supplicant.conf file. For hidden SSIDs that require ap_scan=2, the network blocks are supposed to have explicit security settings (as outlined in the above link) and you have TKIP and CCMP both listed. So a first quick pass might be to delete one (I am not sure which, but CCMP=AES and TKIP=TKIP, depends on your company's router). 

Hope this helps!

---

### Post by jbeiter on 2007-01-08
I'm guessing that is the case. For the security settings, I did try each one individually but will try them again to be sure. I've tried so many variations in that file it would be easy to miss.

---

### Post by jbeiter on 2007-01-08
I'm not sure if that got me further or not. I did get a MSCHAP error until I changed my "/" to a "\" so I'd like to think I am getting closer.

I still can't get eth1 to associate with the SSID though.  Can anyone help decipher this debug output?  I can't really tell if it is happy or not, or where it is not happy.  iwevents just show the interface trying to associate with the SSID:
-------------------------------------------------------------------------------------------------
Trying to associate with SSID 'MYHIDDENSSID'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT 802.1X
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 01 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 60 sec 0 usec
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b1a len=16
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:00:00:00:00:00 blacklist count incremented to 4
State: ASSOCIATING -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'MYHIDDENSSID'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT 802.1X
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 01 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 60 sec 0 usec
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b1a len=16
---------------------------------------------------------------------------------------------------

for my config file, I simply removed CCMP from the pairwise, as Sugardaddy suggested.

---

### Post by SugarDaddy on 2007-01-09
Can you please post your /etc/network/interfaces file? Sometimes this is the problem as well.

---

### Post by jbeiter on 2007-01-09
Well it worked when I removed TKIP from the peergroups and changed it to CCMP.

I'm going to wrestle with the interfaces file next, so it will come up automatically and hopefully start dhcp up.

That is, after I get wireless working again.. (in another thread. de-installing nvidia last night broke the wireless and now the interface isn't even showing up.. /sigh so close)

---

### Post by SugarDaddy on 2007-01-09
I struggled with getting my simple WPA2 (=RSN) with AES (=CCMP) encryption and hidden SSID (ap_scan=2) setup for my Intel 2200BG Pro/Wireless card until I finally reinstalled Ubuntu 6.10 and ONLY installed wpa_supplicant. In other words, no ndiswrapper, network manager, wifi radar, etc. Then suddenly it magically worked. Also, I can now successfully connect to multiple APs with various security settings. If it is any help, here is my /etc/network/interfaces and wpa_supplicant.conf output. Since I am very mobile, my card now attempts to connect to APs in the order they are included in the wpa_supplicant config file as network blocks below.

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf 
post-down killall -q wpa_supplicant

``````
ctrl_interface=/var/run/wpa_supplicant 
ap_scan=2 
 
network={ 
    ssid=<removed> 
    scan_ssid=1 
    proto=RSN 
    key_mgmt=WPA-PSK 
    group=CCMP 
    pairwise=CCMP 
    psk=<removed>
#    priority=1 
}
network={
    ssid="school unlocked AP"
    key_mgmt=NONE
}
network={
    ssid="Condo unlocked AP1"
    key_mgmt=NONE
}
network={
    ssid="Condo unlocked AP2"
    key_mgmt=NONE
}

```

---

### Post by jbeiter on 2007-01-09
Thank you very much. This is extremely helpful. Hopefully I can try the interfaces configuration soon!

---

### Post by jbeiter on 2007-01-10
okay I thought this was all set but noticed it wasn't getting associated again. I know I didn't change the config so I started unloading the ipw3945 module and reloading and retrying... sometimes it links up, sometimes it just wont and will flip between trying to join my home ssid and work.

really seems flakey.

I can unload/load ipw3945, watch the wireless associate with the AP (via iwconfig), sometimes eth1 will even get a DHCP address and then it will just drop. When I'm at home, it is rock solid.

Signal is strong, 97%. Could it be that either ipw3945, wext driver, or wpa_supplicant is just buggy with encryption and the added security? The only thing I'm doing at home is mac filtering on the AP (I live in the country with luddites as neighbors)

I'm really really hesitant to start trying to upgrade/reinstall ipw3945 ieee80211 etc... I just got things almost working :(

---

### Post by SugarDaddy on 2007-01-10
The MAC filtering on your router should be a non-issue. I also use MAC filtering but it does not require any additional settings or flags within the interfaces or .conf file.

Unfortunately I don't have any experience with your card. However, it is pretty standard and I would think it should work right out of the box with wpa_supplicant installed and not need ndiswrapper.

I would suggest posting a new thread with your card in the title. That you you are likely to get help from people with experience with your card.

---

### Post by usererror on 2007-01-10
whoa, whoa whoa, you said you got associated and a DHCP address when using PEAP?

I'm in an environment that runs EAP-FAST and LEAP.  We're working on getting it to work in this link:

[http://www.ubuntuforums.org/showthread.php?t=304706](http://www.ubuntuforums.org/showthread.php?t=304706)

Please post your /etc/network/interfaces; i'm very curious!

---

### Post by jbeiter on 2007-01-10
Yes, I do get dhcp responses but it is not consistent. Only a fraction of the times it actually gets associated with the SSID, it gets an address.

I'm starting to wonder if it is thrashing between my home setup and my work setup, regardless if it gets associated to an AP or not.

my interfaces file:
-------------------------------------------------------------------------------------------
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant/wpa_supplicant.conf 
post-down killall -q wpa_supplicant

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
-----------------------------------------------------------------

---

### Post by warkro on 2007-01-10
did you try changing your ap_scan to 1 instead of 2

---

### Post by SugarDaddy on 2007-01-11
Since your work's Cisco router has a hidden SSID you have to set ap_scan=2, not 1. However, this should not interfere with the other network blocks that associate with broadcast SSIDs.

---

### Post by jbeiter on 2007-01-11
Yes, as sugardaddy said, it would not even associate unless I had ap_scan=2. I did try both.

I also tried commenting out my home network but the work one still drops.

Is there something that would un-configure it if the interface is not in use? It seemed like my home network was not configured until I started trying to hit the internet and then it kicked in.

... poking in the dark here at this point.

---

### Post by tribaal on 2007-01-11
Very stupid question, but why don't your guys use nm-applet/NetworkManager to configure your EAP stuff? It sure works pretty well for me... Or maybe you're trying to authenticate on a more complex network?

- trib'

---

### Post by jbeiter on 2007-01-11
I'm not familiar with nm-applet/NetworkManager. Is that a "stock" application? All I've seen is the "Networking" and "Network Tools" under the System->Administration menu. Neither of those are much help at all.

I'm new to Ubuntu

---

### Post by JTux on 2007-01-11
> **jbeiter said:**
> I'm not familiar with nm-applet/NetworkManager. Is that a "stock" application? All I've seen is the "Networking" and "Network Tools" under the System->Administration menu. Neither of those are much help at all.

I'm new to Ubuntu

It can be installed from the Ubuntu repositories. 
Just search for NetworkManager in synaptic.

---

### Post by tribaal on 2007-01-11
This is a screenshot of how I use it to log on to my school's network, it might give you a hint of it it's what you're looking for or not:


- trib'

---

### Post by jbeiter on 2007-01-12
never could find that networkmanager app (in the system or synaptic)  however,

I tried using two wpa_supplicant.conf files.. one for home, one for work. It seemed to be more stable. When I joined up to the work network, I disconnected the wired interface and it has remained associated and attached.... (connected through it right now)

I don't think this configuration can handle two live interfaces, or multiple network definitions in the wpa_supplicant.conf file.

---

### Post by joneberger on 2007-01-12
you don't need ndiswrapper for this card.   i've never used the wpa before so i don't know how difficult this is to get setup.  good luck jbeiter

---

### Post by jbeiter on 2007-02-01
As a final assessment on this thread, I still think the subject says it all. It may be that the troubles I have encountered are unique to the Intel 3945 and the drivers that are available but this experience was anything but easy. It's still flaky too. Even on wireless networks with no security options, I sometimes have to unload the module, kill wpa, and reload the module to make it join properly.

The windows partition on the same machine nails all configured wireless networks reliably and solidly.

Looking forward to improvement in Edgy version 6.10+

---

### Post by mr4thjuly on 2007-02-01
Ok I didn't go thru all the replies (3pgs) wrt your problem but if you still haven't found a solution here is another possible one.
First off if you are using wireless WPA your interface must be ath0 not eth1 or eth0. Thus you need to put the respective lines in your interfaces file under the auto ath0 section.
Secondly you need to turn off the Wifi that is controlled by the Networking GUI. i.e. go to system->administration->networking and uncheck the wireless card option.
I took these steps when I was in a situation resembling 98% of your problem the 2% difference lies in the fact the in have an Atheros wireless card for which Ubuntu uses the readily available madwifi drivers. I also moved the wpa_supplicant.conf file to the /etc directory instead of keeping it in the /etc/wpasupplicant directory.
Open a test connection by doing this 
sudo wpa_supplicant -iath0 -c/etc/wpa_supplicant.conf -Dmadwifi -w
Replace madwifi with your respective driver name use "test" if you are not sure what to use.
Turn on the Wifi that you turned off by following what I wrote under "Secondly...."
Hope this helps.

---

### Post by jbeiter on 2007-02-05
mr4th,

Thanks for the reply. Any suggestions if I am getting "no such device" type errors? The system seems "wired" to marry the wireless with eth1.

Oddly, when I had wpa configured to go to ath0, the NetworkManager applet worked with the wireless for the first time. I could connect to the different company networks seemingly much easier. I just couldn't bind it to a network interface since the system isn't recognizing ath0.

---

### Post by jbeiter on 2007-02-06
okay, can anyone confirm what the previous poster said? That "if you are using wireless WPA your interface must be ath0 not eth1 or eth0"?

I suspect he is right since the wireless tools in NetworkManager magically started working when I configured wpa to work on ath0 but I can't seem to figure out how to make the system recognize the wireless devices on ath0.

Again, I use ipw3945, Intel's wireless.

---

### Post by mr4thjuly on 2007-02-07
OK sorry for the delay in my reply.
I think I had the same problem i.e. binding the wpa to work with the ath0. Ok first off tell me if you did this in your "interfaces" file located in /etc/network
wpa-driver madwifi
wpa-conf /etc/wpa_supplicant.conf
wireless-essid yourSSID
wireless-key s: yourKey

IF you did this and all you have in your wpa_config are your config setting then open a test connection with the command I posted above.
Ok now if you do the CTRL C your connection is bound to go down. Double click on your network icon and in the dropdown list your should see eth0, ath0 and l0. Needless to say you must select ath0. This should bind the ath0 to your WPA settings thru the interfaces files you edited.

Ok here is another trick, its more of a work around. If you can hardwire your laptop to a cable  modem and just download the kubuntu packages via apt-get by doing the following  sudo apt-get install kubuntu-desktop it will install kubuntu. Now log out and change your session to use KDE. Once logged in you can goto KDE->Internet->Wireless lan settings and you should be able to simply select the connection, which will then prompt you for a the WPA passphrase (if it is a WPA connection). This works all the time for me atleast.
If this does not solve your problem in your next post tell me exactly what you did while trying to configure WPA to work with ath0.

---

### Post by jbeiter on 2007-02-08
Thank you for the response!

In my interfaces file I just had the following entry:
---------------------------
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iath0 -c/etc/wpa_supplicant/wpa_supplicant.conf 
post-down killall -q wpa_supplicant
---------------------------

It was my hope (and understanding from other instructions) that in this way I could configure the system to use wireless or wired ethernet depending on what was plugged in. Also, I'm connecting to multiple wireless networks and it *seems* like you are able to specify multiple wireless networks/SSIDs/configs in the wpa config file..

regarding kubuntu, I'm actually running Ubundu Edgy using Gnome. Am I going to foul things up by installing the kubuntu desktop?

This may be a stupid question, but does it matter that I have an integrated Intel 3945 Wireless device? You mentioned an Atheros Wireless Card in your previous post.

---

### Post by mr4thjuly on 2007-02-11
No nothing will go wrong if you install Kubuntu in addition to Ubuntu. Mine works just fine and it gives me the flexibility to use both KDE and GNOME You basically can choose your session on boot i.e. KDE or Gnome. KDE will bring up Kubuntu.
As long as you are using the correct drivers for a wireless device it doesn't matter whether or not it is integrated. My wireless card is integrated as well.
Ok in your interfaces file this is what I want you to do. But first make a backup of the current interfaces file you have and just copy what I am pasting on here, ofcourse you need to replace your respective parameters.

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface ath0 inet dhcp
wpa-driver yourdriver(type "test" if you don't know yours)
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
wireless-essid youSSID
wireless-key s:youkeyorpassphrase

auto ath0

Note: auto ath0 is empty.

Sorry for my delayed replies. I am a busy guy and I only come on here a couple times a week.
Keep us posted on how you are progressing.
Also here is the link on how to install Kubuntu on Unbuntu edgy. It should be a flawless process.
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by jbeiter on 2007-02-13
okay I did this. When I go into the KDE network management tools, the only thing that comes up is eth0 and eth1 (even though I have the configuration stuff in interfaces, like you posted.)

ifconfig ath0 yeilds:

ath0: error fetching interface information: Device not found


I can't quite figure out how to direct the system to put the wireless device on ath0 rather than eth1.

---

### Post by mr4thjuly on 2007-02-14
Don't you see "Wireless Networks" somewhere under your programs menu? I can't tell you exactly where since I have come to realize that it differs based on your system architecture. If you see wireless networks then pull it up and choose your SSID to connect. If a WPA key is required you will be asked for it. 
If none of the above works then copy (and I mean copy not cut and paste) the part under
> iface ath0 inet dhcp
after > auto ath0

---

