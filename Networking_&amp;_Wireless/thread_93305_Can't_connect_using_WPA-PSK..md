---
title: "Can't connect using WPA-PSK."
date: 2005-11-21
forum: Networking &amp; Wireless
---

### Post by jvdebian on 2005-11-21
hey guys,

well I've been quite a while trying to set up my wireless network, everybody at home uses windows and the security is set to WPA-PSK I've tried to install wpa_supplicant but it didn't get trought. have a look...

junior@booya:~$ wpa_supplicant -i eth1 -c /etc/wpa_supplicant.conf -D madwifi
ENGINE: ctrl cmd_string failed: LOAD (null) [error:25066067:DSO support routines:DLFCN_LOAD:could not load the shared library]
SSL: Failed to initialize TLS context.
Failed to initialize EAPOL state machines.

I just followed the ubuntu-wiki and just added those lines at the end of the wpa_supplicant.conf

# Example blocks:

# Simple case: WPA-PSK, PSK as an ASCII passphrase, allow all valid ciphers
network={
     ssid="2WIRE260"
     proto=WPA
     key_mgmt=WPA-PSK          psk=1227ecdf26f2d0315aa091308e0d34b547ea7d1673c7136783eb60158121d3ef
}

#end of the wpa_supplicant.conf

and also, when I run 

junior@ubuntu:~$ iwconfig 

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0

sit0      no wireless extensions.


It catches the unsecure network that is in the range...

so if anyone has any idea... go for it!!!

cheeers!!!!

---

### Post by jvdebian on 2005-11-21
have a look at this now!!!

junior@ubuntu:~$ wpa_supplicant -Bdd -i eth1 -c /etc/wpa_supplicant.conf -D ipw
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=8):
     32 57 49 52 45 32 36 30                           2WIRE260
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
group: 0x8
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='2WIRE260'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
ioctl[SIOCSIWPMKSA]: Operation not permitted
ioctl[SIOCSIWMODE]: Operation not permitted
Could not configure driver to use managed mode
SIOCSIFFLAGS: Permission denied
Could not set interface 'eth1' UP
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
socket(PF_PACKET): Operation not permitted
wpa_driver_ipw_set_wpa: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not permitted
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not permitted
wpa_driver_ipw_set_drop_unencrypted: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not permitted
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not permitted
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not permitted
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not permitted
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not permitted
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not permitted
Failed to set encryption.
ioctl[SIOCSIWAP]: Operation not permitted
SIOCSIFFLAGS: Permission denied



never give up!!! cheers again!!

---

### Post by firecat53 on 2005-11-22
Here's my /etc/network/interfaces, wpa_supplicant.conf and /etc/default/wpasupplicant.  I've got a perfectly working wpa connection that comes up on boot. Just make sure and change the driver type, wpa_supplicant path, and interface name in the wpa_supplicant command.  By the way, it looks like one of your issues was not running wpa_supplicant as root! (sudo wpa_supplicant -wB ....)

```
# /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp

#auto eth0

auto ath0
iface ath0 inet static
address 192.168.0.110
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid athome
pre-up /usr/local/sbin/wpa_supplicant -wB -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
post-down killall -p wpa_supplicant

# /etc/wpa_supplicant.conf
network={
   ssid="firecat4153"
   #psk="mypassphrase"
   psk=34150987asdfasdfjkh3407etcetcetc
   key_mgmt=WPA-PSK
   proto=WPA
}


# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>          Wireless drive, typically optional.
#  -i <ifname>          Interface
#  -c <config file>     Configuration file
#  -d                   Debugging (-dd for more)
#  -w                   Wait for interface to come up

# See the manual page wpa_supplicant(1) for more options and information.

OPTIONS="-w"

# EXAMPLES:

# OPTIONS="-i wlan0 -D hostap -c /etc/wpa_supplicant.conf"
# OPTIONS="-i ath0 -D madwifi -c /etc/wpa_supplicant.conf"
```

Good luck!

Scott

---

