---
title: "Can connect to router but without internet, ubuntu 16.04"
date: 2018-01-27
forum: Networking &amp; Wireless
---

### Post by jonatanlv on 2018-01-27
Hi all,

I'm having trouble with my internet connection.

I'm able to connect to my router, it says that I'm connected, however when I don't get to internet.

Find attached the wireless-info result.

Thank you in advance.

---

### Post by Hadaka on 2018-01-27
Hi the report indicates several issues that may be contributing
to the inability to access the internet.

#*wlp3s0 ESSID:"THOM_ONO1867" Power Management**[COLOR=#ff0000]-on[/COLOR]**
*To correct..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
#*THOM_ONO1867 <MAC 'THOM_ONO1867' [AC1]> 2412 MHz  54 Mbit/s  66  &#9602;&#9604;&#9606;_  **[COLOR=#ff0000]WPA1 WPA2[/COLOR]** yes*
*To correct..
```
Access modem configuration for ESSID:"THOM_ONO1867" and set to WPA2 Only..not mixed
```
#*Region- Europe/Madrid (based on set time zone)-country **[COLOR=#ff0000]00[/COLOR]** DFS-**[COLOR=#ff0000]UNSET[/COLOR]**
*To correct..
```
sudo iw reg set ES
sudo sed -i 's/=.*/=ES/' /etc/default/crda
```
#*wlp3s0 'THOM_ONO1867'>Group Cipher -**[COLOR=#ff0000]TKIP[/COLOR]**,Pairwise Ciphers **[COLOR=#ff0000]TKIP[/COLOR]**,WPA Version **[COLOR=#ff0000]1[/COLOR]**,WPA Version [COLOR=#ff0000]**2**[/COLOR]
*To correct..
```
Access router configuration and set to WPA2 only AES CCMP ..NO..tkip
```
Make all correction if possible,boot and test wireless.
*If after above changes you are still having difficulty please submit a NEW wireless report.
Thanks.

---

### Post by jonatanlv on 2018-01-28
Hi Hadaka:

I think I did everything you told me and it didn't work.

Attached is the new report.

Thank you very much.

---

### Post by Hadaka on 2018-01-28
Hi, please configure the Wireless connection like the attached..
Click in this order..
#wifi icon
#Edit Connections
#Wireless tab
#Your SSID - THOM_ONO1867
#Edit
#IPv4 tab
#Change Method to..
#**[COLOR=#ff0000]*[/COLOR]**Automatic (DHCP)addresses only
#set DNS servers to..
$**[COLOR=#ff0000]*[/COLOR]**8.8.8.8,8.8.4.4
#**[COLOR=#ff0000]*[/COLOR]**SAVE
[ATTACH=CONFIG]278357[/ATTACH]

---

### Post by jonatanlv on 2018-01-31
Hi Hadaka,

It didn't work. Could you tell me anything else to test?

Thank you in advance.

---

### Post by Hadaka on 2018-01-31
Hi, please post the output of..
```
ping -c2 localhost | awk '/packets/'
ping -c2 192.168.0.1 | awk '/packets/'
ping -c2 8.8.8.8 | awk '/packets/'
ping -c2 google.com| awk '/packets/' 
```
Thanks

---

### Post by jonatanlv on 2018-02-03
Hi Hadaka:

This is the output:
```

2 packets transmitted, 2 received, 0% packet loss, time 999ms
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
ping: unknown host google.com
```

Thank you

---

### Post by Hadaka on 2018-02-03
Hi, please give this a try..
[https://askubuntu.com/questions/886359/ping-8-8-8-8-works-but-ping-www-google-com-doesnt](https://askubuntu.com/questions/886359/ping-8-8-8-8-works-but-ping-www-google-com-doesnt)
Thanks.

---

### Post by jonatanlv on 2018-02-03
Hi Hadaka,

It worked, thank you very much for your help.

---

### Post by Hadaka on 2018-02-03
Hi, Glad that worked for you !
and Thank You for marking your thread Solved.

---

