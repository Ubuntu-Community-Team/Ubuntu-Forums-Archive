---
title: "Cannot connect to internet: Alfa awuso36h wireless adapter"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by dormeurduval on 2010-11-20
Hey everyone! I am an absolute noob to linux and I have no idea how to get my wireless adapter to work. I have Alfa awuso36h usb adapter, which comes a CD that has the rtl8187 Linux driver in a .tar.gz folder. I have no idea what to do with this since I'm not familiar with Linux, and I've just installed Ubuntu 10.04 an hour ago.

I left clicked the wireless access icon thing and it detected my usb adapter, but said that "wireless is disabled". When I right clicked the icon, "Enable Networking" is checked. My Ubuntu is installed on an laptop that has a broken internal adapter and it also shows up as disabled and I don't know if that has anything to do with my problem right now. I've tried looking around and typed a bunch of random things in the terminal but nothing seems to have worked so far, so if you walk me through this like I'm an idiot I would be so happy! Thank you!

---

### Post by jrev on 2010-11-20
Hello,
Have you got a wired connection on eth0 ? It's easier to start the Internet connection on a wired connection 
the usb modems don't work on Linux
check the documentation first :
[http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml)
hope it helps 
;)

---

### Post by BrandonC19 on 2010-11-20
Copy the .tar.gz to your desktop, then right click the .tar.gz item and select "Extract Here". Post what you get in the extracted folder. :)

---

### Post by dormeurduval on 2010-11-20
Jrev: Hmm, I'm not sure what you mean by that, sorry. I don't have a wired connection and my usb adapter is detected by the computer, but I don't have any connection and it says that "wireless is disabled". I'm wondering if that's related to my lacking a driver? The linux driver is in the CD but I have no clue what I'm supposed to do with it.

- Edit -

I can't connect directly with a wire because I share the internet with a couple of roommates and the modem is not in my room.

---

### Post by dormeurduval on 2010-11-20
When I extracted the .tar.gz file, I got another folder with a lot of indecipherable files. In the folder there's a drv.tar.gz, stack.tar.gz, makedrv, wlan0up, wlan0down, ifcg-wlan0, wlan0dhcp, wlan0rmv, makedrv, then three other folders: iee80211, rt18187, wpa_supplicant - 0.4.9 Confusing :(

---

### Post by khatikbbdn72 on 2010-11-20
well at least you got the driver in your case.., so wat u need to do is that..
right click on .tar.gz folder and select extract here
open your terminal and locate the place of your extracted folder
ex:
cd /home/user/(tar.gz) folder
sudo make install
enjoy

---

### Post by dormeurduval on 2010-11-20
Hey, for some reason after sudo make install I got "make:*** No rle to make target 'install'. Stop." Not sure what this means...

---

