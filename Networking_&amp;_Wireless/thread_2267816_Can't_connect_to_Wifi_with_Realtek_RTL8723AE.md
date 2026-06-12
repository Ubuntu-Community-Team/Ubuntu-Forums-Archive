---
title: "Can't connect to Wifi with Realtek RTL8723AE"
date: 2015-03-04
forum: Networking &amp; Wireless
---

### Post by enricobe on 2015-03-04
Hello,
I am having a serious problem with Wifi and my Realtek RTL8723AE.
With 14.10 the Wifi works pretty fine, but in 15.04 I can't often connect to the Wifi. When I boot to Ubuntu 15.04 the wifi icons blinks, like if it is trying to connect to Wifi, but it never stops. It continues to blink and never connects. I have tried to disable the Network and the Wifi, but when I enable it again the network still doesn't connect. The only way to solve the problem is reboot the PC and it usually connects. If the Wifi is connected on boot, it works fine until I shut down the PC, but half of the times that I boot the PC it can't connect.

---

### Post by Smask on 2015-03-05
Linux support from Realtek is non-existent. All Linux drivers are reverse engineered, using the firmware from the Windows driver blob. It's easier to switch the NIC to something that work in Linux. [COLOR=#ff0000]

Beware if your computer is a Lenovo or a HP, those brands comes with hardware whitelist in the BIOS.[/COLOR] [COLOR=#ff0000]They won't boot unless you've bought the NIC directly from Lenovo/HP.  [/COLOR]There exists hacking tools that removes/disables the whitelist.

I have "Unauthorized network card is plugged in - Power off and remove the miniPCI network card." 						on my Lenovo 50-45

---

### Post by enricobe on 2015-03-05
My PC is a Toshiba and it's strange because with 14.10 the WiFi works pretty fine. Sometimes it  disconnects, but it's stable. With 15.10 I need to reboot twice every  time I want to use Ubuntu

---

### Post by Smask on 2015-03-05
> **enricobe said:**
> My PC is a Toshiba and it's strange because with 14.10 the WiFi works pretty fine. Sometimes it  disconnects, but it's stable. With 15.10 I need to reboot twice every  time I want to use Ubuntu

I went to 15.04 directly so I didn't experience it using utopic. I do have spotty WIFI connection and no Bluetooth whatsoever. The WIFI works for half an hour on average and then I have to disable/enable the network card.

---

### Post by dino99 on 2015-03-05
> **Smask said:**
> I went to 15.04 directly so I didn't experience it using utopic. I do have spotty WIFI connection and no Bluetooth whatsoever. The WIFI works for half an hour on average and then I have to disable/enable the network card.

if your wifi works with the 14.10 kernel, but not with the 15.04 one, then report against 15.04 kernel (ubuntu-bug linux)
but what is strange: it works from time to time and/or for a while only. So the kernel can't be blamed in such a case, but instead the wifi network.
Dont you have something usefull logged to narrow down that issue? (watch syslog/dmesg and/or the other /var/log/ files)

---

### Post by enricobe on 2015-03-05
> **9d9 said:**
> if your wifi works with the 14.10 kernel, but not with the 15.04 one, then report against 15.04 kernel (ubuntu-bug linux)
but what is strange: it works from time to time and/or for a while only. So the kernel can't be blamed in such a case, but instead the wifi network.
Dont you have something usefull logged to narrow down that issue? (watch syslog/dmesg and/or the other /var/log/ files)

I'm connected with a USB adapter and it works, so i confirm that is a realtek problem.

Here is the syslog AFTER that I have enabled the wifi (I have typed some 'X' in place of MAC addresses). 
[ATTACH]260470[/ATTACH]

Please, help me to understand where is the problem now I have restarted Ubuntu 4-5 times and never connected :'(

---

### Post by enricobe on 2015-03-07
Hi again, I have some useful updates :)

I can solve this problem going in Edit Connections (Modifica Connessioni in Italian) and removing the Wifi Network. Then i can try to reconnect and it connects correctly.
Maybe it isn't a driver related problem and is it a software problem?

---

### Post by enricobe on 2015-03-11
The problem did not solve in the way i suggested above. Sometimes it works, but often it doesn't. 
I have reported the problem in Launchpad and they suggest me to install and test the Kernel 4. 

I have understood to do like follows, please tell me if it's right or wrong:

1. download from [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D) the RC3
2. download the "generic" version for my architecture (amd64)
3. sudo dpkg -i *.deb
4. reboot

Is it correct? Need I do something else?

---

### Post by zika on 2015-03-11
```
cd /tmp
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0-rc3-vivid/linux-headers-4.0.0-040000rc3-generic_4.0.0-040000rc3.201503082035_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0-rc3-vivid/linux-headers-4.0.0-040000rc3_4.0.0-040000rc3.201503082035_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0-rc3-vivid/linux-image-4.0.0-040000rc3-generic_4.0.0-040000rc3.201503082035_amd64.deb
sudo dpkg -i linux*.deb
rm linux*.deb
```

---

### Post by enricobe on 2015-03-11
Thank you!

---

### Post by dino99 on 2015-03-11
This cant be a kernel issue, as that driver is present since kernel 3.8
[http://cateee.net/lkddb/web-lkddb/RTL8723AE.html](http://cateee.net/lkddb/web-lkddb/RTL8723AE.html)

you may need to run 'sudo journalctl' and/or read syslog to find some usefull warnings/errors; otherwise it means that the wifi connection is poor (bad ISP place coverage, waves breaking security, ...)

---

### Post by enricobe on 2015-03-11
WiFi connection can't be poor because I have the following values:
-Realtek on Ubuntu 15.04: max 90 Kb/s in download
-USB network adapter on Unbuntu 15.04: max 600 Kb/s in download
-Realtek on Windows: max 815 Kb/s download.

Same Wifi Network @ 2.4 GHz

I tried to read some logs as you can see in my previous posts, but i'm not so expert to fully understand them. On Launchpad the team has asked me to test with Kernel 4: the realtek **always connects** but it's slow. With the kernel 3.19 the wifi network card can't connect most of the times. So the Kernel 4 works a little better than 3.19 with this realtek. Now i'm trying with the kernel 3.16.x as requested on launchpad

---

### Post by enricobe on 2015-03-21
Hello,
I have some useful updates.

With the kernel 4 the network card always connects, but it it still slow.
I did some tests:

Yesterday evening (OS,download,upload,ping):
Windows, 5,95M, 0,41M, 58ms
Ubuntu  , 0,80M, 0,39M, 50ms

Today morning
MANJARO, 6,98M, 0,40M, 45ms
Ubuntu   , 0,80M, 0,37M, 48ms 

Manjaro Linux works fine with the same Wireless Network Card. I can suppose it's a problem of Ubuntu and not concerning the Kernel. 

I've also tried to go near the router (1 meter) and the Wifi has worked at full-speed. Maybe ubuntu drops too many packets that it considers "damaged"? I'm trying to find a solution, but I don't know how can I solve.

P.S. I really don't like Manjaro's GUI, but I can't waste 20 seconds everytime I need to post on a forum :lolflag:

---

### Post by dino99 on 2015-03-21
so its time to report a bug ;)

but maybe some tweaks too: google around 'ubuntu slow wifi', i get for example:
[http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/](http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/)

and some more too ):P

---

### Post by enricobe on 2015-03-21
> **9d9 said:**
> so its time to report a bug ;)

but maybe some tweaks too: google around 'ubuntu slow wifi', i get for example:
[http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/](http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/)

and some more too ):P

Thank you.
I have reported the bug here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1430509](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1430509) 
Do you think I should add something?

---

### Post by dino99 on 2015-03-21
> **enricobe said:**
> Thank you.
I have reported the bug here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1430509](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1430509) 
Do you think I should add something?

your title bug report is also bugged  :confused::confused:

'cant connect' and 'slow' : hm, how it can not be ?

---

### Post by enricobe on 2015-03-21
> **9d9 said:**
> your title bug report is also bugged  :confused::confused:

'cant connect' and 'slow' : hm, how it can not be ?

I have reported it on March, 10. 
I can change the title, but... what should I write? The main bug is the slowness.

---

### Post by dino99 on 2015-03-21
> **enricobe said:**
> I have reported it on March, 10. 
I can change the title, but... what should I write? The main bug is the slowness.

what hurts my eyes is the 'can't connect' (meaning its of course 'slow', can say =0 !!!)
but in fact you 'can' connect, but get non stable speed and is quite slow compared to other OSs

so a title like 'RTL8723AE wifi regression: badly slow compared to other OSs' ( but it is your report, so it(s up to you indeed) ):P

---

### Post by enricobe on 2015-03-21
> **9d9 said:**
> what hurts my eyes is the 'can't connect' (meaning its of course 'slow', can say =0 !!!)
but in fact you 'can' connect, but get non stable speed and is quite slow compared to other OSs

so a title like 'RTL8723AE wifi regression: badly slow compared to other OSs' ( but it is your report, so it(s up to you indeed) ):P

Thank again for your patience. I have changed the title as you suggested. 

The "can't connect" is not invented because the Wfi network really can't connect the most of the time (with the kernel 3.19). Works fine with 4.0 RC but it is slow.

 I've changed the title because I'm now using the kernel 4 and I can't still confirm the connection problem. Anyway, the main bug is the slowness and it is better to focus on that.

---

### Post by zika on 2015-03-21
Not having much mileage on that particular WiFi piece of HW but did You try ndisgtk having seen that Windows driver You seem to like?

---

### Post by enricobe on 2015-03-21
> **zika said:**
> Not having much mileage on that particular WiFi  piece of HW but did You try ndisgtk having seen that Windows driver You  seem to like?

Thank you, I'm going to try. 

I've found the drivers for Win7 and Win8 (both 64bit). Have you any experience about the compatibility of the drivers? Should I try to install the W8 or W7 version?


EDIT:
I have done some test, trying to install various versions of the driver and.... my wireless card doesn't work anymore :lolflag: I think that I should re-install my Ubuntu partition :D

---

### Post by enricobe on 2015-03-22
Last Update of this problem.
The problem is (maybe) not related to Ubuntu. 

Today I've installed Manjaro Linux and after the install the speed of network was terribly slow! From the liveCD the speed was near 7M in download, but from the installed OS it was only 0,8M!!! So I have searched online for a solution, but I did not find nothing useful at the beginning. After an hour of search I have found a useful post on a blog (I don't remeber the name of the blog, but Thank You!) where the author suggests to **disable** the "**WMM (Wi-fi Multi-Media)"** from the router. This is an option that you can find in the "QoS" settings of the router (Quality of Service).

The speed has immediatly gone up to 7M and now the network works very well. 

Now I need to report the solution to launchpad as I have opened a report. What I should do? Ask for the deletion of the bug report? Report the solution in the bug report?
Thank you all for your patience and I hope that this thread can be useful for someone else in the future :)

---

### Post by dino99 on 2015-03-22
Glad you finally found the good solution ):P
Please post it to your bug report; it can help some other users having the same issue and searching about it.

---

### Post by Randall_Paul_Allen on 2015-04-26
Enricobe, I am having the same issue with my new computer.  I'm dual booting it with Windows 8.1 and I don't have a problem with Wi-Fi.  I'm not sure if my Wi-Fi card uses the same driver as yours.  Mine is a Realtek RTL8723BE.  I don't know if the "B" instead of an "A" at the end of the product code is significant.  
Unfortunately, where I use the computer I don't have access to the router, so I can't try disabling the "WMM (Wi-fi Multi-Media)".  Since it doesn't seem like there's a good solution, I'd like to know what USB adaptor you are using.  In an earlier post you said you were using a USB adaptor that was working fine.  I'm planning to use one of those but I'd like to make sure I get one that will work with my lubuntu install.

---

### Post by cariboo on 2015-04-26
@Randall_Paul_Allen, I guess you missed the large banner at the top of the page, moved to Networking and Wireless.

---

### Post by rob89 on 2015-05-06
> **Randall_Paul_Allen said:**
> Enricobe, I am having the same issue with my new computer.  I'm dual booting it with Windows 8.1 and I don't have a problem with Wi-Fi.  I'm not sure if my Wi-Fi card uses the same driver as yours.  Mine is a Realtek RTL8723BE.  I don't know if the "B" instead of an "A" at the end of the product code is significant.  
Unfortunately, where I use the computer I don't have access to the router, so I can't try disabling the "WMM (Wi-fi Multi-Media)".  Since it doesn't seem like there's a good solution, I'd like to know what USB adaptor you are using.  In an earlier post you said you were using a USB adaptor that was working fine.  I'm planning to use one of those but I'd like to make sure I get one that will work with my lubuntu install.


Re: RTL8723_**BE**_ - I don't know if the BE makes a difference BUT, I have the RTL8723BE and the following fixed my intermittent wifi:

echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
  
... and reboot

  [h=2]For reference[/h]  My Ubuntu version is 15.04

  
I've got a RTL8723BE in a Toshiba Satellite L10W-B-102


  My precise symptom was that wifi would connect OK for a few minutes  then I'd "lose internet access" - actually, I found that I could no  longer ping the router even though the wifi was connected. 

  
My lspci output is: 02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter

AND THANKS to Jeremy - this solution is from his post: [https://askubuntu.com/questions/596665/ubuntu-14-04-14-10-15-04-wifi-disconnection/619910#619910](https://askubuntu.com/questions/596665/ubuntu-14-04-14-10-15-04-wifi-disconnection/619910#619910)

Finally, though this post is for a slightly different version of card, I really struggled to find the solution for the BE type so apologies for posting here but as I was so glad it worked, I wanted to share my joy to help others :-)

---

