---
title: "University WLAN  PEAP configuration help"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by dsmits on 2006-11-10
Hi everybody,

Ok I'm a bit of a newbie here and if I really want to make my switch to Ubuntu worthwhile I need to setup WLAN for my university, fortunatly my UNI is semi-Linux friendly and was willing to give me the code to paste in my config file:

Below is the script that needs to be placed into your config file.

network=
{
       ssid="ODU"
       key_mgmt=IEEE8021X
       eap=PEAP         
       phase1="peaplabel=0"
       phase2="auth=MSCHAPV2"
       identity="enter your username"
       password="enter your passs"
      }

The only problem is I don't know what file this script needs to be pasted in, if anyone could help me it would be a major help. Also, if there are any Ubuntu Gurus out there, Ubuntu forums could really use a nice HOWTO for configuring EAP/PEAP.

One last tid bit of information, I'm using Kubuntu Dapper Drake 6.06 LTS

Thanks, 
Dan Smits

---

### Post by towel on 2006-12-11
Dan did you ever find out where it goes?

My school uses those exact same settings for its wlan or very close to them.

I'm still trying to get my wifi working :(

---

### Post by dsmits on 2006-12-11
Towel,

This is the tutorial I used susbstituting my settings with.
Hope this helps.

[http://www.ubuntuforums.org/showthread.php?t=249654]("http://www.ubuntuforums.org/showthread.php?t=249654")

Regards,
Dan:cool:

---

### Post by FrodoB on 2006-12-11
Folks, I have never used PEAP, but I have used wpasupplicant to do WPA-PSK and I believe the configuration is about the same.  

On Edgy or Dapper the instructions are about like this if you already have a working wireless device.

So based upon the code that dsmits was supplied I think it must be about like the following:

1) Install wpasupplicant:

$ sudo apt-get update

$ sudo apt-get install wpasupplicant


2) Create a /etc/wpa_supplicant.conf file that contains the following: 

$ sudo gedit /etc/wpa_supplicant.conf

===================== cut ==========================================================
ctrl_interface=/var/run/wpa_supplicant

# You may or may not need the next line, remove the "#" to uncomment
# ap_scan=1    # 1 for broadcast SSID and 2 for hidden SSID

network=
{
  ssid="ODU"
  key_mgmt=IEEE8021X
  eap=PEAP
  phase1="peaplabel=0"
  phase2="auth=MSCHAPV2"
  identity="enter your username"
  password="enter your password"
}

===================== cut ==========================================================

Enter your actual username and password into the /etc/wpa_supplicant.conf

Save the file and exit.


3) Edit the /etc/network/interfaces file and add a record for your wireless device:

$ sudo gedit /etc/network/interfaces

Add a record similar to this one, replacing wlan0 with the actual name of your interface.

===================== cut ==========================================================
auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
wpa-ssid Your_SSID_Name
post-down killall -q wpa_supplicant

===================== cut ==========================================================

Note that -Dwext is the driver that your device is using, please refer to the wpasupplicant 
documentation for additional device driver information. The wext driver is good for
ndiswrapper and the Atheros devices at least.

Note that you need to change the interface, -i, to your wireless device name such as wlan0 or ath0, etc.

4) Reboot your system or use the following command:

sudo /etc/init.d/dbus restart

A complete system reboot can be helpful, so I recommend that.

---

