---
title: "please please please help!!"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by luhan on 2009-05-04
I can not get my shared 3G connection to work. My 3G modem is on a windows pc. I also hav a mac that connects threw that 3g connection. i have set up the ip address and dns but cant get it to work. i need my connection to work urgently

---

### Post by apienk01 on 2009-05-04
How are you connecting to that windows PC with 3G modem?

---

### Post by phantom3113 on 2009-05-04
Some other important information is: which version of ubuntu are you running, and what kind of wireless card are you using? (not sure if the card is important for 3G as I've never used it)

---

### Post by luhan on 2009-05-04
threw a network hub

---

### Post by luhan on 2009-05-04
using ver 8.10

---

### Post by luhan on 2009-05-04
its one of those vodafone usb jobbies

---

### Post by canadiandude007 on 2009-05-04
Hello,

Let's start with some basics ...

Does Ubuntu recognise the USB stick when you plug it in?  

What are the results of ...? > iwconfig

Do you see any information?

---

### Post by apienk01 on 2009-05-04
So you're connecting to the hub with a ethernet cable? Is the Mac attached to the hub as well and working? Is the hub set to plain DHCP without any MAC filters and with enough IP adresses to assign? If so, Ubuntu should work as well. Just plug in and Network Manager should report a connection. If it fails, please open up terminal, type dmesg and post the output.

---

### Post by canadiandude007 on 2009-05-04
Also if you see some wireless connection, realise you need to get it to work sometimes by using the command:

> ifconfig wlan0 up

---

### Post by luhan on 2009-05-04
iwconfig says no wireless extentions. but im not plugin the modem into the ubuntu pc. i wana access the network on a shared internet connection

---

### Post by luhan on 2009-05-04
All the network stuff works fine my ubuntu workstation can access my network but not the shared internet connection

---

### Post by abjt on 2009-05-04
> **luhan said:**
> iwconfig says no wireless extentions. but im not plugin the modem into the ubuntu pc. i wana access the network on a shared internet connection

luhan,
have you tried the Network Tools in System->Administration?

can you connect to your Windows PC from the "Lookup" tab of these tools?

I mean't on the Ubuntu machine.

---

