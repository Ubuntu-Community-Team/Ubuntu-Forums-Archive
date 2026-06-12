---
title: "Ubuntu 10.10 Cannot detect wireless network after install"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by M.DKeller on 2010-12-03
Hello everyone,
      I decided to install Ubuntu on my new Dell Studio 1558. The installation of Ubuntu went well, the only thing I cannot seem to get working is my connection to my home wireless network. I spent quite a bit of time last night navigating around Ubuntu and it is so clean clever and unique I am very excited to get rolling. I have these 2 questions.

First will Ubuntu automatically connect to my wireless network using some type of "wizard" once I enter my network password? I should note that I see the wireless indicator with the red exclamation point in the upper right hand corner of my screen, I played with the connection system through that but could not seem to make any progress.

Is there another location under a different menu that will help me connect to my wireless home network? I may not even be looking in the right part of town. Either way I will keep checking here and see if I cannot fix this on my own.

Thanks in advance for any help or tips getting this running.

-Matt

---

### Post by freshmeatz on 2010-12-03
Can you open a terminal and post back the output of
Code:
```

nm-tool
sudo iwconfig
cat /etc/network/interfaces


```

If all else fails read this thread :P

[http://ubuntuforums.org/showthread.php?t=1377829](http://ubuntuforums.org/showthread.php?t=1377829)

---

### Post by jplo on 2010-12-03
A good place to start (assuming this is desktop edition) would be System > Administration > Additional Drivers. Work through the dialogue box to see if any additional drivers are available. 

Also, search the Dell Support website, and also the Ubuntu Forums Dell section.

hope this helps.:KS

Additionally, Connection Settings are automatically saved once you successfully connected to a WiFi network

---

### Post by TBABill on 2010-12-03
You have a Broadcom BCM4312 I believe. That's the identifier of the wireless chipset....verify by using ```
lspci
``` in a terminal. Go to System>Administration>Hardware (or Additional Drivers in 10.10) and activate the STA driver when prompted. Then restart. 

You likely will still have no internet so you may need to do the following ```
sudo rfkill list
``` and if either soft or hard blocked are marked YES, then just ```
sudo rfkill unblock all
```

You may need to then ```
sudo modprobe wl
``` and enjoy.

---

### Post by M.DKeller on 2010-12-03
Hey guys thanks for the feedback: Here is the following terminal information.
 
[FONT=Batang][SIZE=3]kellers@ubuntu:~$ nm-tool[/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]NetworkManager Tool[/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]State: disconnected[/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]- Device: eth0 -----------------------------------------------------------------[/SIZE][/FONT]
[SIZE=3][FONT=Batang]  Type:              Wired[/FONT][/SIZE]
[SIZE=3][FONT=Batang]  Driver:            r8169[/FONT][/SIZE]
[SIZE=3][FONT=Batang]  State:             unavailable[/FONT][/SIZE]
[SIZE=3][FONT=Batang]  Default:           no[/FONT][/SIZE]
[SIZE=3][FONT=Batang]  HW Address:        B8:AC:6F:7B:57:77[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]  Capabilities:[/FONT][/SIZE]
[SIZE=3][FONT=Batang]    Carrier Detect:  yes[/FONT][/SIZE]
[SIZE=3][FONT=Batang]    Speed:           10 Mb/s[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]  Wired Properties[/FONT][/SIZE]
[SIZE=3][FONT=Batang]    Carrier:         off[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]kellers@ubuntu:~$ sudo iwconfig[/SIZE][/FONT]
[FONT=Batang][SIZE=3]lo        no wireless extensions.[/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]eth0      no wireless extensions.[/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]kellers@ubuntu:~$ cat /etcnetwork/interfaces[/SIZE][/FONT]
[FONT=Batang][SIZE=3]cat: /etcnetwork/interfaces: No such file or directory[/SIZE][/FONT]
[FONT=Batang][SIZE=3]kellers@ubuntu:~$ cat /etc/network/interfaces[/SIZE][/FONT]
[FONT=Batang][SIZE=3]auto lo[/SIZE][/FONT]
[FONT=Batang][SIZE=3]iface lo inet loopback[/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3][EMAIL="kellers@ubuntu:~$"]kellers@ubuntu:~$[/EMAIL][/SIZE][/FONT]
 
 
The good news is that if I plug into my router the internet works fine, also because this is a dual boot system with Windows 7 and everything works fine on the other end, I at least have the benefit of knowing it is not a hardware problem !!
 
I decided to take a different approach to learning Linux this time and put it right on my new Laptop so that I could learn it over a longer period of time with a new computer I would be using all the time. So I am really looking forward to getting this up and running. 
 
I will check out the forum links asap and see if I cannot get it up and running myself. 
 
Thanks guys !!
 
-Matt

---

### Post by M.DKeller on 2010-12-03
Network Controller is  Broadcom 4727

---

### Post by M.DKeller on 2010-12-03
I got it working guys, thanks for your help. All I did was followed the simple instructions listed above with a wired connection !!
 
" A good place to start (assuming this is desktop edition) would be System > Administration > Additional Drivers. Work through the dialogue box to see if any additional drivers are available. "
 
I am now in the process of downloading 174 updates and we are off !! 
 
Thanks everyone !!

---

