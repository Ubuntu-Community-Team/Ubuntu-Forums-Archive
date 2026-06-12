---
title: "Help with compaq wireless w200 in lubuntu"
date: 2015-06-07
forum: Networking &amp; Wireless
---

### Post by TheAzther on 2015-06-07
-Hello, i have a little problem with lubuntu 14.04.2 and is that i cannot use the wifi, i just cant turn the wifi on, lsusb say this:
> theazther@TheAzther-Evo-N610c:~$ lsusb
Bus 001 Device 008: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 049f:0076 Compaq Computer Corp. Wireless LAN MultiPort W200
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
i tried using the orinoco usb driver but doesn´t work (i dont know if im doing something wrong, i follow this tutorial [https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200) but doesn´t work for me), and also when i try to use the windows driver on ndsiwrapper the computer freeze, please help (im using a usb wifi adapter right now)

---

### Post by chili555 on 2015-06-08
I'm confused. Are you trying to get the internal device, an Orinoco perhaps, working, or the USB. You provided details of only the USB and then said:> (im using a usb wifi adapter right now) If you want to get an internal device working, let's see:```
lspci -nn | grep 0280
```Thanks.

---

### Post by TheAzther on 2015-06-08
-Sorry if i explained wrong, right now im using a wifi stick connected via usb, its the > Bus 001 Device 008: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573Wireless Adapter.
-i just cant use the Wireless LAN MultiPort W200, my laptop its a compaq evo N610c and i followed the tutorial i said and this thread that you answered but doens´t work too: [http://ubuntuforums.org/showthread.php?t=1932398](http://ubuntuforums.org/showthread.php?t=1932398) i do everithing you say there but the module dont start

---

### Post by TheAzther on 2015-06-08
i want to make the w200 work

---

### Post by chili555 on 2015-06-08
Where did the instructions in the other link go wrong? Were you able to install the firmware? When you loaded the module orinoco_usb, was a wireless interface, either wlan0 or eth1, created? Can you click the Network Manager icon and see networks? What happens when you try to connect to yours? Is there any clue in the log?```
sudo modprobe orinoco_usb
dmesg | grep -e ndis -e orinoco
```

"...doesn´t work for me..." doesn't tell us much.

I'm sorry for my previous mistake.

---

### Post by TheAzther on 2015-06-08
-I follow you´r steps that you say in the other thread but when i reboot nothing happens, the network manager dont appears and when i press Fn+f2 nothing happens, but a interesting thing is sometimes in lsusb only appears this:
> Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 but if i press Fn+F2 the compaq lan w200 appears again in lsusb.
And also in the help ubuntu tutorial when i try to download all the packages it says with this code: > sudo apt-get install build-essential subversion linux-headers-`uname -r` gcc-3.4-base cpp-3.4 curl the terminal say some packages cant be found. im sorry for my bad explaining its just my english is not much good and im only 13 years old

---

### Post by chili555 on 2015-06-08
Please don't worry about your English. I will try harder to understand and help you. I promise.

Let's try to get your device working with the driver already in Ubuntu without downloading other things. First, load the module from the terminal:```
sudo modprobe orinoco_usb
```Are there any errors or warnings? If so, post them and we'll see if we can solve the errors. Check if a wireless interface is created:```
iwconfig
```If not, see if there are any errors in the log:```
dmesg | grep orinoco
```The pipe symbol | is on the right side of my keyboard on the same key with \.

Thanks.

---

### Post by TheAzther on 2015-06-09
sudo modprobe orinoco_usb dont show anything, iwconfig show this:
> theazther@TheAzther-Evo-N610c:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions and dmesg \ grep orinoco show this:
> theazther@TheAzther-Evo-N610c:~$ dmesg \ grep orinoco

Usage:
 dmesg [opciones]

Opciones:
 -C, --clear                 clear the kernel ring buffer
 -c, --read-clear            read and clear all messages
 -D, --console-off           disable printing messages to console
 -d, --show-delta            show time delta between printed messages
 -E, --console-on            enable printing messages to console
 -f, --facility <list>       restrict output to defined facilities
 -h, --help                  display this help and exit
 -k, --kernel                display kernel messages
 -l, --level <list>          restrict output to defined levels
 -n, --console-level <level> set level of messages printed to console
 -r, --raw                   print the raw message buffer
 -s, --buffer-size <size>    buffer size to query the kernel ring buffer
 -T, --ctime                 show human readable timestamp (could be 
                             inaccurate if you have used SUSPEND/RESUME)
 -t, --notime                don't print messages timestamp
 -u, --userspace             display userspace messages
 -V, --version               output version information and exit
 -x, --decode                decode facility and level to readable string

Supported log facilities:
    kern - mensajes del núcleo
    user - random user-level messages
    mail - sistema de correo
  daemon - system daemons
    auth - security/authorization messages
  syslog - mensajes generados internamente por syslogd
     lpr - line printer subsystem
    news - network news subsystem

Supported log levels (priorities):
   emerg - system is unusable
   alert - se debe tomar una acción inmediatamente
    crit - condiciones críticas
     err - condiciones de error
    warn - condiciones de advertencia
  notice - normal but significant condition
    info - informational
   debug - debug-level messages


---

### Post by chili555 on 2015-06-09
It is not:> dmesg \ grep orinocoThat is the backslash.

Instead, it is:```
dmesg | grep orinoco
```That is the pipe symbol.

On my US keyboard, over on the right, it this key: [http://njgeo.org/wp-content/uploads/2015/01/IMG_0033-300x300.jpg](http://njgeo.org/wp-content/uploads/2015/01/IMG_0033-300x300.jpg) The lower-case is \. We need the upper-case; that is, Shift+\.

---

### Post by TheAzther on 2015-06-09
dmesg | grep orinoco dont show anything but when i pressed Fn+F2 and i tried again, the terminal showed this:
> theazther@TheAzther-Evo-N610c:~$ dmesg | grep orinoco
[  467.292736] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[  467.662186] orinoco_usb: probe of 2-3:1.0 failed with error -14
[  467.669299] usbcore: registered new interface driver orinoco_usb


---

### Post by chili555 on 2015-06-09
>  orinoco_usb: probe of 2-3:1.0 failed with error -14I'm not sure what that means but let's try to find out. Is ndiswrapper loaded?```
lsmod | grep -e orinoco -e ndis
```Is the required firmware installed?```
ls /lib/firmware | grep orinoco
```We hope you have orinoco_ezusb_fw. If not, please repeat the steps at post #6 here: [http://ubuntuforums.org/showthread.php?t=1932398](http://ubuntuforums.org/showthread.php?t=1932398)

Then reboot.

---

### Post by TheAzther on 2015-06-09
lsmod | grep -e orinoco -e ndis show this:
> theazther@TheAzther-Evo-N610c:~$ lsmod | grep -e orinoco -e ndis
orinoco_usb            26398  0 
orinoco                70872  1 orinoco_usb
cfg80211              409394  3 mac80211,rt2x00lib,orinoco
 right now i dont have installed ndiswrapper, and  ls /lib/firmware | grep orinoco showed this:
> orinoco_ezusb_fw
 i did that steps that you say, i say that in one of my first replies, i do everything but when i reboot nothing happens, the network manager don´t appear and i cant turn the module on.

---

### Post by chili555 on 2015-06-10
> orinoco_usb 26398 0 
orinoco 70872 1 orinoco_usb
cfg80211 409394 3 mac80211,[COLOR="#FF0000"]rt2x00lib[/COLOR],orinocoI notice that the driver for the USB is loaded. I'd like to see what happens if you boot up without the USB inserted. Please remove it. Run the following in the terminal:```
sudo -i
echo orinoco_usb  >>  /etc/modules
exit
```Reboot. Now, with the USB still removed, run:```
dmesg | grep -e orinoco -e wlan  >  wifi.txt
cat /etc/udev/rules.d/70-persistent-net.rules  >>  wifi.txt
```Insert the USB wireless, find the file wifi.txt in your user directory and post it in your reply.

---

### Post by TheAzther on 2015-06-10
wifi.txt say this:
> # PCI device 0x8086:0x1038 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:02:a5:bf:03:cb", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rt73usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:27:19:bc:74:37", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


---

### Post by chili555 on 2015-06-10
And there was nothing here?```
dmesg | grep -e orinoco -e wlan
```:confused:

---

### Post by TheAzther on 2015-06-10
nothing, it show a wrong message:
> dmesg: opción incorrecta (incorrect option)-- «e»

Usage:
 dmesg [opciones]

Opciones:
 -C, --clear                 clear the kernel ring buffer
 -c, --read-clear            read and clear all messages
 -D, --console-off           disable printing messages to console
 -d, --show-delta            show time delta between printed messages
 -E, --console-on            enable printing messages to console
 -f, --facility <list>       restrict output to defined facilities
 -h, --help                  display this help and exit
 -k, --kernel                display kernel messages
 -l, --level <list>          restrict output to defined levels
 -n, --console-level <level> set level of messages printed to console
 -r, --raw                   print the raw message buffer
 -s, --buffer-size <size>    buffer size to query the kernel ring buffer
 -T, --ctime                 show human readable timestamp (could be 
                             inaccurate if you have used SUSPEND/RESUME)
 -t, --notime                don't print messages timestamp
 -u, --userspace             display userspace messages
 -V, --version               output version information and exit
 -x, --decode                decode facility and level to readable string

Supported log facilities:
    kern - mensajes del núcleo
    user - random user-level messages
    mail - sistema de correo
  daemon - system daemons
    auth - security/authorization messages
  syslog - mensajes generados internamente por syslogd
     lpr - line printer subsystem
    news - network news subsystem

Supported log levels (priorities):
   emerg - system is unusable
   alert - se debe tomar una acción inmediatamente
    crit - condiciones críticas
     err - condiciones de error
    warn - condiciones de advertencia
  notice - normal but significant condition
    info - informational
   debug - debug-level messages


---

### Post by chili555 on 2015-06-10
Did you carefully paste the entire, exact command into the terminal?```
dmesg | grep -e orinoco -e wlan
```It works on my system.

---

### Post by TheAzther on 2015-06-10
-Now show this:
> theazther@TheAzther-Evo-N610c:~$ dmesg | grep -e orinoco -e wlan
[   23.805477] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   23.908453] usbcore: registered new interface driver orinoco_usb
[  219.369575] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  219.370362] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  222.031783] wlan0: authenticate with 00:26:5a:ad:9e:1e
[  222.049150] wlan0: send auth to 00:26:5a:ad:9e:1e (try 1/3)
[  222.077300] wlan0: authenticated
[  222.080476] wlan0: associate with 00:26:5a:ad:9e:1e (try 1/3)
[  222.092148] wlan0: RX AssocResp from 00:26:5a:ad:9e:1e (capab=0xc21 status=0 aid=6)
[  222.104009] wlan0: associated
[  222.104175] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2773.139555] wlan0: deauthenticating from 00:26:5a:ad:9e:1e by local choice (reason=3)
[ 2786.012194] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2787.505505] wlan0: authenticate with 00:1d:0f:fa:9e:22
[ 2787.539194] wlan0: send auth to 00:1d:0f:fa:9e:22 (try 1/3)
[ 2787.541290] wlan0: authenticated
[ 2787.541938] rt73usb 1-3:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2787.541948] rt73usb 1-3:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2787.544387] wlan0: associate with 00:1d:0f:fa:9e:22 (try 1/3)
[ 2787.549641] wlan0: RX AssocResp from 00:1d:0f:fa:9e:22 (capab=0x421 status=0 aid=10)
[ 2787.560581] wlan0: associated
[ 2787.560674] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2815.325529] wlan0: deauthenticating from 00:1d:0f:fa:9e:22 by local choice (reason=3)
[ 2855.064238] wlan0: authenticate with 00:26:5a:ad:9e:1e
[ 2855.098708] wlan0: send auth to 00:26:5a:ad:9e:1e (try 1/3)
[ 2855.124508] wlan0: authenticated
[ 2855.128118] wlan0: associate with 00:26:5a:ad:9e:1e (try 1/3)
[ 2855.137519] wlan0: RX AssocResp from 00:26:5a:ad:9e:1e (capab=0xc21 status=0 aid=6)
[ 2855.148945] wlan0: associated
[ 3159.768204] wlan0: deauthenticating from 00:26:5a:ad:9e:1e by local choice (reason=3)


---

### Post by TheAzther on 2015-06-11
-Do you know what, im going to try to re-install lubuntu and follow your instructions to install the driver in that thread  but using ethernet and no the realtek wifi usb

---

### Post by chili555 on 2015-06-12
> **TheAzther said:**
> -Do you know what, im going to try to re-install lubuntu and follow your instructions to install the driver in that thread  but using ethernet and no the realtek wifi usbI suggest you install the latest version, that is, Ubuntu 15.04, to get the best chance.

Frankly, this makes me suspect that the device and the driver are not going to work at all:> orinoco_usb: probe of 2-3:1.0 failed with error -14I hope I'm wrong. Good luck.

---

### Post by TheAzther on 2015-06-13
It dind´t worker, i did all the steps but nothing happened, but i have a question, this only install the firmware right?, but dind´t need a driver too?, according [this]("https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200") tutorial first i need install the driver and patch it, after that,, i have to install the driver, im downloading everything to see whath happens, and also, have installed windows xp with dual boot inflict on the driver?

---

### Post by TheAzther on 2015-06-13
Agh!, it dind't worked... this is annyoing me!

---

### Post by chili555 on 2015-06-13
The driver is included by default; confirm:```
modinfo orinoco_usb
```And confirm that the version you installed covers your device:>  ID[COLOR="#FF0000"] 049f:0076[/COLOR] Compaq Computer Corp. Wireless LAN MultiPort W200```
modinfo orinoco_usb | grep 0076
```On my machine, it returns:```
alias:          usb:v[COLOR="#FF0000"]049F[/COLOR]p[COLOR="#FF0000"]0076[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
```However, all this won't fix an old, poorly supported driver that covers an old and, by now, rare device. Most of these old Compacs are dead and gone by now.

Although the driver is included by default, the firmware is not. That's why you needed to install it after installation.

When you load the driver:```
sudo modprobe orinoco_usb
```...are there any helpful messages in the log?```
dmesg | grep orinoco
```

---

### Post by TheAzther on 2015-06-13
-Well... it show this:
> theazther@theazther-Evo-N610c:~$ dmesg | grep orinoco
[   17.170974] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   17.753906] orinoco_usb: probe of 2-3:1.0 failed with error -14
[   17.753974] usbcore: registered new interface driver orinoco_usb
theazther@theazther-Evo-N610c:~$ 
]

---

### Post by TheAzther on 2015-07-01
ts been a while that i do not answer about it in the tread, nut today i turned on my laptop and when i enter in lubuntu, before show the logo, it showed those lines in yellow:
> [COLOR=#000000][I][ 19.393002] orinoco_usb: Invalid firmware variant offset: 0x22bb
[ 19.393017] orinoco_usb: Firmware download failed. error -22
[/I][/COLOR]

---

### Post by chili555 on 2015-07-01
According to *modinfo*, the driver needs *orinoco_ezusb_fw*.```
$ modinfo orinoco_usb
filename:       /lib/modules/4.0.1-040001-generic/kernel/drivers/net/wireless/orinoco/orinoco_usb.ko
license:        Dual MPL/GPL
description:    Driver for Orinoco wireless LAN cards using EZUSB bridge
author:         Manuel Estrada Sainz
[COLOR="#FF0000"]firmware:       orinoco_ezusb_fw[/COLOR]
srcversion:     31F2E52F6760FED8A053B6F
<snip>
```Please check to see if you have it:```
ls -al /lib/firmware | grep orinoco
```On my system, I get:```
-rw-r--r--  1 root root    6976 Jul  1 17:02 orinoco_ezusb_fw
```Is yours the same size, 6976 bytes? Is it corrupted? Check:```
md5sum  /lib/firmware/orinoco_ezusb_fw
```I get:```
3085b091c29fa6449c12e0d05af68a10  /lib/firmware/orinoco_ezusb_fw
```

---

### Post by TheAzther on 2015-07-01
in ls -al /lib/firmware | grep orinoco say this:
> -rw-r--r--  1 root root    6976 jun 26 17:54 orinoco_ezusb_fw

and in md5sum  /lib/firmware/orinoco_ezusb_fw i get this:
> [1a6fe624506d333ff6e3868528805256  /lib/firmware/orinoco_ezusb_fw


---

### Post by chili555 on 2015-07-01
I suggest we try to get a fresh copy and see if that helps. First, back up the existing firmware file:```
sudo mv /lib/firmware/orinoco_ezusb_fw  /lib/firmware/orinoco_ezusb_fw.bak
```Now, with a temporary internet connection:```
wget http://web.archive.org/web/20061206062642/http://www.agere.com/mobility/docs/windows_drivers_sr02-2.3.zip
unzip windows_drivers_sr02-2.3.zip WLAGS51.SYS
dd if=WLAGS51.SYS of=orinoco_ezusb_fw skip=10312 count=436 bs=16
cp  orinoco_ezusb_fw  /lib/firmware
```Now check the md5sum again:```
md5sum  /lib/firmware/orinoco_ezusb_fw
```I noticed this: [https://wireless.wiki.kernel.org/en/users/drivers/orinoco](https://wireless.wiki.kernel.org/en/users/drivers/orinoco)> features

**working**

Station mode
Ad-hoc mode
Monitor mode
WEP
WPA-PSK (TKIP)


**not working yet**

AP mode
Radiotap headers in monitor mode

**not supported**

WPA2
WPA-PSK (CCMP)It may be that your router needs to be set to the somewhat insecure WPA-TKIP instead of the recommended WPA2-AES (also known as CCMP) in order to connect. If your landlord, coffee shop or univversity uses the more secure WPA2-AES, you may never connect.

---

### Post by TheAzther on 2015-07-01
now md5sum show this:
> 3085b091c29fa6449c12e0d05af68a10  /lib/firmware/orinoco_ezusb_fw

what im suposed to do now? note those numbers are the same that md5sum show to you

---

### Post by chili555 on 2015-07-01
> what im suposed to do now?Reboot and see if you can connect. If not, let us see:```
dmesg | grep orinoco
cat /var/log/syslog | grep -e orin -e etwork | tail -n20
```

---

### Post by TheAzther on 2015-07-03
sorry for taking too long to answer you, sadly, its still dind´t working in  dmesg | grep orinoco say this:
> [   19.608458] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   20.420145] orinoco_usb: probe of 2-3:1.0 failed with error -14
[   20.468326] usbcore: registered new interface driver orinoco_usb
 
and cat /var/log/syslog | grep -e orin -e etwork | tail -n2 without the tp-link wifi adapter showed this:
> Jul  3 19:05:00 theazther-Evo-N610c NetworkManager[705]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan1/accept_ra': (2) No existe el archivo o el directorio
Jul  3 19:05:00 theazther-Evo-N610c NetworkManager[705]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan1/use_tempaddr': (2) No existe el archivo o el directorio
Jul  3 19:05:00 theazther-Evo-N610c NetworkManager[705]: <warn> (5) failed to find interface name for index
Jul  3 19:05:00 theazther-Evo-N610c NetworkManager[705]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Jul  3 19:05:00 theazther-Evo-N610c NetworkManager[705]: <error> [1435966500.844911] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Jul  3 19:05:00 theazther-Evo-N610c NetworkManager[705]: <warn> (5) failed to find interface name for index
Jul  3 19:05:00 theazther-Evo-N610c NetworkManager[705]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Jul  3 19:05:00 theazther-Evo-N610c NetworkManager[705]: <error> [1435966500.846783] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Jul  3 19:05:00 theazther-Evo-N610c NetworkManager[705]: <info> (wlan1): bringing up device.
Jul  3 19:05:00 theazther-Evo-N610c NetworkManager[705]: <warn> (5) failed to find interface name for index
Jul  3 19:05:00 theazther-Evo-N610c NetworkManager[705]: nm_system_iface_flush_routes: assertion 'iface != NULL' failed
Jul  3 19:05:00 theazther-Evo-N610c NetworkManager[705]: <warn> (5) failed to find interface name for index
Jul  3 19:05:00 theazther-Evo-N610c NetworkManager[705]: <warn> DNS: plugin dnsmasq update failed
Jul  3 19:05:00 theazther-Evo-N610c NetworkManager[705]: <info> Removing DNS information from /sbin/resolvconf
Jul  3 19:05:01 theazther-Evo-N610c NetworkManager[705]: <info> (wlan1): cleaning up...
Jul  3 19:05:01 theazther-Evo-N610c NetworkManager[705]: <warn> (5) failed to find interface name for index
Jul  3 19:05:01 theazther-Evo-N610c NetworkManager[705]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Jul  3 19:05:01 theazther-Evo-N610c NetworkManager[705]: <error> [1435966501.91462] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Jul  3 19:05:01 theazther-Evo-N610c NetworkManager[705]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Jul  3 19:05:01 theazther-Evo-N610c NetworkManager[705]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0e.2/usb1/1-3/1-3:1.0/net/wlan1, iface: wlan1)
 
(note some words are in spanish)

---

### Post by TheAzther on 2015-07-08
I SOLVED IT! i justo needid to update to utópico unicornio, thanks a lot for your help! :)

---

### Post by chili555 on 2015-07-09
Awesome! Glad it's working.

---

