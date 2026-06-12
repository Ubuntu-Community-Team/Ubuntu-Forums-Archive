---
title: "Verizon AC595"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by halvara1 on 2008-03-24
Can anyone assist me in setting up my verizon wireless card? I have a AC 595 PCMCIA air card and want to run it on my laptop which has Ubuntu 7.10.  Any assistance would be greatly appreciated. 

Thanking you in advance.

---

### Post by lift28 on 2008-06-20
kubuntu hardy
--------------------------------------------
sudo nano /etc/ppp/peers/verizon
--------------------------------------------
-detach 
ttyUSB0 #adjust to your port -- insert card and do a dmesg - you will see it on the last few lines
115200
debug
noauth
defaultroute
usepeerdns
user [email]xxxxxxxxxx@vzw3g.com[/email] # phone # of card
show-password
crtscts
lock
connect '/usr/sbin/chat -v -t3 -f /etc/ppp/peers/verizon_chat'
lcp-echo-failure 0
lcp-echo-interval 0



--------------------------------------------
sudo nano /etc/ppp/peers/verizon_chat
--------------------------------------------

ABORT 'NO CARRIER' ABORT 'ERROR' ABORT 'NO DIALTONE' ABORT
'BUSY' ABORT 'NO ANSWER'
'' ATZ
OK-AT-OK ATDT#777
CONNECT \d\c

---------------------------------------
sudo nano /etc/network/interfaces
---------------------------------------
#add
iface ppp0 inet ppp
provider verizon-no-gps
#i have a gps which grabs usbttsy0 so i have 2 entrys-- remember to get your proper usbttys* right
iface ppp1 inet ppp
provider verizon

-------------------------------------
start the connection in networkmanger
i use knetworkmanger - i think networkmanager is same

if anyone has a better way post it- this was just trial and error.
if the connection buggers up - close the connection and reinsert card -- then restart the connection.
it has been working great for me for 3 days.
sorry for typos im driving lol

---

