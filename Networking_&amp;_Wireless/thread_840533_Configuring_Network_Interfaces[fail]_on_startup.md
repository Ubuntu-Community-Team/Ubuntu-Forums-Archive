---
title: "Configuring Network Interfaces[fail] on startup"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by oBirdman on 2008-06-25
This morning I tried to upgrade the kernel to a newer version and got into big trouble with an Error 15. ([http://ubuntuforums.org/showthread.php?t=840256](http://ubuntuforums.org/showthread.php?t=840256)) With the great help of Frodon I got past the Error 15. However, I now ran into other problems:

After the Ubuntu Splash screen I get a few errors:

> 
Configuring network interfaces[FAIL]
Starting NFS common utilities [FAIL]
(...)
Starting NFS common utilities [FAIL]
Starting NFS kernel daemon (takes several minutes to load)


Before diving into the NFS errors, I was thinking of solving the network issues. Note that I have been using my Wireless USB (Conceptronic) for a few months without any problem. Even with the Error 15 and the Live CD I did not have any problem.

The output of /etc/network/interfaces:

> 
auto lo
iface lo net loopback



iface wlan0 inet static
address 192.168.24.175
netmask 255.255.255.0
gateway 192.168.24.80
wpa-ap-scan 1
wpa-pairwise TKIP
wpa-group TKIP
wpa-psk ***
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid NetOA

auto wlan0


Hope that anybody can help me with this issue.

---

### Post by oBirdman on 2008-06-25
Forgot to mention that I tried the following:

sudo /etc/init.d/networking restart

output:
> 
* Reconfiguring network interfaces...
ifdown: failed to open statefile /var/run/network/ifstate: No such file or directory
ifup: failed to open statefile /var/run/network/ifstate: No such file or directory
[fail]


then I did:

sudo mkdir /var/run/network
sudo touch /var/run/network/ifstate

output:
> 
* Reconfiguring network interfaces...
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Could not set interface 'wlan0' UP
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Failed to bring up 'wlan0'
[ OK ]


---

### Post by oBirdman on 2008-06-25
ok, in the past hours I have tried several things.

I have installed the driver now with nsdiswrapper and it does recognize the device. However, I still cannot get the wireless up and running.

The output of
sudo /etc/init.d/networking start

> 
 * Configuring network interfaces...                                            
wlan0: ERROR while getting interface flags: No such device
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
Failed to disable WPA in the driver.
ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
wlan0: ERROR while getting interface flags: No such device
Failed to bring up wlan0.


However, when I start up System-> Adminstration -> Network
the wireless is not listed anymore as it used to do.

The strangest thing is that if I start up the system with the Live CD, it automatically establishes the connection to the WLAN.

Hope somebody can help me a bit with this problem.

---

### Post by fetebaieti.com on 2009-06-24
[QUOTE=oBirdman;5260395]Forgot to mention that I tried the following:

Configuring network interfaces[FAIL]

* Reconfiguring network interfaces...
ifdown: failed to open statefile /var/run/network/ifstate: No such file or directory
ifup: failed to open statefile /var/run/network/ifstate: No such file or directory
[fail]

same problem... :( anyone can help?

---

