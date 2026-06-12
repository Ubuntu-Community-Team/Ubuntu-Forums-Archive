---
title: "Cannot connect to wifi Ubuntu 16.04"
date: 2016-04-22
forum: Networking &amp; Wireless
---

### Post by anthony58 on 2016-04-22
Before I upgraded, I was running 14.04 and it was running fine until a couple days ago when the wifi stopped working on that device, all other devices, including Windows 10 on the same laptop worked fine.  

I did a fresh install of Ubuntu 16.04 and the same problem persists.  I can see my wifi network, among the others from my neighbors but I cannot connect to the network.  Using the lshw -c network command it shows that ubuntu identifies the card.  It is Wireless 7265 of the Intel Corporation.  I don't know what the issue is as I couldn't even figure it out in 14.04.  As I said before, 14.04 was done for about a month before it stopped working out of nowhere.

---

### Post by Hadaka on 2016-04-23
Hi, please try..
```
sudo apt-get update
sudo apt-get install git 
git clone https://github.com/OpenELEC/iwlwifi-firmware.git
cd iwlwifi-firmware/firmware 
sudo cp iwlwifi-7265*  /lib/firmware
```

From chili555's guide here -> #[http://askubuntu.com/questions/726292/cant-connect-wifi-with-intel-ac-7265-on-ubuntu-15-10-asus-zenbook-ux305](http://askubuntu.com/questions/726292/cant-connect-wifi-with-intel-ac-7265-on-ubuntu-15-10-asus-zenbook-ux305)
thanks.

---

### Post by anthony58 on 2016-04-23
Thanks for the quick response!  Regarding the code, if I can't connect to the internet, how would they work?

---

### Post by Hadaka on 2016-04-23
Hi anthony58. The code for wireless should always be loaded from a working wired
connection. If you do not have a working wired connection, such should be clearly
stated on your initial post,
thanks,

---

### Post by anthony58 on 2016-04-23
Oh okay thanks, sorry about that, didn't mention my laptop doesn't have an Ethernet port.  I'll get a USB to Ethernet conversion cable and give it a go.  Thanks again

---

### Post by anthony58 on 2016-04-23
I tried it after establing a connection through my phone, still no change after inputting the above commands in the terminal

---

### Post by Hadaka on 2016-04-23
Hi, Hopefully you still have your usb/ethernet cable. if so please
run and post a diagnostic report,
Please open a terminal ctrl/alt/t then Copy and paste the following command and press enter.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is ***wireless-info.txt***
Next.
From your directory please copy,paste and post the ***wireless-info.txt***
thanks.

---

### Post by sylar2 on 2016-04-24
Hi, [**[COLOR=#000000]Hadaka[/COLOR]**]("http://ubuntuforums.org/member.php?u=1599436") i have same issue this is my *** [wireless-info.txt]("http://pastebin.com/fzifGYk9") ***

---

