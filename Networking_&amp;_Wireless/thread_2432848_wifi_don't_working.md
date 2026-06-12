---
title: "wifi don't working"
date: 2019-12-09
forum: Networking &amp; Wireless
---

### Post by klays on 2019-12-09
hi, when i try to use wifi i can't, i only can access with ethernet cable, i try with "ifconfig", this is the output:
[HTML]root@klays:/home/klays# ifconfig
enp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 18:67:b0:3a:ae:14  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enx00e04c36dd85: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.90  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::31ee:3583:5de9:6a07  prefixlen 64  scopeid 0x20<link>
        ether 00:e0:4c:36:dd:85  txqueuelen 1000  (Ethernet)
        RX packets 2545  bytes 1778525 (1.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2275  bytes 318408 (318.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Bucle local)
        RX packets 646  bytes 60116 (60.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 646  bytes 60116 (60.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

[/HTML]

---

### Post by wildmanne39 on 2019-12-09
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

### Post by klays on 2019-12-09
add: when i try to use: "
sudo ip link set wlan0 up

"

the terminal outputs: root@klays:/home/klays# sudo ip link set wlan0 up
Cannot find device "wlan0"

---

### Post by klays on 2019-12-09
this my controller: 02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)

---

### Post by wildmanne39 on 2019-12-09
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by klays on 2019-12-09
file snipped

---

### Post by QIII on 2019-12-09
Please use pastebin and post the link here.

Do not ask the community to open a random compressed file.

Thanks.

---

### Post by wildmanne39 on 2019-12-09
You have to many drivers installed, please do:

```
sudo apt remove --purge firmware-b43-installer
```
Reboot and see if you can connect, if not run:
```
rfkill list All
```
does it still show a hard block if so do you have a physical switch that you can turn it on with or a key combination that turns your wifi on?

You do not need to bring the wifi up manually, you can and should use network manager in the upper right hand corner of the screen is an icon for networking and this driver usually requires a parameter to make it connect so please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
if it still does not connect please run and post the wireless script again so we can see if the changes stuck and what effect they have.

---

### Post by klays on 2019-12-09
[https://pastebin.com/vWxiG4rh](https://pastebin.com/vWxiG4rh)

---

### Post by klays on 2019-12-09
> **wildmanne39 said:**
> You have to many drivers installed, please do:

```
sudo apt remove --purge firmware-b43-installer
```
Reboot and see if you can connect, if not run:
```
rfkill list All
```
does it still show a hard block if so do you have a physical switch that you can turn it on with or a key combination that turns your wifi on?

You do not need to bring the wifi up manually, you can and should use network manager in the upper right hand corner of the screen is an icon for networking and this driver usually requires a parameter to make it connect so please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
if it still does not connect please run and post the wireless script again so we can see if the changes stuck and what effect they have.

the package "firmware-b43-installer" is not installed.

---

### Post by wildmanne39 on 2019-12-09
You have at least 3 drivers loaded so we will blacklist them:
```
sudo su
echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist cordic" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
exit
```
If you have not done so already please do the other commands I asked you to do after you did not find the b43 installer then reboot and if it does not connect then run and post another wireless file, you still have a hard block did you try to resolve that per my instructions in my previous post?

---

### Post by klays on 2019-12-09
when i try to use that commands shows "bash: /etc/modprobe.d/blacklist.conf: Permiso denegado", in english is "you dont have permission" or something

edit: the hard block still

---

### Post by wildmanne39 on 2019-12-09
After you pasted the command ```
sudo su
``` it should have asked you to type your password which you will not see as you type but when you are done typing it hit enter and then paste the commands one line at a time and it should run unless you enter the wrong password.
```
echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist cordic" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
exit
```

---

