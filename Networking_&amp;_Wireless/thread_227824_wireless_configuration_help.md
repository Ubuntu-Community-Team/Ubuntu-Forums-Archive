---
title: "wireless configuration help"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by linux_baby on 2006-08-02
hello all, i am new in this forum and also new using ubuntu...i need help for configuring my wireless network account...below is my  laptop details

laptop: acer travelmate 292LMi
60GB, centrino 1.5GHz, 512MB ram, ATI 9700, intel PRO/Wireless 2200BG (802.11 b(g WLAN), DVD

now, i have account on wirelless network in my home and also in my uni..both have same ID/password....and i was using winxp now wanna use ubuntu and also wanna configure my wireless account on ubuntu...how could i do that? please help...if u find this post too  stupid than please leave it and i am sorry (at least i want friendly help thats all i need).......any link,website help,is welcome...thank you.

NB: when i scan for wireless available network on winxp...it finds one network for my home and other network in university..but i can access both with same ID/password

---

### Post by judgekaster on 2006-08-02
a) you might want to try the "Networking" tool, (System->Administration->Networking).

b) also, post the results of

```
iwconfig
```
which you should enter in a terminal

---

### Post by Banewood on 2006-08-02
I've just recently succeeded in getting my Acer Aspire 3000 working with the built-in Broadcom WiFi.  Use the Synaptic Package Manager to get ndiswrapper and wpa_supplicant -- both are available as binaries. You'll probably have to expand the range of Repositories to search. Ndiswrapper is what you'll need to translate the Windows version of your WiFi driver (.INF and .SYS files).  The wpa_supplicant, which few seem to mention, is what you need if you're dealing with the WPA-PSK protocol in your wireless lan.
Good luck!

---

### Post by linux_baby on 2006-08-03
thnx for ur reply and help....i m trying and some funny thing happens...

when i type in console.....su  and next line password is wanted..i try several times with my login password but it failed...the thing is when i install ubuntu , in a point, its wanted a login name , i gave (example) 'linux' and pass word (example) 'ubuntu'....it is the login name to enter ubuntu machine..so when i rebot/boot ma laptop in ubuntu,at first a login and password is wanted and i gave those things....but using terminal window and type 'su'..which password i should gave? becoz while installing ubuntu,nothing is wanted for root password or something..thts why i cant access ifconfig or iwconfig commands....its saying permission denied....

wht should i do? is thr any file whr i can see my su password? 
should i re-install ubuntu? 
if i re-install..whch options i select for accessing administrator ?

---

### Post by Banewood on 2006-08-03
No, it's not necessary to re-install -- Ubuntu is made to work without a "root" account.  Instead of typing "su," type "sudo" and use your "ubuntu" password.  You'll be doing that a lot, I'm afraid.
E.g., 
sudo ndiswrapper
sudo wpa_supplicant -Bw -c/etc/wpa_supplicant.conf -ieth0
sudo wpa_gui
 
The hard part of this whole thing for me is dealing with access permissions.  What I recommend is to start up an editor with root privilege, e.g.,
sudo gedit
Then you can modify config files or change a file's permissions.
 
Hope this helps you.  I'm an Ubuntu neebie myself.

---

### Post by linux_baby on 2006-08-10
hello friends....thr something happen...when i rebot my laptop on ubuntu with wireless LAN card switch on (WLAN is builtin)..i can access internet on ubuntu......but if i switch my WLAN card after logon UBUNtu...no internet....wht happen??...(i never configure internet on ubuntu, above things happened automatically)..also i did software update on ubuntu when i access internet

---

