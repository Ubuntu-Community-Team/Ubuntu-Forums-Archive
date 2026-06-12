---
title: "HP cant connect to internet"
date: 2017-08-20
forum: Networking &amp; Wireless
---

### Post by senseitraveler on 2017-08-20
Hello, guys. I have a problem. I just buy HP dv6000 and instal ubuntu 16.04 and Windows vista is there aswell. My internet conection is just wifi without router so i cant use cabel connection and of course my ubuntu have a bug on wireless :o I read many posts about it but i simly dont understand what they say... now i understand what the sudo means but still i dont understand any of programing stuff. Is there any option how to fix the wireless on my HP just with the wifi connection? Thx for every answer

---

### Post by jeremy31 on 2017-08-20
Moved to its own thread, what is the result for ```
rfkill list
```

---

### Post by senseitraveler on 2017-08-20
Hi Jeremy, thx for help... it was good task for me to copy text from one system to other one:p and here it is

pavel@ubuntu:~$ rfkill list
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

---

### Post by jeremy31 on 2017-08-20
Check ```
lspci -nnk | grep -iA3 net
```
If it says you have a RTL8723BE wifi chipset, do
```
sudo modprobe -r rtl8723be
```
```
sudo modprobe rtl8723be ant_sel=1
```
```
iwlist scan | egrep -i 'ssid|level'
```
```
sudo modprobe -r rtl8723be
```
```
sudo modprobe rtl8723be ant_sel=2
```
```
iwlist scan | egrep -i 'ssid|level'
```
You should notice a difference in the number of AP's you can see with one setting.
If you don't have the RTL8723be, see the wireless script link in my signature

---

### Post by senseitraveler on 2017-08-20
ok i use your method 2 without  internet and i have a problem with run the: **wireless-info.txt    I do execute it in proprietes and  all what i can is to open the file. any advice?**

---

### Post by gordintoronto on 2017-08-20
As a comment, Wi-Fi is only available from a router. These days, many people use a single device which combines modem and router functions.

---

### Post by Hadaka on 2017-08-21
Hi, please COPY and paste these command one at a time..
```
arch
uname -r
lsmod | awk '/mac80211/'
lspci -n | awk '/0200|0280/{print$3}'
```

Please post the output of each command.
Thanks

---

### Post by senseitraveler on 2017-08-21
first of all thanks everyone fer help and patience. Second i use BT wifi hotspot so yes I have just wifi and here is result of terminal

[INDENT] pavel@ubuntu:~$ arch[/INDENT][INDENT]x86_64[/INDENT][INDENT]pavel@ubuntu:~$ uname -r[/INDENT][INDENT]4.10.0-28-generic[/INDENT][INDENT]pavel@ubuntu:~$ lsmod | awk '/mac80211/'[/INDENT][INDENT]mac80211              782336  1 b43[/INDENT][INDENT]cfg80211              602112  2 b43,mac80211[/INDENT][INDENT]pavel@ubuntu:~$ lspci -n | awk '/0200|0280/{print$3}'[/INDENT]

---

### Post by Hadaka on 2017-08-21
Hi pavel, thank you for posting the outputs of the commands.
you forgot to post the output of..
Please COPY and paste..
```
lspci -n | awk '/0200|0280/{print$3}'
```
please post the output. this gives us the pci-id of your network cards.
Thanks

---

### Post by senseitraveler on 2017-08-21
Hello, sorry for that, here is result...

[COLOR=#000000][FONT=Ubuntu Mono, monospace]lspci -n | awk '/0200|0280/{print$3}'[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]14e4:4315[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]10ec:8136[/FONT][/COLOR]

---

### Post by Hadaka on 2017-08-21
Thank you, using your bt hotspot please COPY and paste one command at a time.
*Do every command even if you get get an error or file not found. That is not
a problem but do every command.
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
then disconnect the blue tooth connection..boot
and test wireless.
Thanks

---

### Post by senseitraveler on 2017-08-24
Hello, sorry my sd card has died. It take some time to buy new one. But now i have new one so here is the result of your codes. I do every comand separetly but Im not sure if you understand because my ubuntu have Czech republic location. Thx for all help and feel free to ask about translation if its necesary. Have a nice day

pavel@ubuntu:~$ sudo apt-get update
[sudo] password for pavel: 
Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
  Do&#269;asné selhání p&#345;i zji&#353;&#357;ování &#8222;security.ubuntu.com&#8220;
Err:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease
  Do&#269;asné selhání p&#345;i zji&#353;&#357;ování &#8222;gb.archive.ubuntu.com&#8220;
Err:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease
  Do&#269;asné selhání p&#345;i zji&#353;&#357;ování &#8222;gb.archive.ubuntu.com&#8220;
Err:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease
  Do&#269;asné selhání p&#345;i zji&#353;&#357;ování &#8222;gb.archive.ubuntu.com&#8220;
Na&#269;ítají se seznamy balík&#367;&#8230; Hotovo
W: Selhalo sta&#382;ení [http://gb.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Do&#269;asné selhání p&#345;i zji&#353;&#357;ování &#8222;gb.archive.ubuntu.com&#8220;
W: Selhalo sta&#382;ení [http://gb.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Do&#269;asné selhání p&#345;i zji&#353;&#357;ování &#8222;gb.archive.ubuntu.com&#8220;
W: Selhalo sta&#382;ení [http://gb.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Do&#269;asné selhání p&#345;i zji&#353;&#357;ování &#8222;gb.archive.ubuntu.com&#8220;
W: Selhalo sta&#382;ení [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Do&#269;asné selhání p&#345;i zji&#353;&#357;ování &#8222;security.ubuntu.com&#8220;
W: N&#283;které indexové soubory se nepoda&#345;ilo stáhnout. Jsou ignorovány, nebo jsou pou&#382;ity star&#353;í verze.








pavel@ubuntu:~$ sudo apt-get remove --purge bcmwl-kernel-source
Na&#269;ítají se seznamy balík&#367;&#8230; Hotovo
Vytvá&#345;í se strom závislostí       
Na&#269;ítají se stavové informace&#8230; Hotovo
E: Nelze najít balík bcmwl-kernel-source






pavel@ubuntu:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove '/etc/modprobe.d/blacklist-bcm43.conf': No such file or directory






pavel@ubuntu:~$ sudo apt-get install firmware-b43-installer
Na&#269;ítají se seznamy balík&#367;&#8230; Hotovo
Vytvá&#345;í se strom závislostí       
Na&#269;ítají se stavové informace&#8230; Hotovo
E: Nelze najít balík firmware-b43-installer






pavel@ubuntu:~$ sudo modprobe b43
[sudo] password for pavel: 
pavel@ubuntu:~$ sudo modprobe b43
pavel@ubuntu:~$ 
pavel@ubuntu:~$ 
pavel@ubuntu:~$

---

### Post by Hadaka on 2017-08-24
Hi..this..
```
E. Nelze najít balík firmware-b43-installer
```
Means..in English..
```
E. Unable to find firmware-b43-installer package
```

You must be connected to the internet for this command to work.

Can you connect to the internet by some means ?...yes/no ??
Please advise.
Thanks.

---

### Post by senseitraveler on 2017-09-09
in few days i hope i can finally connect my laptop to cable-net. I hope it sort out my problem.

---

### Post by praseodym on 2017-09-09
Download this package (somehow), save it in your "Downloads" folder and run
```

sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

[https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)  

Reboot

---

### Post by senseitraveler on 2017-09-11
Hello praseodym. It looks like you know how to help me!! I folow your instruction and here is the result. ( I change word downloads to stazene because of czech location of my ubuntu. When did I use the code with word Downloads my ubuntu can't find the folder) That is what terminal shows me when i put the code in and press enter terminal just show me what is down below. Firmware was in downloads/stazene folder in my ubuntu. Any other advice? thx a lot and have a nice day.

 sudo tar xvf ~/Sta&#382;ené/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
b43/
b43legacy/
b43/b0g0initvals5.fw
b43/b0g0bsinitvals5.fw
b43/a0g0initvals5.fw
b43/a0g1initvals5.fw
b43/a0g0bsinitvals5.fw
b43/a0g1bsinitvals5.fw
b43/b0g0initvals9.fw
b43/b0g0bsinitvals9.fw
b43/a0g0initvals9.fw
b43/a0g1initvals9.fw
b43/a0g0bsinitvals9.fw
b43/a0g1bsinitvals9.fw
b43/n0initvals11.fw
b43/n0bsinitvals11.fw
b43/n0absinitvals11.fw
b43/lp0initvals13.fw
b43/lp0bsinitvals13.fw
b43/b0g0initvals13.fw
b43/b0g0bsinitvals13.fw
b43/a0g1initvals13.fw
b43/a0g1bsinitvals13.fw
b43/lp0initvals14.fw
b43/lp0bsinitvals14.fw
b43/lp0initvals15.fw
b43/lp0bsinitvals15.fw
b43/ucode5.fw
b43/ucode9.fw
b43/ucode11.fw
b43/ucode13.fw
b43/ucode14.fw
b43/ucode15.fw
b43/pcm5.fw
b43legacy/a0g0bsinitvals5.fw
b43legacy/b0g0initvals2.fw
b43legacy/b0g0initvals5.fw
b43legacy/b0g0bsinitvals2.fw
b43legacy/a0g1initvals5.fw
b43legacy/a0g0initvals2.fw
b43legacy/a0g1bsinitvals5.fw
b43legacy/a0g0initvals5.fw
b43legacy/b0g0bsinitvals5.fw
b43legacy/a0g0bsinitvals2.fw
b43legacy/pcm5.fw
b43legacy/pcm4.fw
b43legacy/ucode11.fw
b43legacy/ucode5.fw
b43legacy/ucode4.fw
b43legacy/ucode2.fw

---

### Post by praseodym on 2017-09-11
Ok, did you reboot?

---

### Post by senseitraveler on 2017-09-11
ha ha ha... that small word on the end of your quote.... Reboot... i missed it. But now I'm such a happy man!! Thanks you thousand times praseodym!! my linux on HP dv 6000 have a very good (better then on windows) wi-fi connection!! thx u all and have a nice day

---

