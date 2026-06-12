---
title: "No WiFi adapter found in Ubuntu 18.04, HP Laptop 15q-bu0xx"
date: 2018-05-21
forum: Networking &amp; Wireless
---

### Post by zueore on 2018-05-21
I've installed my Ubuntu 18.04 with minimal installation mode with keeping the option to install WiFi drivers along. But still I couldn't use the WiFi, since the setting is showing that there is no WiFi devices found. 

Attaching pastebin link from terminal outputs. Tried most of the solutions mentioned in forum like , sudo apt-get install --reinstall bcmwl-kernel-source

[http://paste.ubuntu.com/p/52nm6tsyqz/](http://paste.ubuntu.com/p/52nm6tsyqz/)

---

### Post by jeremy31 on 2018-05-21
```
sudo apt remove bcmwl-kernel-source && sudo apt install git dkms
git clone -b extended [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```
Reboot
If you notice weak signal try
```
sudo modprobe -r rtl8723de && sleep 5 && sudo modprobe rtl8723de ant_sel=1
```
and see if it is better, if not do 
```
sudo modprobe -r rtl8723de && sleep 5 && sudo modprobe rtl8723de ant_sel=2
```

---

### Post by zueore on 2018-05-25
Wow! That was a huge help. Thanks.

---

### Post by venki68 on 2018-06-10
thank you jeremy 31, Now wifi adapter is on.

---

### Post by zueore on 2018-06-13
Is there any way to do run this modrobe command automatically while booting up? It's becoming irritating to run this everytime inorder to connect to WiFi!

---

### Post by jeremy31 on 2018-06-13
Yes ```
echo "options rtl8723de ant_sel=X" | sudo tee /etc/modprobe.d/rtl8723de.conf
```
Replace X with whatever setting worked best

---

### Post by flash1996 on 2018-06-28
HI,
I installed the minimal version of Ubuntu 18.04 and the problem is wifi gets disconnected and automatically airplane mode gets turned on which i couldn't disable manually. so I used the commands you have given and i rebooted it after few minutes the wifi option wasn't there and says "wifi adapter is not found " please help me out here.

---

### Post by chili555 on 2018-06-28
> **flash1996 said:**
> HI,
I installed the minimal version of Ubuntu 18.04 and the problem is wifi gets disconnected and automatically airplane mode gets turned on which i couldn't disable manually. so I used the commands you have given and i rebooted it after few minutes the wifi option wasn't there and says "wifi adapter is not found " please help me out here.Please start your own new question and include the diagnostics report from here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by dubeysandeep on 2018-07-05
Hi @jeremy31,

Thanks for posting the solution but i tried the way you have asked and that didn't resolved my problem "wifi adapter is not found ". can you please help i have added logs  for my device info over here [https://pastebin.com/qzsL029z](https://pastebin.com/qzsL029z).

---

### Post by ayemin6060 on 2018-07-31
Hi jeremy
   My laptop is Dell Inspiron 3442. I've also the same problem that showing '' no wifi adapter .''So I can't use wifi on my laptop that recently installed Ubuntu 18.04 alongside with window 10. I tried with your codes. The first line of codes work.But others do not.Please help.

---

### Post by jeremy31 on 2018-07-31
> **ayemin6060 said:**
> Hi jeremy
   My laptop is Dell Inspiron 3442. I've also the same problem that showing '' no wifi adapter .''So I can't use wifi on my laptop that recently installed Ubuntu 18.04 alongside with window 10. I tried with your codes. The first line of codes work.But others do not.Please help.

Please start a new topic and include results from the wireless script link in my signature

---

### Post by kouani on 2018-08-07
HI ,mate thanx a lot ..it worked wonders

---

### Post by avinal on 2018-08-11
I am experincing the same problem on my HP Pavilion x360 14-cd-0087-tu .....would you please suggest me how to rectify this.....above process is not working for me

---

### Post by chili555 on 2018-08-11
> **avinal said:**
> I am experincing the same problem on my HP Pavilion x360 14-cd-0087-tu .....would you please suggest me how to rectify this.....above process is not working for mePlease start your own new question and include the diagnostics report from here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by kuhncasey.76.gmail.com on 2018-08-12
ive tried over 30 fixes. this one doenst work either. i have hp probook 6465b. there is a greyed out option in the network that says wifi disabled by hardware switch. ive got a virtual machine running Kali and cannot get past this wifi issue. can you point me someplace beside best buy to get this fixed.

---

### Post by jeremy31 on 2018-08-12
Please start your own topic and include results from the wireless script link in my signature

---

### Post by wildmanne39 on 2018-08-12
Hello kuhncasey.76.gmail.com, please start your own thread so you can get the help you need, since this is in a vm I assume you know to be able to use wifi in the vm you need to have an usb adapter and since you are using Kali you will have a better chance of getting it to work at the kali forum, assuming again that you want the hacking tools to work because we do not support that topic in the Ubuntu Forums.

---

### Post by Strusty on 2018-09-10
This information is great, but it is incomplete- for those who have not been able to get this working.

After the cited procedure, you will need to cd into the source tree and, 

$sudo su -
#make clean
#make all
#make install

after reboot, you will have working wifi.  dkms is not sufficient.

---

### Post by chili555 on 2018-09-10
> **Strusty said:**
> This information is great, but it is incomplete- for those who have not been able to get this working.

After the cited procedure, you will need to cd into the source tree and, 

$sudo su -
#make clean
#make all
#make install

after reboot, you will have working wifi.  dkms is not sufficient.First, there is a slight but real security risk running sudo su. I cannot recommend increasing risk if there is another way.

Second, in what way and in what circumstance is dkms insufficient?

---

### Post by prashobhpackal on 2018-09-12
am having the same issue. Not yet resolved. updated to 18.04 version, but still showing no drivers available

---

### Post by majedaly on 2018-09-12
> **Strusty said:**
> This information is great, but it is incomplete- for those who have not been able to get this working.

After the cited procedure, you will need to cd into the source tree and, 

$sudo su -
#make clean
#make all
#make install

after reboot, you will have working wifi.  dkms is not sufficient.

Yes, this is the only option that worked. DKMS simply doesn't work. The ant_sel=2 works better with HP3060

---

### Post by jeremy31 on 2018-09-12
The only thing I can see that would cause issues using dkms is that it doesn't install the firmware for the rtl8723de
```
sudo cp -fr ~/rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
```
Then dkms will work

---

### Post by chili555 on 2018-09-12
> **prashobhpackal said:**
> am having the same issue. Not yet resolved. updated to 18.04 version, but still showing no drivers availableYou won't get much attention in a thread that is already marked Solved. 

Please start your own new question and include the diagnostics report from here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by 11tripin11 on 2018-10-24
Thank you sooooo very much. You are a figurative lifesaver. <3  :D

---

### Post by coffeecat on 2018-10-24
Thread Closed to prevent any more necro-hijacks. 

If you need help with your wireless adapter, please start your own thread, linking back to this one **if** it is relevant.

---

