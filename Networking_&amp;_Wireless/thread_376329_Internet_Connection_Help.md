---
title: "Internet Connection Help"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by buried on 2007-03-04
I d/l and installed Ubuntu 6.06 (Dapper Drake) and am Trying to connect to the Internet (I have ADSL/LAN and really need help. I'm a Noob at Ubuntu and really love it but need help with the Intenet

---

### Post by gradedcheese on 2007-03-04
What does the network look like?  A PC wired to the modem directly?  A PC wired to a router that's connected to the modem?  The router and modem are one and the same?  Did it just work in Windows or did you need special ADSL connection software?

---

### Post by buried on 2007-03-04
No But My Computer (Lappy) Is a Acer 5053WXMi 
and I have a modem with a ethernet cable connected to my Laptop (Notebook) :|

---

### Post by gradedcheese on 2007-03-04
Ok, so your laptop is directly connected to the modem.  Now, is this modem a basic ADSL modem for which (in Windows) you needed some special software or ISP settings?  Or does it just give you an address (router style) and have everything work without configuration?  There's a big difference here and it helps to know which setup you have.

---

### Post by buried on 2007-03-05
> **gradedcheese said:**
> Ok, so your laptop is directly connected to the modem.  Now, is this modem a basic ADSL modem for which (in Windows) you needed some special software or ISP settings?  Or does it just give you an address (router style) and have everything work without configuration?  There's a big difference here and it helps to know which setup you have.

No software needed just go and click Broadband in Windows and type in Username and  Pass and I'm Connected
Oh yeah Ubuntu does Detect my ethernet thing as eth0 and it works but It doesn't let me enter my Username or Pass (BroadBand) 
Thanks gradedchesse, you're providing great help.(ISP settings)

---

### Post by fdrake on 2007-03-05
it sounds like you have a cable internet connection.
try this:

menubar>system>administration>networking>
select ethernet connection
sel proprties
check enable this connection
select DHCP
click ok
click on activate
set default device eth0

i assume you have a dinamic ip. hope it'll work.

---

### Post by buried on 2007-03-05
> **fdrake said:**
> it sounds like you have a cable internet connection.
try this:

menubar>system>administration>networking>
select ethernet connection
sel proprties
check enable this connection
select DHCP
click ok
click on activate
set default device eth0

i assume you have a dynamic ip. hope it'll work.

I don't know, But I have ISP setting (Username and Passwords)
and I Don't think that'll work but thanks and I'll give it a try.

---

### Post by fdrake on 2007-03-05
my mistake i missed the part in which you say you use an username and password.

---

### Post by buried on 2007-03-05
> **fdrake said:**
> my mistake i missed the part in which you say you use an username and password.

Ok Then Can **Anyone** help me here.:confused:

---

### Post by zvacet on 2007-03-05
When you do what fdrake say click on DNS.If you know your IP provider address(nameserver),than delete one you see when you opened DNS and replace it with your own.Close.In terminal type 
```
sudo pppoeconf
```
If this method fail try 
[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")
Replace Exec=gksudo /opt/rp-pppoe-3.8/go-gui with  Exec=gksudo tkpppoe
Restart.Programs>internet>rp-ppoe
First time may take some time before you see GUI.If you don´t get GUI do this
```
sudo -i
```
```
cd /opt/rp-pppoe
```
```
root@localhost rp-pppoe#./go
```

---

### Post by buried on 2007-03-05
> **buried said:**
> Ok Then Can **Anyone** help me here.:confused:

> **zvacet said:**
> When you do what fdrake say click on DNS.If you know your IP provider address(nameserver),than delete one you see when you opened DNS and replace it with your own.Close.In terminal type 
```
sudo pppoeconf
```
If this method fail try 
[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")
Replace Exec=gksudo /opt/rp-pppoe-3.8/go-gui with  Exec=gksudo tkpppoe
Restart.Programs>internet>rp-ppoe
First time may take some time before you see GUI.If you don´t get GUI do this
```
sudo -i
```
```
cd /opt/rp-pppoe
```
```
root@localhost rp-pppoe#./go
```
How are you gonna get the code from the site when you're not already online in ubuntu to download the .tar.gz file? does it work without going on the internet?

---

### Post by zvacet on 2007-03-05
From your post I understand that first option doasen´t work for you.Try type in terminal
```
pon dsl-provider
```
that have to triger your connection.Once you have conection download rp-pppoe.

---

### Post by buried on 2007-03-05
O.K I'll give it a try.

---

### Post by zvacet on 2007-03-06
Sorry,I overlooked Ubuntu version you use.This is what you are sopose to look at
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")
In this case you don´t need to replace anything in rp-pppoe.
P.S.In case that you have no luck with dhcp(just guessing that is your type of connection),try with static until you get rp-pppoe.

---

### Post by buried on 2007-03-06
Yeah got it Working by typing sudo pppoecinf in the terminal:lolflag: 
BIG thanks to anyone who replyed to my post, much appreciated.

---

