---
title: "Ubuntu 14 LST receive wifi but not on the wifi"
date: 2014-10-15
forum: Networking &amp; Wireless
---

### Post by andyhuynh on 2014-10-15
I would like to mention specific excess long for everyone to understand, rather than a lack of: 


I use dell vostro 1450 Lap win 7 32 bit, a few days ago I installed ubuntu 14 LST in the 20GB partition, the installation process can tick the box whatever update it, pass it to enter wifi and wifi on, things occur normally, 


display it on ubuntu wifi connection success, BUT not on the network via firefox (available), ping google -> not found, ping 8.8.8.8 or 8.8.4.4, the unreachable
set ip: 
[COLOR=#333333][FONT=Helvetica]192.168.1.60 255.255.255.0 192.168.1.1 [/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica] 8.8.8.8[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica] 8.8.4.4
[/FONT][/COLOR]on wifi: everyone in the room sketchy normal, even the win 7 32 bit still on the network as usual, did not understand why the ubuntu it is not on the network 


- There are few articles saying use wicd, you can download the wicd in win 7 through ubuntu install but then it reports file not found wicd, then reinstall the update command is not well 


name@scandium:~$ ifconfig
[COLOR=#333333][FONT=Helvetica]lo        Link encap:Local Loopback  [/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]          inet6 addr: ::1/128 Scope:Host[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]          UP LOOPBACK RUNNING  MTU:65536  Metric:1[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]          RX packets:1469 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]          TX packets:1469 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]          collisions:0 txqueuelen:0 [/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]          RX bytes:123929 (123.9 KB)  TX bytes:123929 (123.9 KB)[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica] [/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]wlan0     Link encap:Ethernet  HWaddr cc:af:78:91:a3:c9  [/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]          inet addr:192.168.1.60  Bcast:192.168.1.255  Mask:255.255.255.0[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]          inet6 addr: fe80::ceaf:78ff:fe91:a3c9/64 Scope:Link[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]          RX packets:137 errors:0 dropped:0 overruns:0 frame:3479[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]          TX packets:535 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]          collisions:0 txqueuelen:1000 [/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]          RX bytes:12980 (12.9 KB)  TX bytes:48619 (48.6 KB)[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]          Interrupt:19 

desire to help people, actually a few days to find out should not last more then asked (read entire show some other post said, do not have to look before you ask, I'm looking for the next 5 pages should google keywords and sympathy for the ignorance of newcomers like me) 


PLS!


[/FONT][/COLOR]

---

### Post by jeremy31 on 2014-10-15
Please follow the instructions on how to download and run the wireless script [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

If you do not want to have to look for the file to attach it to your post, you can download pastebin before running the script and the script will ask if you want to upload to pastebin.  If you chose yes, the script will upload and display a URL that you can copy with your mouse and paste into a post.  The command to install pastebin is ```
sudo apt-get install pastebinit
```

---

