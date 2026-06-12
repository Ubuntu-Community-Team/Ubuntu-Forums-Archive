---
title: "How do I get Ubuntu 13.04 to prefer WiFi for internet?"
date: 2013-10-14
forum: Networking &amp; Wireless
---

### Post by Ella_Bella on 2013-10-14
I'm having difficulty getting Ubuntu to prefer WiFi for internet access, and ignore Ethernet as a resource for that. I only want to use Ethernet for a direct cable connection between two computers to do a SAMBA share with static IPs. This is something I've made work just fine for years with OS X and Windows 7/8. They seem to auto-detect the right preferences for where to source internet access from, but Ubuntu seems to need to be told? 

What I've tried:

( [http://ubuntuforums.org/showthread.php?t=1499325&p=10228328#post10228328](http://ubuntuforums.org/showthread.php?t=1499325&p=10228328#post10228328) ) I edited the Ethernet connection to route using the preference "Use this connection only for resources on this network", which other people have reported having success with as a means of getting WiFi preferred, but it doesn't work for me. The issue persists. Ethernet is still being preferred for internet, and WiFi gets ignored. 

What else can I try?

---

### Post by varunendra on 2013-10-14
Welcome to the forums Ella_Bella. :)

Can you confirm the ethernet settings were saved and that the wifi connection has gateway and dns addresses attached with it?
Can you try a manual IP configuration if required?
And most importantly, have you checked if the wifi is active at all when the ethernet connection is working too? Some BIOS have this inbuilt 'feature' to disable wifi when a cable connection is detected. So just to rule out that possibility.

Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
nm-tool
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by Ella_Bella on 2013-10-14
Thanks so much for the prompt reply! :)

Ethernet settings are saved. 

Wifi connection has gateway and dns addresses. I'm using it to write this message. 

I would have to play with my router's admin panel to set my Wifi to use a manual IP address. I use a DHCP service for Wifi, so I don't know why you would ask me to do that? My problem is with interface preference surrounding Ethernet when a cable is detected.

My Wifi is active and I am using it right now to write this. I can't test ethernet with internet because I'm not near my router, which is why I use Wifi, and it's not the use-case I'm looking for. There is no problem with the BIOS because this machine has run Windows Vista, 7 and 8, and ALL have worked with wifi/internet while the ethernet port is used for other things since 2009 :) It's only ubuntu that starts ignoring Wifi and tries to use ethernet when it detects a cable plugged in after the fact, despite already having a live internet connection with Wifi.

nm-tool:
```
NetworkManager Tool

State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             disconnected
  Default:           no
  HW Address:        00:23:8B:6E:FD:63


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on




- Device: wlan0  [my_SSID] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:21:6B:60:0F:8A


  Capabilities:
    Speed:           36 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *my_SSID:       Infra, 00:22:B0:BA:20:EF, Freq 2422 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.135
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1



```

cat network/interfaces:
```
# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback

```

/etc/NetworkManager/NetworkManager.conf:

```
[main]plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=00:23:8B:6E:FD:63,


[ifupdown]
managed=false



```

(I edited-out my real SSID in the pasted text, for privacy.)
(If you see ethernet disabled, it's because I lose my existing Wifi/internet connection when it's enabled, which would prevent me from writing these messages.)

---

### Post by varunendra on 2013-10-14
> **Ella_Bella said:**
> I would have to play with my router's admin panel to set my Wifi to use a manual IP address. I use a DHCP service for Wifi, so I don't know why you would ask me to do that? My problem is with interface preference surrounding Ethernet when a cable is detected.
Not in the router, I meant to assign a manual IP to the ethernet interface 'if required'. Objective was to assign it just IP and subnet, without gateway. Although the option you have enabled should have done this automatically even with the DHCP. Try enabling the other option too at the same place (**Ignore automatically obtained routes**).

> There is no problem with the BIOS because this machine has run Windows Vista, 7 and 8, and ALL have worked with wifi/internet while the ethernet port is used for other things since 2009 :) It's only ubuntu that starts ignoring Wifi and tries to use ethernet when it detects a cable plugged in after the fact, despite already having a live internet connection with Wifi.
Okay, so the BIOS 'feature' playing the 'bug' possibility is ruled out. It is not Ubuntu, but Network Manager which prefers ethernet over wifi (it is designed as such).

There seems nothing out of order in the output except this (although this shouldn't affect the behaviour under discussion) -
```
# interfaces(5) file used by ifup(8) and ifdown(8)**[COLOR="#FF0000"]auto lo[/COLOR]**
iface lo inet loopback

```
This should have been -
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```
A mistake during copy-paste? Anyway, it shouldn't affect the preference, but better to keep things properly than ignoring them. So if it is actually like what you posted, please correct the /etc/network/interfaces file to make it as shown above.

So there is nothing else I can suggest except trying the "Ignore automatically obtained routes" option, or, if it doesn't help (which would surprise me), try a manual IP without gateway for ethernet. Oh, and make sure the "IPv6" method is set to "Ignore" for both ethernet and wifi, so that it is completely out of picture.

Hope you won't need to try anything extraordinary though. :)

---

### Post by Ella_Bella on 2013-10-14
I'm willing to try advanced things if it helps. :)

I am always using a static IP for ethernet, because that's what I want. I'm connecting two computers, each with their own static IP set on their respective ethernet connections, which allows me to easily SAMBA with \\192.168.0.95\mountpoint . But enabling the ethernet connection causes ubuntu to abandon Wifi for internet, and try to get it through static IPs of the other connected computer, which won't work of course.

I checked /etc/network/interfaces and it was indeed a pasting error. Sorry about that! It looks like you say it should.

When I set the static IP on ethernet, I am using:
Address 192.168.0.96
Netmask 255.255.255.0
Gateway: nothing

That's how I've always set it up for Windows 8 and OS X, and it works. So I replicated that in Ubuntu. 

My "ignore auto obtained routes" checkbox is greyed out because I didn't duplicate the IP address settings above in the second panel "editing ipv4 routes for eth0". I only set them in the "editing eth0" panel. Should I be duplicating the settings and see if it enables the ghosted checkbox for auto routing?

---

### Post by Ella_Bella on 2013-10-14
I tried adding the IP addresses a second time in that third panel, but the "[COLOR=#000000]ignore auto obtained routes" checkbox remained greyed out. :([/COLOR]

---

### Post by varunendra on 2013-10-14
> **Ella_Bella said:**
> I tried adding the IP addresses a second time in that third panel, but the "[COLOR=#000000]ignore auto obtained routes" checkbox remained greyed out. :([/COLOR]

That's because you have selected the method to be "Manual" for eth0.

Since you are using a static IP anyway, and there was a bug in NM which didn't allow the manual IP configuration without defining a gateway, let's not use NM at all for eth0.

By default (due to "managed=false" option in NetworkManager.conf file), NM will ignore any interfaces that are mentioned in the /etc/network/interfaces file, and the interfaces file is what we are going to use to assign a no-fuss manual IP.

So please add the following lines to your **/etc/network/interfaces** file (you'll have to open it as root (gksu ...) if using the text editor) -
```
# Manual config for eth0
auto eth0
iface eth0 inet static
address 192.168.0.96
netmask 255.255.255.0
```
..below the existing lines in it, so that the file looks like -
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# Manual config for eth0
auto eth0
iface eth0 inet static
address 192.168.0.96
netmask 255.255.255.0
```

The commandline way to add this -
```
sudo su
echo -e "\n# Manual config for eth0\nauto eth0\niface eth0 inet static\naddress 192.168.0.96\nnetmask 255.255.255.0" >> /etc/network/interfaces
exit
```
[COLOR="#FF0000"]**EDIT:** Changed ">" to ">>" in above command, VERY IMPORTANT ![/COLOR]

Confirm if the lines were added correctly and the file looks exactly like mentioned above -
```
cat /etc/network/interfaces
```

Now restart both Network Manager and networking services -
```
sudo service network-manager restart
sudo service networking restart
```

This should be enough to bring your ethernet up without gateway, while keeping the wifi active via Network Manager. If not, you may additionally have to do -
```
sudo ifdown eth0
sudo ifup eth0
```
(maybe you should also set the "Method" for eth0 to "Automatic" in NM, it won't be effective anyway after adding the interface to the interfaces file).

---

### Post by Ella_Bella on 2013-10-14
Editing etc/network/interfaces with the text provided produced identical results. Once the network was restarted, ethernet came to life, and Wifi internet went away: the same as when I added ethernet using the GUI tools. So I had to revert the edit and reboot. Why reboot instead of restarting services? Because:

A new problem appeared with the command, "[COLOR=#000000][FONT=Ubuntu Mono]sudo service networking restart" In Ubuntu 13.04 64bit. This produced an Ubuntu internal system error (with popup dialog, core dump, etc. and submit button) that brought down gnome, unity, and only a forced restart with the laptop's power button could give me the ability to reboot/recover. I tried it again after rebooting, with same results. It's definitely repeatable.
[/FONT][/COLOR]
So I stopped fooling around with ethernet or further commands after that. :) I'd like to try something else if possible.

---

### Post by varunendra on 2013-10-15
> **Ella_Bella said:**
> Editing etc/network/interfaces with the text provided produced identical results.
Please try that again, reboot and post back the outputs of -
```
cat /etc/network/interfaces
ifconfig -a
rfkill list
nm-tool
route -n
cat /var/log/syslog | egrep -i 'network|wlan|ifup|interface'
lsmod
```
Oh, and please delete any existing 'Wired' connections in the Network Manager before rebooting.

> Why reboot instead of restarting services? Because:

A new problem appeared with the command, "sudo service networking restart" In Ubuntu 13.04 64bit. This produced an Ubuntu internal system error (with popup dialog, core dump, etc. and submit button) that brought down gnome, unity, and only a forced restart with the laptop's power button could give me the ability to reboot/recover. I tried it again after rebooting, with same results. **It's definitely repeatable**.
Definitely a bug then, the "Submit report" dialogue means something unusual happened. It works here and is supposed to work everywhere. At the risk of another system lockup, you may also try -
```
sudo /etc/init.d/networking restart
```
Which by the way, is a deprecated method to do the same thing, slightly differently (more simply). But if the problem is with any of the drivers, this one will fail too.

---

### Post by Ella_Bella on 2013-10-16
Ok, phew, this was all very difficult to do because as soon as I added ethernet to interfaces and rebooted, Wifi stopped getting the internet. I pulled out my iPad to be able to read this post and the requested commands. :) I then had to save the otuput of those commands to a text file, then copy it to a USB storage device, then reboot into Windows to get Wifi access back, and then post a reply to this post. 

Here are the outputs:

```
~ >cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


# Manual config for eth0
auto eth0
iface eth0 inet static
address 192.168.0.96
netmask 255.255.255.0


===
~ >ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:8b:6e:fd:63  
          inet addr:192.168.0.96  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe6e:fd63/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:360 (360.0 B)  TX bytes:14994 (14.9 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:134064 (134.0 KB)  TX bytes:134064 (134.0 KB)


wlan0     Link encap:Ethernet  HWaddr 00:21:6b:60:0f:8a  
          inet addr:192.168.0.135  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6bff:fe60:f8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17980 (17.9 KB)  TX bytes:11635 (11.6 KB)


===
~ >rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


===
~ >nm-tool


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unmanaged
  Default:           no
  HW Address:        00:23:8B:6E:FD:63


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on




- Device: wlan0  [SSID] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:21:6B:60:0F:8A


  Capabilities:
    Speed:           1 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *SSID:       Infra, 00:22:B0:BA:20:EF, Freq 2422 MHz, Rate 54 Mb/s, Strength 76 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.135
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


===
~ >route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0


===
~ >cat /var/log/syslog | egrep -i 'network|wlan|ifup|interface'


360 + lines of output that blows past my terminal window buffer. The last 10 lines are:


Oct 16 18:07:18 ariellalinuxmultipass NetworkManager[1004]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Oct 16 18:07:18 ariellalinuxmultipass NetworkManager[1004]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Oct 16 18:07:18 ariellalinuxmultipass NetworkManager[1004]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Oct 16 18:07:18 ariellalinuxmultipass NetworkManager[1004]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Oct 16 18:07:18 ariellalinuxmultipass NetworkManager[1004]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Oct 16 18:07:18 ariellalinuxmultipass NetworkManager[1004]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Oct 16 18:07:18 ariellalinuxmultipass NetworkManager[1004]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Oct 16 18:07:18 ariellalinuxmultipass NetworkManager[1004]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Oct 16 18:07:18 ariellalinuxmultipass NetworkManager[1004]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Oct 16 18:07:18 ariellalinuxmultipass NetworkManager[1004]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Oct 16 18:09:14 ariellalinuxmultipass wpa_supplicant[1050]: wlan0: WPA: Group rekeying completed with 00:22:b0:ba:20:ef [GTK=TKIP]
===


~ >lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     36906  1 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228808  10 bnep,rfcomm
ir_lirc_codec          12859  0 
lirc_dev               19166  1 ir_lirc_codec
joydev                 17377  0 
coretemp               13355  0 
snd_hda_codec_idt      70256  1 
gpio_ich               13476  0 
hp_wmi                 18048  0 
snd_hda_intel          39619  3 
snd_hda_codec         136498  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
sparse_keymap          13890  1 hp_wmi
ir_mce_kbd_decoder     12723  0 
ir_sanyo_decoder       12513  0 
ir_sony_decoder        12510  0 
ir_jvc_decoder         12507  0 
uvcvideo               80847  0 
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ir_rc6_decoder         12507  0 
ir_rc5_decoder         12507  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
ir_nec_decoder         12507  0 
videodev              129260  2 uvcvideo,videobuf2_core
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
rc_rc6_mce             12502  0 
arc4                   12615  2 
ene_ir                 18246  0 
rc_core                26426  11 ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,ene_ir,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder,rc_rc6_mce
snd_seq_midi           13324  0 
hp_accel               26012  0 
iwldvm                241872  0 
lis3lv02d              20111  1 hp_accel
mac80211              606457  1 iwldvm
input_polldev          13896  1 lis3lv02d
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mac_hid                13205  0 
nouveau               943184  3 
mxm_wmi                13021  1 nouveau
wmi                    19070  3 hp_wmi,mxm_wmi,nouveau
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
iwlwifi               173516  1 iwldvm
video                  19390  1 nouveau
ttm                    83187  1 nouveau
drm_kms_helper         49394  1 nouveau
jmb38x_ms              17416  0 
drm                   286028  5 ttm,drm_kms_helper,nouveau
psmouse                95905  0 
cfg80211              511019  3 iwlwifi,mac80211,iwldvm
serio_raw              13215  0 
microcode              22881  0 
memstick               16554  1 jmb38x_ms
lpc_ich                17061  0 
i2c_algo_bit           13413  1 nouveau
soundcore              12680  1 snd
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
firewire_ohci          40103  0 
ahci                   25731  2 
libahci                31364  1 ahci
sdhci_pci              18590  0 
firewire_core          64508  1 firewire_ohci
sdhci                  32522  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
r8169                  67466  0 







```

---

### Post by varunendra on 2013-10-17
Its day 5 since total power outage at my village (thanks to strong winds due to the cyclone that struck many hundred miles away) and I may not stay online for more than a couple of hours on this 'somehow resumed lead-acid battery power'. So did a quick search and here's a quick suggestion -

> **Ella_Bella said:**
> 
```

~ >route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
```
This looks a bit unusual to me, comparing with my own output here. Apparently, no route to the host is set. This should have been automatic but maybe the errors in the syslog have something to do with it. Please check the output of "route -n" when the internet (via wlan0) is working. Do you see a line like this -
```
192.168.0.1     0.0.0.0         255.255.255.255 UH    0      0        0 wlan0
``` ??

If yes, then revert to the current state, and try manually adding this same route with -
```
sudo route add 192.168.0.1 wlan0
```
Does the internet start working? If not, try restarting the Network Manager, either simply disable-enable in GUI, or -
```
sudo service network-manager restart
```
(assuming the crash occurs on restarting the "networking" service, not "network-manager")

Like I said, the above shouldn't be needed (should have been automatic) and I'm not sure if this would work at all. Even if does, maybe we are just curing the symptoms and not the cause.

As for those weird errors in syslog, I honestly have no idea. There is only one hint I could find on archlinux forums in my hasty search which suggests it may be a result of wpa_supplicant service not starting automatically..., and the speed "1 Mb/s" suggests this and the unexpected crash while restarting networking service may be related to the driver iwlwifi. I'll look into it when power resumes here and I don't have to hurry.

For now, please try disabling IPv6 completely following [post=12640479]this post[/post], and I Strongly recommend you change the encryption type in the router to **pure WPA2-PSK (AES)**. **No WPA/WPA2** mixed mode, **no TKIP**. This may be adding to the problem if not causing it. See [post=12817495]this post[/post] if you need convincing. :P

Oh, and maybe you should try disabling IPv6 and changing the encryption BEFORE the "route add" command. Maybe you won't need at all if this is indeed caused due to wpa_supplicant or the driver not liking TKIP.

Sorry if I made any mistakes in hurry, and **ANYONE having any ideas is please welcome to jump in !** :)

---

### Post by Ella_Bella on 2013-10-17
IT'S WORKING!

I was able to get things working by:

1-Removing changes we made to /etc/network/interfaces
2-Restoring the GUI eth0 entry and specifying the static IP along with "only use this connection with ressources" blah blah.
3-And using the last command you offered : [COLOR=#000000][FONT=Ubuntu Mono]sudo route add 192.168.0.1 wlan0

Now I am able to SMB files between the Ubuntu machine and the old Powermac G4, both with static IPs for their respective ethernet connections, and the Wifi internet connection of the Ubuntu machine is maintained with the ethernet cable connected, or not.

Yay!

Now, do I have to type "[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo route add 192.168.0.1 wlan0" with every reboot, or is that a permanent setting? If Ubuntu has to be told to do this with every boot, where do I go to add this? is there a *.d file, or line in a file, to create?

Thanks so much for the help![/FONT][/COLOR]

---

### Post by Ella_Bella on 2013-10-17
Here's the confusing thing:


NO ETHERNET CABLE/NETWORK (internet is accessible through wifi)
```

route -n
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```

ETHERNET NETWORK AND CABLE PLUGGED IN (internet is no longer accessible through wifi as ubuntu tries to grab it from ethernet)
```
route -n
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```

After I add the route for 192.168.0.1 and wlan0, and wifi resumes being the funnel for internet and ethernet stands happily alone for SMB file sharing between two machines across an ethernet cable :


```
route -n
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.0.1     0.0.0.0         255.255.255.255 UH    0      0        0 wlan0

```

I don't get why Wifi works fine as an internet source long as there is no ethernet cable plugged in without an entry for 192.168.0.1 as a destination, but once ethernet is in use, it needs to be added? Why does this solution work with adding, and not substitution? The use case is "ubuntu uses ethernet INSTEAD of wifi to source internet". And why does Wifi internet work with a destination of 0.0.0.0 and a gateway that is the router's IP, but then it needs to have 192.168.0.1 as a destination, and the gateway blanked out, when ethernet is in in use?


???


Either way, the problem is solved. I can SMB file share between Ubuntu on the HP laptop and the Powermac G4 flawlessly now. I just went to the file manager, added a server connection to smb://static_ip_of_powermac/sharepoint, provided login and password, and boom. Done.


The main difference I can see is that when an interface is in use for sourcing internet, its "Metric" gets set to 1000. The first output where wifi works fine shows it having a Metric of 1000. But in the second output, it's eth0 that takes the Metric value despite having different "destination" values. And then, even though eth0 keeps the Metric of 1000 in the last output, the additional wlan0 routing with a destination of 192.168.0.1, seems to make the Metric value unimportant?

---

### Post by Ella_Bella on 2013-10-17
Ok, the "sudo route add 192.168.0.1 wlan0" command needs to be issue with each boot or wifi loses internet access. I'll have to figure out where to put it.

---

### Post by Ella_Bella on 2013-10-17
I tried adding:

up route add 192.168.0.1 wlan0

to interfaces but that didn't work. Still learning. :)

---

### Post by Ella_Bella on 2013-10-17
Tried:

ip route add 192.168.0.1 wlan0

Saw this alternate prefix (ip vs up) on the web and tried it. Same result: no worky. I have to keep typing the command myself after a reboot.

---

### Post by Ella_Bella on 2013-10-17
Fixed it.

I added "route add 192.168.0.1 wlan0" to /etc/init.d/rc.local.

Thanks for all the help!

---

### Post by varunendra on 2013-10-17
I love writing explanation novels whenever I get an opportunity to :D

Before making the last post, my knowledge about the routing table was same as, or probably less than you. Most of what I'm going to explain is very nicely documented in the man page for the "route" command ("man route"), especially the "OUTPUT" part of it (but must read other parts as well to properly understand it).

**Some rules to keep in mind -**
[LIST]
[*]Any address whose netmask (or Genmask) is 255.255.255.255, is a host (one fixed machine). All others are "networks", not hosts.
[*]The number 255 in the netmask means that segment in the "address" can take no other value (so that number in the "address" is fixed and can't be anything else).
[*]The number 0 in the netmask means that segment in the "address" can take 'any' value from 0 to 255, and so it denotes a whole network segment, not a fixed machine.
[/LIST]


Applying above conventions, the "*Destination*" 0.0.0.0 for the gateway, with netmask 0.0.0.0 means that the "*address*" can be 'Anything' that can be possibly addressed by an IPv4 address (from 0.0.0.0 to 255.255.255.255), thus covering the whole Internet. So the destination is '*Whole Internet*' (of course the local addresses being a part of it).

Similarly, the "*Destination*" 192.168.0.0, with the netmask being 255.255.255.0 represents a whole network where only the last segment can be anything from 0 to 255, the rest being fixed. So this network can have addresses from 192.168.0.0 to 192.168.0.255 - denoting your whole network.

**Some conventions in the routing table -**
[LIST]
[*]The **Iface** in the routing table is the interface to which the packets taking that route will be sent.
[*]The **default gateway** (the one with both address and netmask being 0.0.0.0) is the 'fixed' address through which all packets will be gatewayed when taking that route.
[*]The **gateway must be reachable** first, means, a route to the gateway, or to the network on which the gateway resides, must exist for the packets to reach the gateway.
[/LIST]


**Now the answers to your questions -**

> **Ella_Bella said:**
> I don't get why Wifi works fine as an internet source long as there is no ethernet cable plugged in without an entry for 192.168.0.1 as a destination,
Because in that case, **[COLOR="#0000CD"]wlan0[/COLOR]** is* the only interface* through which the gateway 192.168.0.1 can be reached (it is a part of the "network" 192.168.0.0 for which a route is defined and that route uses the interface **[COLOR="#0000CD"]wlan0[/COLOR]**) -
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         **[COLOR="#006400"]192.168.0.1[/COLOR]**     0.0.0.0         UG    0      0        0 **[COLOR="#006400"]wlan0[/COLOR]**
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
[COLOR="#0000CD"]192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 **wlan0**[/COLOR]

```

> but once ethernet is in use, it needs to be added?
Because as soon as **[COLOR="#FF0000"]eth0[/COLOR]** enters the scene, we get two interfaces - **[COLOR="#0000CD"]wlan0[/COLOR]** and **[COLOR="#FF0000"]eth0[/COLOR]** - for the same route to reach the same network on which the gateway resides -
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         **[COLOR="#006400"]192.168.0.1[/COLOR]**     0.0.0.0         UG    0      0        0 **[COLOR="#006400"]wlan0[/COLOR]**
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
[COLOR="#FF0000"]192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 **eth0**[/COLOR]
[COLOR="#0000CD"]192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 **wlan0**[/COLOR]

```
So which one should the system pick? Taking simple logic - whichever comes first in the list. Now why eth0 gets the higher place - is something I haven't understood yet, so can't explain.

From now on, the packets are routed through **[COLOR="#FF0000"]eth0[/COLOR]** to reach the gateway, but the gateway is set to use the interface **[COLOR="#006400"]wlan0[/COLOR]** to route the packets back to the local network. Therefore the outgoing packets do reach the gateway, but either don't go anywhere from there, or the gateway can't route the reply packets back (you can't send from one interface and receive from another). Result - a blackhole.

> Why does this solution work with adding, and not substitution?
Adding a new route **specific to the gateway 192.168.0.1** (not the whole network), explicitly tells the system to use that route to reach the gateway. Since we set this route to use the interface **[COLOR="#006400"]wlan0[/COLOR]**, there is no confusion and problem is solved.
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         **[COLOR="#006400"]192.168.0.1[/COLOR]**     0.0.0.0         UG    0      0        0 **[COLOR="#006400"]wlan0[/COLOR]**
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
[COLOR="#FF0000"]192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 **eth0**[/COLOR]
[COLOR="#0000CD"]192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 **wlan0**[/COLOR]
[COLOR="#006400"]**192.168.0.1**     0.0.0.0         255.255.255.255 U**H**    0      0        0 **wlan0**[/COLOR]

```
We can also just 'delete' the duplicate route using eth0 interface instead of adding the one we are adding, but then you won't be able to reach any machines on your network **via eth0**, and wlan0 will be used for 'All' traffic.

One and only 'substitution' you can do is to delete the [COLOR="#0000CD"]second last route[/COLOR] in the above table (thus 'substituting' the network with a fixed address), since we are not using wlan0 to reach the 'whole' network, but just the gateway for which the last route is sufficient and essential in above scenario. The drawback of deleting it would be that you won't be able to 'talk' to other machines on the network IF ethernet is unplugged (currently, as soon as **[COLOR="#FF0000"]eth0[/COLOR]** exits the table, the same route becomes active via **[COLOR="#0000CD"]wlan0[/COLOR]**).

It is also notable that if we can somehow make the route using **[COLOR="#0000CD"]wlan0[/COLOR]** higher than **[COLOR="#FF0000"]eth0[/COLOR]**, even in that situation the system would start routing all packets destined to network 192.168.0.0 through wlan0, which I'm sure you don't want. :)

Now why the system isn't adding this route 'specific' to the gateway automatically is something currently beyond my understanding. As much as I have seen and understood, this should have been done automatically as soon as we eliminated the gateway from eth0 and assigned it to wlan0. Normally this route is added right after the gateway (thus no. 2 row from top).

This not happening automatically seems to me like a bug or a result of some other error in the system.

Speaking of errors, have you checked syslog again to see if those hundreds of NetworkManager errors are gone or not?

Oh, and forget about the Metric thing in the routing table, it is just a red herring. If the Network Manager errors still exist, maybe you should _start another thread to get that fixed_ (and probably your wireless speed too).

And this -
> **Ella_Bella said:**
> I added "route add 192.168.0.1 wlan0" to /etc/init.d/rc.local.
..is not really a fix, just a workaround which will work only when the wifi is active at startup. If it is disabled at booting time, you'll have to run the command manually when it comes back up. This thread should give you a better idea of where to add this command to actually associate it with wifi status (I haven't tested the suggestions myself though) : [http://ubuntuforums.org/showthread.php?t=2102559](http://ubuntuforums.org/showthread.php?t=2102559)

But if everything works as it should (no bugs, no errors), I believe you shouldn't need to manually or otherwise add that route yourself.

Anyway really glad that could help, and I learned some more basics too ! :P

---

### Post by Ella_Bella on 2013-10-18
That's such a wonderful explanation! Thank you for taking the time to write all this out and with nice formatting. It's very thoughtful and I think I might actually understand it now haha.  

I'll read that forum link and see if I can get a better solution in place this weekend.

---

