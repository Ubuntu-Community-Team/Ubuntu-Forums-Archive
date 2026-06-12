---
title: "Wifi issues Lenovo ideapad 310"
date: 2016-11-12
forum: Networking &amp; Wireless
---

### Post by artulo on 2016-11-12
Recently bought me a new computer. My wifi does not work on ubuntu for some reason. It connects to the network but I cant ping google.com or use the internet.
This is my lspci:
[ATTACH=CONFIG]272084[/ATTACH]
Here is my ifconfig:
[ATTACH=CONFIG]272085[/ATTACH]

Can anyone help me? Guide me in the right direction..

---

### Post by wildmanne39 on 2016-11-12
I am sorry but the text is really small I can not read what it says, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by artulo on 2016-11-15
here is the output from wireless script

---

### Post by wildmanne39 on 2016-11-15
Which device are you trying to get working?

---

### Post by artulo on 2016-11-16
I think the interface is wlp2s0
its my default wlan that comes with the laptop.
Is it the interace you want to know or the name of the actual wireless card?

---

### Post by wildmanne39 on 2016-11-16
What kind of issues are you having when using the internal card? please disconnect the usb adapter, reboot and run the wireless script again:
Since you have already ran the script before you can just do this:
```
./wireless-info
```
Thanks

---

### Post by artulo on 2016-11-17
I removed my wireless usb adapter and restarted. Here is the output

---

### Post by artulo on 2016-11-17
The issues I am having is that whenever I connect to my networks, which are called Bota and Eduroam it connects, however the internet doesnt work when I use google for example.

---

### Post by wildmanne39 on 2016-11-17
You have to sign into the network through a web page correct? do you get redirected to that page? can you sign in?

---

### Post by artulo on 2016-11-17
No on my home network(Bota) i sign in through the normal wireless software on ubuntu. Same with my school network (Eduroam), however I use certificates for that, its an enterprise system. It works on windows, just not ubuntu.

---

### Post by artulo on 2016-11-17
So basically i can connect to my networks through the ubuntu wireless software that ubuntu has as default. However I cant use any site or ping any website

---

### Post by wildmanne39 on 2016-11-17
At college you have a nightmare with all those networks so close together, let's disable IPV6 and make sure IPV4 is enabled, I am going to post screenshots set your settings to much mine, even the dns settings will make a better connection.

If it still has issues please post the wifi info again this time while trying to connect to your personal wifi and not the school.
Thanks

---

### Post by wildmanne39 on 2016-11-17
Please post the output of:
```
dmesg | grep ath10k
```
```
ls /lib/firmware/ath10k_pci
```
because you have a firmware issue.

---

### Post by artulo on 2016-11-18
Doesnt seem to make a difference when i change the IPv6 settings. 
Ill post the ouput of my wifi when i get home.
However I have the output of dmesg that u asked for. However the ls doesnt find a /lib/firmware/ath10k_pci only /lib/firmware/ath10k
check the text file.

---

### Post by wildmanne39 on 2016-11-18
Your wifi signal is to low for ubuntu to connect too, anything under 50 percent is to low.
Let's try:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
if that does not work please do what is in post 28 of this thread.
[https://ubuntuforums.org/showthread.php?t=2304250&page=3](https://ubuntuforums.org/showthread.php?t=2304250&page=3)
Thanks

---

### Post by wadilson on 2016-12-14
The solution is to upgrade the system by using the network cable. The  updated system installs all new drivers and the wifi will work. The update worked on my Lenovo 310. The Wifi is now working perfectly.

---

