---
title: "Get wireless working under Ubuntu Server 16.04"
date: 2016-05-25
forum: Networking &amp; Wireless
---

### Post by kcallis on 2016-05-25
I just installed Server 16.04 via CD. When I installed, the installation found my wireless adapter and I was able to connect to repositories to get the server installed. Once I rebooted, I see the iwldvm installed, but I am not use how to activate is from command line or connect using wpa_supplicant to connect. I can not use ethernet to connect, so I need to get wireless up and running. Any pointers would be appreciated!

Using Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)

---

### Post by chili555 on 2016-05-25
This is the general process: [http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552)

You will set it up by editing the mentioned file with nano:```
sudo nano /etc/network/interfaces
```As of Ubuntu 16.04, your wireless interface will not be wlan0; it will be something like wlp3s0 or some such. Find out by running:```
iwconfig
```Here is a sample from my machine:```
chili@T440p:~$ iwconfig
enp0s25   no wireless extensions.

lo        no wireless extensions.

[COLOR="#FF0000"]wlp3s0[/COLOR]    IEEE 802.11bgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: XX:2B:B0:DC:45:XX 
          Bit Rate=72.2 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:109   Missed beacon:0

```Whatever you find, substitute it in the example I gave in place of wlan0.

---

### Post by kcallis on 2016-05-29
I finally have wireless working, but I am still having a slight issue. Although I am able to get the interface to work, I am still getting error when it runs.

```
systemctl status wpa_supplicant@wlo1.service 
&#9679; wpa_supplicant@wlo1.service - WPA supplicant daemon (interface-specific version)
   Loaded: loaded (/lib/systemd/system/wpa_supplicant@.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2016-05-29 07:45:52 CDT; 1h 9min ago
 Main PID: 965 (code=exited, status=255)

May 29 07:45:52 kobayashi-maru wpa_supplicant[965]: ctrl_iface exists and seems to be in use - cannot override it
May 29 07:45:52 kobayashi-maru wpa_supplicant[965]: Delete '/var/run/wpa_supplicant/wlo1' manually if it is not used anymore
May 29 07:45:52 kobayashi-maru wpa_supplicant[965]: Failed to initialize control interface '/var/run/wpa_supplicant'.
May 29 07:45:52 kobayashi-maru wpa_supplicant[965]: You may have another wpa_supplicant process already running or the file was
May 29 07:45:52 kobayashi-maru wpa_supplicant[965]: left by an unclean termination of wpa_supplicant in which case you will need
May 29 07:45:52 kobayashi-maru wpa_supplicant[965]: to manually remove this file before starting wpa_supplicant again.
May 29 07:45:52 kobayashi-maru wpa_supplicant[965]: nl80211: deinit ifname=wlo1 disabled_11b_rates=0
May 29 07:45:52 kobayashi-maru systemd[1]: wpa_supplicant@wlo1.service: Main process exited, code=exited, status=255/n/a
May 29 07:45:52 kobayashi-maru systemd[1]: wpa_supplicant@wlo1.service: Unit entered failed state.
May 29 07:45:52 kobayashi-maru systemd[1]: wpa_supplicant@wlo1.service: Failed with result 'exit-code'

```

I have removed the .pid file and try to reload systemctl, but the same issue. 

My current /etc/wpa_supplicant looks like this:

```
# /etc/wpa_supplicant/wpa_supplicant-wlan1.conf

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=netdev
update_config=1
eapol_version=1
ap_scan=1
fast_reauth=1




network={
        ssid="NOT MY ESSID"
        #psk="NOT MY PASSKEY"
        psk=a20000000000000000000000
}

```

My interface works because I am only using it on one network, but I am ready to go out and be able to roam and I am sure that the wpa_supplicant is going to bring problems.

---

### Post by chili555 on 2016-05-29
>  I am ready to go out and be able to roam and I am sure that the wpa_supplicant is going to bring problems. With a server? If you are, instead, running a desktop machine, you are better off to let Network Manager do the work.

My example that I linked did not suggest a separate wpa_supplicant.conf file nor do I recommend it.

---

### Post by kcallis on 2016-05-29
> **chili555 said:**
> With a server? If you are, instead, running a desktop machine, you are better off to let Network Manager do the work.

My example that I linked did not suggest a separate wpa_supplicant.conf file nor do I recommend it.

There is a purpose to using a server deployment! Considering that I need to show the server in play at client location, there is a need to be able to have the wireless working. I need to get systemd-networkd working and more importantly getting wireless bridging working as well.

---

### Post by chili555 on 2016-05-29
> **kcallis said:**
> There is a purpose to using a server deployment! Considering that I need to show the server in play at client location, there is a need to be able to have the wireless working. I need to get systemd-networkd working and more importantly getting wireless bridging working as well.You can certainly scan and see the SSID. I assume the (prospective?) customer will need to give you the password. Then if you plug them in to /etc/network/interfaces, you should be all set.

Sorry, I am inexperienced with wireless bridging.

---

### Post by kcallis on 2016-05-29
> **chili555 said:**
> You can certainly scan and see the SSID. I assume the (prospective?) customer will need to give you the password. Then if you plug them in to /etc/network/interfaces, you should be all set.

Sorry, I am inexperienced with wireless bridging.

That is what I am doing right now, and I am sure that will work. I am still concerned about the wpa_supplicant error, but if I am able to so scan and connect to an AP,  I will be content.

---

### Post by kcallis on 2016-06-02
> **kcallis said:**
> That is what I am doing right now, and I am sure that will work. I am still concerned about the wpa_supplicant error, but if I am able to so scan and connect to an AP,  I will be content.

Today, I tried to access an open AP and was greet with crickets, but no access.


# /etc/wpa_supplicant/wpa_supplicant-wlan1.conf

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=netdev
update_config=1
eapol_version=1
ap_scan=1
fast_reauth=1




network={
        ssid="Library"
        key_mgmt=NONE
}

At least when I was using a PSK I was doing just fine. Now I am trying to use an open AP, and I can't connect using dhclient when I boot or even manually setting address and gateway. So what am I missing now? It almost makes it seem that it would be a lot easier to just install Desktop and boot to command line and play with KVM and the other to-do list.

---

### Post by chili555 on 2016-06-03
I wonder if wpa_supplicant.conf implies that you will be using WPA.

Did you try the easy way?```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid Library

```Followed by:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```

---

### Post by antonyj75 on 2017-02-02
This worked for me to configure WiFi in my Ubuntu 16.04 LTS server:

1. Install wpasupplicant if not already installed:
```
sudo apt install wpasupplicant
```

2. Find out your Wireless interface name using "iwconfig" command.
If it is not installed, install it using ```
sudo apt install wireless-tools
```
The interface name will be like wlp3s0 or wlp3s0b1 or something similar to this.

3. Add the Wireless interface configuration to */etc/network/interfaces*.
For example, taking *wlp3s0b1 *as Wireless interface name:

```
auto wlp3s0b1
iface wlp3s0b1 inet dhcp
        wpa-ssid <YOUR WIFI NETWORK NAME>
        wpa-psk <YOUR WIFI NETWORK PASSWORD>
```

4. Save */etc/network/interfaces* and run ```
sudo service networking restart
```.

For more detailed instructions, see [https://wiki.debian.org/WiFi/HowToUse#WPA-PSK_and_WPA2-PSK](https://wiki.debian.org/WiFi/HowToUse#WPA-PSK_and_WPA2-PSK)

---

### Post by pwwalker on 2017-03-18
> **antonyj75 said:**
> This worked for me to configure WiFi in my Ubuntu 16.04 LTS server:

1. Install wpasupplicant if not already installed:
```
sudo apt install wpasupplicant
```

2. Find out your Wireless interface name using "iwconfig" command.
If it is not installed, install it using ```
sudo apt install wireless-tools
```
The interface name will be like wlp3s0 or wlp3s0b1 or something similar to this.

3. Add the Wireless interface configuration to */etc/network/interfaces*.
For example, taking *wlp3s0b1 *as Wireless interface name:

```
auto wlp3s0b1
iface wlp3s0b1 inet dhcp
        wpa-ssid <YOUR WIFI NETWORK NAME>
        wpa-psk <YOUR WIFI NETWORK PASSWORD>
```

4. Save */etc/network/interfaces* and run ```
sudo service networking restart
```.

For more detailed instructions, see [https://wiki.debian.org/WiFi/HowToUse#WPA-PSK_and_WPA2-PSK](https://wiki.debian.org/WiFi/HowToUse#WPA-PSK_and_WPA2-PSK)

I've configured my files in the same way but hangs when I try to restart the service.  I just can't seem to get an IP.

---

### Post by chili555 on 2017-03-18
> **pwwalker said:**
> I've configured my files in the same way but hangs when I try to restart the service.  I just can't seem to get an IP.Restarting networking is deprecated; i.e. no longer useful. The correct method is:```
sudo ifdown wlp3s0 && sudo ifup -v wlp3s0
```Of course, substitute your interface name you found with:```
ifconfig
```I wouldn't use DHCP if I wanted to easily ssh and ftp into my server, but, hey, that's just me. I usually take the fast, easy, fool-proof way if I can.

---

