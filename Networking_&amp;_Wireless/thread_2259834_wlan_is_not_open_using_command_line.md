---
title: "wlan is not open using command line"
date: 2015-01-07
forum: Networking &amp; Wireless
---

### Post by Hasan55 on 2015-01-07
guys my laptop wlan is not opening by command line untill trip the power button of wlan. i used these commands.....


```
hasan@mx1:~
$ sudo su -
[sudo] password for hasan: 
root@mx1:~# iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.

root@mx1:~# ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
root@mx1:~# 
```





plz help me giving me some suggestion   what is worng here...thanks

---

### Post by slickymaster on 2015-01-07
*Moved to the ***Networking & Wireless*** sub-forum*

@Hasan55:
I've edited your post, adding code tags to it because output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of 'Code' tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by Al1000 on 2015-01-08
Try the following commands one at a time:

```
sudo rfkill unblock all
sudo /etc/init.d/networking restart
sudo ifconfig wlan0 up
```

You might then need to restart your system, but hopefully that should do the trick.

---

