---
title: "Wifi on/off/on/off/on/off Constantly"
date: 2016-09-10
forum: Networking &amp; Wireless
---

### Post by markackerman8@gmail.com on 2016-09-10
Edit - WOOHOO - SOLVED.
THANK YOU!  and for others wanting to learn from this the script worked wonders, and you can see the cuplit and the fix in the last 2-4 posts ... awesome.:P :D :o

I can't find anyone else with this ... so here we go.

Edit.  Still trying to find the solution, and since this is cutting edge a solution may indeed 1000s or 1,000,000s od others.  WooHoo.
:D

[https://ubuntuforums.org/member.php?u=504316](https://ubuntuforums.org/member.php?u=504316) BuckyBall Thanks
has been helping me thanks thanks thanks, and look below for his link to a script to help all others with WiFI or Network issues, giving pages and pages of useful info. Awesome,

and see my results if you think you can help or are just curious
----------------------------------------------------------------------------------------------------------------------

It is an Intel 7260 AC Wireless Network Card, brand new cutting edge (apparently) laptop Hp Omen 15-5220.

I see many posts with others having issues with this model for 2 years, so I would think it should be ironed out.

I just re-installed yet again (for another reason) so don't have my notes.

Please ask me what to do and I will troubleshoot it with you.

Thanks mark 
p.s. the ethernet is fine so I just have to have the wifi turned off, for now.

---

### Post by uRock on 2016-09-10
Have you checked Additional Drivers to see if there are any drivers being offered for your card?

If yes, then please run the following in a terminal and paste the output here,```
lspci
```

---

### Post by Bucky Ball on 2016-09-10
Please give the output of

iwconfig

... preferably after a boot. Check if power management is on or off. Presuming you are using 16.04?

---

### Post by Keith_Helms on 2016-09-10
What did you mean by on/off/on/off?  Does the wifi disconnect and reconnect frequently?  Does it show connected the whole time, but traffic sometimes stops for minutes at a time?

I also have the 7260 card and it gives me trouble on certain networks such as the hotspot on my android tablet.

---

### Post by markackerman8@gmail.com on 2016-09-10
```
lspci
09:00.0 Network controller: Intel Corporation Wireless 7260 (rev c3)
```

with the wireless button off, not surprisingly ...
```
lo        no wireless extensions.
wlp9s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on  
enx0050b6ce8a68  no wireless extensions.
```

with wireless laptop button pressed and still regularly flashing on/off/on/off every second, and any network manager showing wifi on/off/on/off here is iwconfig is exactly the same

and going off and on every second gives the connection no time to be on
arghhhhh
thanks for your help guys - sorry for being late I was getting no email responses, that should be changed now

BUMP BUMP
here is some more info to at least show my dilligence
and I installed a bunch of seemingly appropriate drivers into /lib/firmware

```
sudo lshw -c network
&#8728;   *-network               
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlp9s0
       version: c3
       serial: 58:91:cf:7a:1c:96
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless

&#8728; configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-36-generic firmware=16.242414.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
&#8728; resources: irq:44 memory:b3400000-b3401fff
```

```
• lspci | grep -i wireless
• 09:00.0 Network controller: Intel Corporation Wireless 7260 (rev c3)
```

```
• $ dmesg | grep iwlwifi | grep firmware
&#8728; NOTHING!
```

```
• $ lsmod | grep iw
• iwlmvm                311296  0
• mac80211              737280  1 iwlmvm
• iwlwifi               200704  1 iwlmvm
• cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
```

```
• $ uname -a
&#8728; Linux Aarawn3 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Bucky Ball on 2016-09-10
Please start using code tags for your terminal output. See the link in my signature for how. Easier to read and neater. 

Try this.
```
cd /etc/pm/power.d

    sudo nano wireless
```

    This will open an empty file, copy the code below into it:

    ```
#!/bin/sh 
    /sbin/iwconfig wlan0 power off

```
    Save the file, remember to

    ```
sudo chmod +x wireless
```

    and restart. [From here]("http://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on"). 

Once you've booted up, run 'iwconfig' again and check to see if the 'power management = off'

Once again, you are using 16.04? Try and reply to all questions, please. :)

PS: There is no need to post 'bump' in threads when you are adding information at any time. Bumping will happen naturally then. Bumps are reserved for if you have no information and neither does anyone else after about 12 hours. (Reason I mention this is that excessive bumping attracts staff attention, in a bad way, and you don't unintentionally want to do that when you are only legitimately adding info. :))

---

### Post by markackerman8@gmail.com on 2016-09-11
Thanks for the reply and the tips.

To start I tried
```
ack@Aarawn3:~$ cd /etc/pm/power.d
bash: cd: /etc/pm/power.d: No such file or directory
```

So I took a leap of faith and googled powerd and thought you may be on to something so I installed it.  After installing and rebooting there was still no "/etc/pm/power.d" folder.

So I will stop for now as i may be doing more harm than good.

What would you suggest next?

Thanks, Mark
p.s.  It is about time I started using the "code" option ... 8 years later.  you taught an old dog a new trick.

From the link you gave me i tried 
```
ack@Aarawn3:~$ sudo iwconfig wlan0 power off
[sudo] password for ack: 
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; No such device.
```

hmmmm?

then I tried
```
ack@Aarawn3:~$ ls -1 /etc/modprobe.d/
alsa-base.conf
blacklist-ath_pci.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-rare-network.conf
blacklist-watchdog.conf
dkms.conf
fbdev-blacklist.conf
intel-microcode-blacklist.conf
iwlwifi.conf
mlx4.conf
nvidia-370_hybrid.conf
nvidia-graphics-drivers.conf
vmwgfx-fbdev.conf
```

and I see here intel-microcode and iwlwifi are ?Blacklisted?.  Perhaps we are on to something.  And Woohoo these code quotes are awesome.

Cheers, Mark

---

### Post by Bucky Ball on 2016-09-11
Replace 'wlan0' in all commands with the name of your wireless. Run

```
sudo lshw -C network
```

... and check the logical name value. Here's mine.

```
logical name: wlx40a5ef057cff
```

For instance, 

```
sudo iwconfig wlx40a5ef057cff power off
```

Try this then. Open file:

```
sudo nano /etc/rc.local
```

On the line prior to 'exit 0'.

```
sleep 10
iwconfig wlan1 power off
exit 0
```

... remembering to replace 'wlan1' with your the logical name of your wireless. Save file then reboot or run

```
sudo service network-manager restart
```

... should do it if you're using network manager. Check 'iwconfig' and make sure power management is off. If so, see how the wireless goes. If there's no change, please check the 'Wirelessinfo Script' link in my signature, run the script and post a link to, or the output, here and hopefully one of the resident gurus will spot it. I'm a mere minnow, but do know that the power management is an issue on some machines with some cards and with some Ubuntu releases and switching it off has solved the problem you're having on two of mine (and has worked for lots of other folk). Good luck. ;)

(Glad you like the [code] tags. The taskbar in 'Adv Reply' has some nice things, the paperclip icon for large attachments being one of my favourites.)

---

### Post by markackerman8@gmail.com on 2016-09-11
Wow, thanks.

That script is awesome.  Geniuses abound.  How can Windows survive when there are people like you around.  :P

[PHP]ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n########## wireless info START ##########\n\n"

########## wireless info START ##########

ack@Aarawn3:~$ REPORTDATE=$(date +"%d %b %Y %H:%M %Z %z")
ack@Aarawn3:~$ SCRIPTDATE=$(date -u -d "$SCRIPTDATE" +"%d %b %Y %H:%M %Z %z")
ack@Aarawn3:~$ LASTBOOTDT=$(last -FRn 1 reboot | sed -n 's/.*system boot[ ]\+\(.\+\) - .*$/\1/p')
ack@Aarawn3:~$ LASTBOOTDT=$(date -d "$LASTBOOTDT" +"%d %b %Y %H:%M %Z %z")
ack@Aarawn3:~$ printf "Report from: %s\n\n" "$REPORTDATE"
Report from: 11 Sep 2016 08:23 PDT -0700

ack@Aarawn3:~$ printf "Booted last: %s\n\n" "$LASTBOOTDT"
Booted last: 11 Sep 2016 00:00 PDT -0700

ack@Aarawn3:~$ printf "Script from: %s\n" "$SCRIPTDATE"
Script from: 08 Jul 2016 02:16 UTC +0000
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### release ###########################\n\n"

##### release ###########################

ack@Aarawn3:~$ lsb_release -idrc
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### kernel ############################\n\n"

##### kernel ############################

ack@Aarawn3:~$ uname -srvmpio
Linux 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
ack@Aarawn3:~$ echo

ack@Aarawn3:~$ sed 's/root=[^ ]*//;s/[ ]\+/, /g;s/^BOOT_IMAGE=[^ ]*/Parameters:/' /proc/cmdline
Parameters: ro, quiet, splash, vt.handoff=7
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### desktop ###########################\n\n"

##### desktop ###########################

ack@Aarawn3:~$ if [ -n "$DESKTOP_SESSION" ]; then
>     DESKTOP="$DESKTOP_SESSION"
> else
>     DESKTOP=$(sed -n 's/^Session=\(.\+\)$/\1/p' "$HOME/.dmrc")
>     DESKDMRC=" (from ~/.dmrc)"
> fi
ack@Aarawn3:~$ if [ -n "$DESKTOP" ]; then
>     if [ -f "/usr/share/xsessions/$DESKTOP.desktop" ]; then
> DESKTOP=$(sed -n 's/^Name=\(.\+\)$/\1/p' "/usr/share/xsessions/$DESKTOP.desktop")
>     fi
>     echo "${DESKTOP/ Session/}${DESKDMRC}"
> else
>     printf "\nCould not be determined.\n"
> fi
GNOME
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### lspci #############################\n\n"

##### lspci #############################

ack@Aarawn3:~$ lspci -nnk | grep -iA 2 '^[^[:space:]].*net' | sed '/^--$/d; /^[^[:space:]]/ i\\'

09:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev c3)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c070]
	Kernel driver in use: iwlwifi
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### lsusb #############################\n\n"

##### lsusb #############################

ack@Aarawn3:~$ lsusb
Bus 002 Device 002: ID 174c:55aa ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0b95:772a ASIX Electronics Corp. AX88772A Fast Ethernet
Bus 001 Device 003: ID 064e:9314 Suyin Corp. 
Bus 001 Device 002: ID 8087:07dc Intel Corp. 
Bus 001 Device 006: ID 04f3:2016 Elan Microelectronics Corp. 
Bus 001 Device 005: ID 045e:009d Microsoft Corp. Wireless Optical Desktop 3.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### PCMCIA card info ##################\n\n"

##### PCMCIA card info ##################

ack@Aarawn3:~$ if [ -x /sbin/pccardctl ]; then
>     pccardctl info
> else
>     echo "'pccardctl' is not installed (package \"pcmciautils\")."
> fi
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### rfkill ############################\n\n"

##### rfkill ############################

ack@Aarawn3:~$ rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### lsmod #############################\n\n"

##### lsmod #############################

ack@Aarawn3:~$ LSMOD=$(lsmod | egrep "(^|[[:punct:] ])($MODMATCHES|$LSMODMATCHES)[^[:punct:] ]*([[:punct:] ]|$)")
ack@Aarawn3:~$ echo "$LSMOD"
acer_wmi               20480  0
hp_wmi                 16384  0
sparse_keymap          16384  2 acer_wmi,hp_wmi
iwlmvm                311296  0
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
snd_soc_rt5640        114688  0
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
wmi                    20480  2 acer_wmi,hp_wmi
video                  40960  2 i915,acer_wmi
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### interfaces ########################\n\n"

##### interfaces ########################

ack@Aarawn3:~$ sed '/^#/d;s/^wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>/' /etc/network/interfaces
auto lo
iface lo inet loopback
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### ifconfig ##########################\n\n"

##### ifconfig ##########################

ack@Aarawn3:~$ IFCONFIG=$(ifconfig -a)
ack@Aarawn3:~$ sed '/^lo /,/^$/d' <<< "$IFCONFIG"
enx<IF from MAC [IF1]> Link encap:Ethernet  HWaddr <MAC 'enx<IF from MAC [IF1]>' [IF1]>  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2001:569:7508:9a00:571c:d72b:b939:9457/64 Scope:Global
          inet6 addr: 2001:569:7508:9a00:9b4e:7ecc:938a:f93d/64 Scope:Global
          inet6 addr: fe80::75f6:ed57:a84e:5831/64 Scope:Link
          inet6 addr: 2001:569:7508:9a00:9047:8f31:bdc6:2c9d/64 Scope:Global
          inet6 addr: 2001:569:7508:9a00:103d:1e8a:e74c:eda3/64 Scope:Global
          inet6 addr: 2001:569:7508:9a00:fc08:e04f:3bfb:b163/64 Scope:Global
          inet6 addr: 2001:569:7508:9a00:5e4:ee4a:aeb2:d17c/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1434 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:870539 (870.5 KB)  TX bytes:270174 (270.1 KB)

wlp9s0    Link encap:Ethernet  HWaddr <MAC 'wlp9s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
ack@Aarawn3:~$ IFACESETH=($(sed -n 's/^\([^ ]\+\)[ ]\+Link encap:Ethernet.*/\1/p' <<< "$IFCONFIG"))
ack@Aarawn3:~$ if (( ${#IFACESETH[@]} > 0 )); then
>     IFETHMATCHES=${IFACESETH[@]}
>     IFACEMATCHES="($IFACEMATCHES|(${IFETHMATCHES// /|}))"
> fi
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### iwconfig ##########################\n\n"

##### iwconfig ##########################

ack@Aarawn3:~$ iwconfig
lo        no wireless extensions.

enx<IF from MAC [IF1]>  no wireless extensions.

wlp9s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### route #############################\n\n"

##### route #############################

ack@Aarawn3:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 enx<IF from MAC [IF1]>
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enx<IF from MAC [IF1]>
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enx<IF from MAC [IF1]>
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### resolv.conf #######################\n\n"

##### resolv.conf #######################

ack@Aarawn3:~$ grep -v '^#' /etc/resolv.conf
nameserver 127.0.1.1
search telus
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### network managers ##################\n\n"

##### network managers ##################

ack@Aarawn3:~$ printf "Installed:\n\n"
Installed:

ack@Aarawn3:~$ for NETMGRNR in "${!NETMGRPATHS[@]}"; do
>     if [ -f "${NETMGRPATHS[$NETMGRNR]}" ]; then
> NETMGRINST+=("${NETMGRNAMES[$NETMGRNR]}")
>     fi
> done
ack@Aarawn3:~$ printf "\t%s\n" "${NETMGRINST[@]:-None found.}"
	NetworkManager
ack@Aarawn3:~$ NETMGRMATCHES=${NETMGRPATHS[@]/#*\//|}
ack@Aarawn3:~$ NETMGRMATCHES=${NETMGRMATCHES// |/|}
ack@Aarawn3:~$ NETMGRMATCHES="(${NETMGRMATCHES#|})"
ack@Aarawn3:~$ printf "\nRunning:\n\n"

Running:

ack@Aarawn3:~$ ps -ef | egrep "( |/)$NETMGRMATCHES($| )" || printf "\tNone found.\n"
root      5431     1  0 08:19 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### NetworkManager info ###############\n\n"

##### NetworkManager info ###############

ack@Aarawn3:~$ if [ -x /usr/bin/nm-tool ]; then
>     nm-tool
> elif [ -x /usr/bin/nmcli ]; then
>     nmcli -f all device show | sed '/^GENERAL.DEVICE:[ ]\+lo$/,/^$/d; /^AP\[[0-9]\+\]\./d'
>     echo
>     nmcli -f SSID,BSSID,MODE,CHAN,FREQ,RATE,SIGNAL,BARS,SECURITY,ACTIVE,IN-USE device wifi list
> else
>     echo "NetworkManager is not installed (package \"network-manager\")."
> fi
GENERAL.DEVICE:                         enx<IF from MAC [IF1]>
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         ASIX Elec. Corp.
GENERAL.PRODUCT:                        AX88x72A
GENERAL.DRIVER:                         asix
GENERAL.DRIVER-VERSION:                 22-Dec-2011
GENERAL.FIRMWARE-VERSION:               ASIX AX88772 USB 2.0 Ethernet
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/0
GENERAL.IP-IFACE:                       enx<IF from MAC [IF1]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     enx<IF from MAC [IF1]>
GENERAL.CON-UUID:                       d8aada88-1987-4336-93db-d2f45fd3d2f9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c22da78b-7735-456d-bee4-d219817dfe9e | Wired connection 1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   d8aada88-1987-4336-93db-d2f45fd3d2f9 | enx<IF from MAC [IF1]>
IP4.ADDRESS[1]:                         192.168.1.64/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
IP4.DNS[2]:                             75.153.171.122
IP4.DOMAIN[1]:                          telus
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1473693578
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.254
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.64
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = telus
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.254 75.153.171.122
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         2001:569:7508:9a00:103d:1e8a:e74c:eda3/64
IP6.ADDRESS[2]:                         2001:569:7508:9a00:9047:8f31:bdc6:2c9d/64
IP6.ADDRESS[3]:                         2001:569:7508:9a00:fc08:e04f:3bfb:b163/64
IP6.ADDRESS[4]:                         2001:569:7508:9a00:571c:d72b:b939:9457/64
IP6.ADDRESS[5]:                         2001:569:7508:9a00:5e4:ee4a:aeb2:d17c/64
IP6.ADDRESS[6]:                         2001:569:7508:9a00:9b4e:7ecc:938a:f93d/64
IP6.ADDRESS[7]:                         fe80::75f6:ed57:a84e:5831/64
IP6.GATEWAY:                            fe80::4e8b:30ff:fe24:7758
IP6.DNS[1]:                             2001:568:ff09:10a::53
IP6.DNS[2]:                             2001:568:ff09:10b::122
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:568:ff09:10a::53 2001:568:ff09:10b::122
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:<MAC address>
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:6b:38:73:8d:13:16:b9:b8:f6:bc:f3:51:c:c8:46:76

GENERAL.DEVICE:                         wlp9s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7260 (Dual Band Wireless-AC 7260)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-36-generic
GENERAL.FIRMWARE-VERSION:               16.242414.0
GENERAL.HWADDR:                         <MAC 'wlp9s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/wlp9s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### NetworkManager.state ##############\n\n"

##### NetworkManager.state ##############

ack@Aarawn3:~$ cat -s /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### NetworkManager.conf ###############\n\n"

##### NetworkManager.conf ###############

ack@Aarawn3:~$ grep -v '^#' /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false
ack@Aarawn3:~$ if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
>     printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\n\n"
>     grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
> fi
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### NetworkManager profiles ###########\n\n"

##### NetworkManager profiles ###########

ack@Aarawn3:~$ if [ -d /etc/NetworkManager/system-connections ]; then
>     if [ -n "$SUDO" ]; then
> trap "" 2 3
> NMPROFILES=$(find /etc/NetworkManager/system-connections -maxdepth 1 -type f -exec $SUDO${GKSUDO+ -D grep --}${KDESUDO+ -d --comment "<b>grep</b 
>$KDESUDOCMT" --} grep -vH '^$' {} +) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
> trap 2 3
> if [ "$SUDOSUCCESS" = "yes" ]; then
>     ORIGIFS="$IFS"
>     IFS=$'\n'
>     for NMWLPRFFILE in $(sed -n 's/^\(.\+\):type=\(802-11-wireless\|wifi\).*$/\1/p' <<< "$NMPROFILES"); do
> 
Display all 2545 possibilities? (y or n)
> MWLPRFFLPERMS=$(stat -c "%a %U" "$NMWLPRFFILE")
> 
Display all 2545 possibilities? (y or n)
> MWLPROFILE=($(sed -n "s;^$NMWLPRFFILE:\($NMPROFMATCHES.*\)$;\1 |;p" <<< "$NMPROFILES"))
> 
Display all 2545 possibilities? (y or n)
> MWLPROFSOUT+="[[$NMWLPRFFILE]] ($NMWLPRFFLPERMS)"$'\n'"${NMWLPROFILE[@]}"$'\n\n'
>     done
>     IFS="$ORIGIFS"
>     sed 's# | \[#\n\[#g;s#\] |#\]#g;s/ |$//' <<< "$NMWLPROFSOUT" | sed '/^\[[^]]*\]$/d'
> else
>     printf "\nAcquisition of admin privileges failed.\n"
> fi
>     else
> echo "No way to acquire admin privileges found."
>     fi
> else
>     echo "No NetworkManager profiles found."
> fi

ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### iw reg get ########################\n\n"

##### iw reg get ########################

ack@Aarawn3:~$ if [ -x /sbin/iw ]; then
>     if IWREGGET=$(iw reg get 2>&1) && [ -f /etc/timezone ]; then
> REGION=$(cat /etc/timezone)
> printf "Region: %s (based on set time zone)\n\n" "$REGION"
>     fi
>     echo "$IWREGGET"
> else
>     echo "'iw' is not installed (package \"iw\")."
> fi
Region: America/Vancouver (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### iwlist channels ###################\n\n"

##### iwlist channels ###################

ack@Aarawn3:~$ if [ -x /sbin/iwlist ]; then
>     iwlist chan
> else
>     echo "'iwlist' is not installed (package \"wireless-tools\")."
> fi
lo        no frequency information.

enx<IF from MAC [IF1]>  no frequency information.

wlp9s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### iwlist scan #######################\n\n"

##### iwlist scan #######################

ack@Aarawn3:~$ if [ -x /sbin/iwlist ]; then
>     if [ -n "$SUDO" ]; then
> trap "" 2 3
> IWLISTSCAN=$($SUDO${KDESUDO+ -d} iwlist scan) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
> trap 2 3
> if [ "$SUDOSUCCESS" = "yes" ]; then
>     if [[ $IWLISTSCAN = *Frequency:* ]]; then
> 
Display all 2545 possibilities? (y or n)
> tf "Channel occupancy:\n\n"
> 
Display all 2545 possibilities? (y or n)
:                                       hp-check                                printafm
!                                       hp-clean                                printcal
./                                      hp-colorcal                             printenv
[                                       hp-config_usb_printer                   printerbanner
[[                                      hp-doctor                               printer-profile
]]                                      hp-firmware                             printf
{                                       hp-info                                 printtarg
}                                       hp-levels                               prlimit
2to3                                    hp-logcapture                           profcheck
2to3-2.7                                hp-makeuri                              prove
2to3-3.5                                hp-pkservice                            prtstat
411toppm                                hp-plugin                               ps
7z                                      hp-plugin-ubuntu                        ps2ascii
7za                                     hp-probe                                ps2epsi
7zr                                     hp-query                                ps2pdf
a11y-profile-manager                    hp-scan                                 ps2pdf12
aa-enabled                              hp-setup                                ps2pdf13
aa-exec                                 hp-testpage                             ps2pdf14
aa-status                               hp-timedate                             ps2pdfwr
accept                                  hwclock                                 ps2ps
accessdb                                i386                                    ps2ps2
aconnect                                i686-linux-gnu-pkg-config               ps2txt
acpi_available                          ibus                                    psfaddtable
acpid                                   ibus-daemon                             psfgettable
acpi_listen                             ibus-setup                              psfstriptable
add-apt-repository                      ibus-table-createdb                     psfxtable
addgnupghome                            iccdump                                 psicc
addgroup                                iccgamut                                psidtopgm
addpart                                 icclu                                   pstopnm
--More--
[K
addr2line                               iceauth                                 pstree
add-shell                               ico                                     pstree.x11
adduser                                 icontopbm                               pstruct
agetty                                  iconv                                   ptar
alacarte                                iconvconfig                             ptardiff
alias                                   icotool                                 ptargrep
alsa                                    id                                      ptx
alsabat                                 identify                                pulseaudio
alsactl                                 identify-im6                            purple-remote
alsa-info.sh                            iecset                                  purple-send
alsaloop                                if                                      purple-send-async
alsamixer                               ifconfig                                purple-url-handler
alsatplg                                ifdown                                  pushd
alsaucm                                 ifquery                                 pwck
amidi                                   ifup                                    pwconv
amixer                                  igt_stats                               pwd
amuFormat.sh                            iio-sensor-proxy                        pwdx
anacron                                 ijs_pxljr                               pwunconv
animate                                 ilbmtoppm                               py3clean
animate-im6                             illumread                               py3compile
anytopnm                                imagetops                               py3versions
apg                                     im-config                               pybuild
apgbfm                                  imgtoppm                                pyclean
aplay                                   im-launch                               pycompile
aplaymidi                               import                                  pydoc
apm_available                           import-im6                              pydoc2.7
apparmor_parser                         in                                      pydoc3
apparmor_status                         info                                    pydoc3.5
applycal                                infobrowser                             pygettext
--More--
[K
> uency:' <<< "$IWLISTSCAN" | sort | uniq -c | sed 's/^[ ]\+\([ ][0-9]\+\)[ ]\+/     \1   APs on   /'
> 
.adobe/                       .dropbox-dist/                Pictures/                     .steampath
.bash_history                 .gconf/                       .pki/                         .steampid
.cache/                       .gnupg/                       .PlayOnLinux/                 .sudo_as_admin_successful
.config/                      .gvfs/                        PlayOnLinux's virtual drives/ Templates/
.dbus/                        .ICEauthority                 .profile                      .themes/
Desktop/                      .local/                       Public/                       Videos/
Documents/                    .macromedia/                  .pulse-cookie                 winetricks
Downloads/                    .mozilla/                     .ssh/                         wireless-info.txt
.dropbox/                     Music/                        .steam/                       
Dropbox/                      .nv/                          Steam/                        
> echo
>     fi
>     grep -v '^[ ]*IE: Unknown:' <<< "$IWLISTSCAN"
> else
>     printf "\nAcquisition of admin privileges failed.\n"
> fi
>     else
> echo "No way to acquire admin privileges found."
>     fi
> else
>     echo "'iwlist' is not installed (package \"wireless-tools\")."
> fi
> 
> printf "\n##### module infos ######################\n\n"
> MODULES=$(egrep -o "^$MODMATCHES[^ ]*" <<< "$LSMOD")
> for MODULE in $MODULES; do
>     MODINFO=$(modinfo $MODULE | egrep -v "^$MODINFOEXCL:")
>     printf "[%s]\n%s\n\n" "$MODULE" "$MODINFO"
> done
> 
> printf "\n##### module parameters #################\n\n"
> for MODULE in $MODULES; do
>     if [ -d /sys/module/$MODULE/parameters ]; then
> MODPARAMS=$(grep -H '^[[:graph:]]' /sys/module/$MODULE/parameters/* | sed 's#^.*/##;s/:/: /')
> printf "[%s]\n%s\n\n" "$MODULE" "$MODPARAMS"
>     fi
> done
> 
> printf "\n##### /etc/modules ######################\n\n"
> grep -v '^#' /etc/modules
> 
> printf "\n##### modprobe options ##################\n\n"
> for MODPROBEFILE in $(find /etc/modprobe.{conf,d} -name "*.conf" -regextype posix-egrep -not -regex ".*$MODPROBEXCL.*" 2> /dev/null | sort); do
>     MODPROBEOPTS=$(egrep -v '^(#|$)' $MODPROBEFILE)
bash: syntax error near unexpected token `('
ack@Aarawn3:~$     if [ -n "$MODPROBEOPTS" ]; then
> printf "[%s]\n%s\n\n" "$MODPROBEFILE" "$MODPROBEOPTS"
>     fi
ack@Aarawn3:~$ done
bash: syntax error near unexpected token `done'
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### rc.local ##########################\n\n"

##### rc.local ##########################

ack@Aarawn3:~$ grep -v '^#' /etc/rc.local

sleep 10
iwconfig wlp9s0 power off
exit 0

ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### pm-utils ##########################\n\n"

##### pm-utils ##########################

ack@Aarawn3:~$ for PMUTILSFILE in $(find /etc/pm/*.d \( -type f -o -type l \) -regextype posix-egrep -not -regex "$PMUTILSEXCL" | sort); do
>     PMUTFLCONT=$(egrep -v '^(#|$)' $PMUTILSFILE)
>     if [ -n "$PMUTFLCONT" ]; then
> PMUTFLPERMS=$(stat -c "%a %U" $PMUTILSFILE)
> printf "[%s] (%s)\n%s\n\n" "$PMUTILSFILE" "$PMUTFLPERMS" "$PMUTFLCONT"
>     fi
> done
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### udev rules ########################\n\n"

##### udev rules ########################

ack@Aarawn3:~$ for UDEVRLFILE in $(find /etc/udev/rules.d -name "*net*.rules" | sort); do
>     UDEVRULES=$(grep -B1 '^[^#]' $UDEVRLFILE | egrep -v '^(--)?$')
>     if [ -n "$UDEVRULES" ]; then
> printf "[%s]\n%s\n\n" "$UDEVRLFILE" "$UDEVRULES"
>     fi
> done
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n##### dmesg #############################\n\n"

##### dmesg #############################

ack@Aarawn3:~$ dmesg | tail -n 100 | egrep "[[:punct:] ]($MODMATCHES|$IFACEMATCHES|$DMESGMATCHES)[^[:punct:] ]*[[:punct:] ]" | egrep -v "$DMESGEXC 
L" | uniq -cf 2 | sed 's/^[ ]\+1[ ]\+//;s/^[ ]\+\([0-9]\+\)[ ]\+\(.\+\)$/\2 (repeated \1 times)/'
[  407.284885] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[  407.299898] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
[  409.071516] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  409.289441] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
[  411.070630] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  411.291161] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
[  413.069767] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  413.287017] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
[  415.070785] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  415.288874] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
[  417.070149] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  417.290927] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
[  419.068712] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  419.286857] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
[  421.068556] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  421.287011] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
[  423.070141] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  423.288157] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
[  425.069314] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  425.291464] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
[  427.068898] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  427.293246] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
[  429.068461] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  429.291223] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
[  431.068695] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  431.287739] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
[  433.071531] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  433.291672] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
[  435.068602] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  435.290060] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
[  437.067585] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  437.297728] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
[  439.067103] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  439.290536] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)
ack@Aarawn3:~$ 
ack@Aarawn3:~$ printf "\n########## wireless info END ############\n\n"

########## wireless info END ############

ack@Aarawn3:~$ 
ack@Aarawn3:~$ exec 2>&4 4>&-
[/PHP]

ANd this wrap text is AWESOME TOO

and another odd thing, that may shed some light is that ....

when I turn on bluetooth (presumably from Intels 7260AC s well) 2 things different happen:

1st/ Bluetooth does turn on (wifi still is off, and/or STOPS FLASHING AS OFF!)
2nd/ as just mention the Wifi is now off and is unable to turn on with the laptop button, and when i turn it on with Network Manager ....
      2b/ ..... it won't turn on at all OR only turns on for a split second then oddly shuts down totally (as in the on/off/on/off stops)

Curious at least.

---

### Post by jeremy31 on 2016-09-11
You have a stray module loaded ```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
reboot

---

### Post by markackerman8@gmail.com on 2016-09-11
Jeremy31,

You are a genius, SOLVED.
pray tell how did you ascertain this with such certainty ... AWESOME.  I will look thru the script response myself with new eyes. :) while i wait for a response, and post the answer for all to glory in!

Thanks

Edit.  Found it ... now it seems so obvious!
here it was
```
ack@Aarawn3:~$ rfkill list all
**0: acer-wireless: Wireless LAN**
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no 
```

NOW and Working!!
```
ack@Aarawn3:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

:D

---

### Post by jeremy31 on 2016-09-11
We have seen this many times before on HP computers

---

### Post by Bucky Ball on 2016-09-11
> **markackerman8@gmail.com said:**
> Jeremy31,
You are a genius

Na, just one of the resident wireless gurus I was talking about (but yea, it looks close to genius to me sometimes, too!). Thanks jeremy31. :)

The info from the wirelessinfo script did it. Well done posting it and thanks for marking as solved to help others. I advise you revert any changes you've made due to my instructions re. the power management. Looks like it may have been that stray module all along.

Enjoy. ;)

---

