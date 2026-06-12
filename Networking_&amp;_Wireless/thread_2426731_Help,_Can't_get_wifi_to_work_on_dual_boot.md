---
title: "Help, Can't get wifi to work on dual boot"
date: 2019-09-12
forum: Networking &amp; Wireless
---

### Post by Justin18 on 2019-09-12
Hello all! 

I need assitance, I'm unable to get wifi to work on my laptop in ubuntu 19.04 dual booted with windows 10 
I have tried all types of google searches and have tried many of the "fixes" including installing and starting drivers through terminal and nothing seems to be working

I have bought a wifi adapter as well from amazon a Inamax nano 11ac adapter but it wants me to install drivers from a disk and this laptop doesnt have a optical drive. 

Please, any help is much appriciated. I may be slow to reply but I will check in on the thread. 

thank you! :D

---

### Post by wildmanne39 on 2019-09-12
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created. 

If you want to try to get the usb adapter working you will need to have it plugged in before you run the script.

---

### Post by Justin18 on 2019-09-12
Hello! 

Thanks for the reply. I followed the directions and ran the script. I have the network adapter plugged in. although if we can fix it without needing it I would be ok with that. I couldnt find the link to the pastebin so I had to upload it myself. but ive never used pastebin before so I'm sorry if I did this incorrectly

<script src="https://pastebin.com/embed_js/vDHQ82RT"></script>

---

### Post by pcfan1234 on 2019-09-13
Try the commands from here: [https://forum.ubuntuusers.de/topic/wlan-modul-nicht-aktieviert-unter-ubuntu-18-04/#Installationsanleitung-Treiber-8821ce-fuer-Realtek-WLAN-Karten-RTL8821CE](https://forum.ubuntuusers.de/topic/wlan-modul-nicht-aktieviert-unter-ubuntu-18-04/#Installationsanleitung-Treiber-8821ce-fuer-Realtek-WLAN-Karten-RTL8821CE)

---

### Post by Justin18 on 2019-09-13
> **pcfan1234 said:**
> Try the commands from here: [https://forum.ubuntuusers.de/topic/wlan-modul-nicht-aktieviert-unter-ubuntu-18-04/#Installationsanleitung-Treiber-8821ce-fuer-Realtek-WLAN-Karten-RTL8821CE](https://forum.ubuntuusers.de/topic/wlan-modul-nicht-aktieviert-unter-ubuntu-18-04/#Installationsanleitung-Treiber-8821ce-fuer-Realtek-WLAN-Karten-RTL8821CE)

Hello! 
Those commands had no effect whatsoever that I can tell. I followed the first command the second one to install showed a error that the directory did not exist. 

Should I wait for the original replier to answer?

---

### Post by pcfan1234 on 2019-09-13
I was able to run the seconds command git clone... 
Try again.

---

### Post by Justin18 on 2019-09-13
> **pcfan1234 said:**
> I was able to run the seconds command git clone... 
Try again.

Hello! 

I tried again at your asking this time separating the commands and it worked! thank you very much! 

I do have a question though, is my wifi now dependent on the usb wifi adapter I have plugged in or no?

---

### Post by pcfan1234 on 2019-09-13
No, you set up the internal one.
Try plugging of the usb adapter.

---

