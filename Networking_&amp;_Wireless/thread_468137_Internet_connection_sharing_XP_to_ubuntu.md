---
title: "Internet connection sharing XP to ubuntu?"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by Kyranor on 2007-06-08
Please can anyone help me.

I am trying to set up internet connection sharing in XP so that my second pc (ubuntu) can acces the internet.

I have a USB adsl modem connected to my XP PC and a ethernet network connecting the two pc's through a hub.

I can send files over the network no problem, also I can ping various websites on the ubuntu PC (only IP addreses though),  which does not work when the USB modem on the XP PC is disconnected, so I know the connecting must be ok, is that right?

I have the network IP of my XP PC (192.168.0.1)  in as the gateway and DNS on the ubuntu PC, is this correct?

Please help me... pulling my hair out here... 

I am here right now so if anyone could talk me through mabye? Im completely new to linux. used to windows sorting everything out for me.

Thank you

---

### Post by pebo on 2007-06-08
> **Kyranor said:**
> 

I have the network IP of my XP PC (192.168.0.1)  in as the gateway and DNS on the ubuntu PC, is this correct?
...and you can try adding your ISP's DNS server(s) to your /etc/resolv.conf file:```
sudo echo "nameserver [your isp nameserver dns]" >> /etc/resolv.conf
```HTH

---

### Post by Kyranor on 2007-06-08
Hmm the terminal comes up with:

Bash: /ect/resolv.conf: Permission denied

---

### Post by pebo on 2007-06-08
> **Kyranor said:**
> Hmm the terminal comes up with:

Bash: /ect/resolv.conf: Permission denied1. Did you spell it right?
2. Did you use sudo?
3. Alternatively you can edit it directly with```
sudo nano /etc/resolv.conf
```

---

### Post by Soybean on 2007-06-08
With sudo? That's odd.

But not really important. Just put your ISP's DNS server in as the DNS server (whatever the XP box has listed as its DNS server). Do it however you set up the network in the first place. 192.168.0.1 is just the gateway... your Ubuntu system will go through that gateway to get to the DNS. :)

EDIT: oops, pebo beat me to it. His advice is good too; ignore me. ;)

---

### Post by Kyranor on 2007-06-08
> **pebo said:**
> 1. Did you spell it right?
2. Did you use sudo?
3. Alternatively you can edit it directly with```
sudo nano /etc/resolv.conf
```


Ok im into the GNU nano now.... what do I do?

---

### Post by pebo on 2007-06-08
At the bottom of the file add```
nameserver [isp's dns]
```putting in the dns number of course. Then Ctrl-x y to save and close and try connecting again.

---

### Post by Kyranor on 2007-06-08
> **Soybean said:**
> With sudo? That's odd.

But not really important. Just put your ISP's DNS server in as the DNS server (whatever the XP box has listed as its DNS server). Do it however you set up the network in the first place. 192.168.0.1 is just the gateway... your Ubuntu system will go through that gateway to get to the DNS. :)

EDIT: oops, pebo beat me to it. His advice is good too; ignore me. ;)


Well i tried this also and now i can ping and traceroute to for example: [www.bbc.co.uk](www.bbc.co.uk) from ubuntu PC.

internet still comes with "timed out" message..?

---

### Post by Kyranor on 2007-06-08
> **pebo said:**
> At the bottom of the file add```
nameserver [isp's dns]
```putting in the dns number of course. Then Ctrl-x y to save and close and try connecting again.

Sorry you say bottom of file.. there is nothing there, should there be?

*edit*

Attempted inputting what you suggested:

It says error writing /etc/resolv.conf: no such file or directory

---

### Post by pebo on 2007-06-08
If you go into System->Administration->Network and go to the DNS tab does it list your DNS servers? (You can forget about the command line stuff and enter the servers here)
Edit: that's odd - I've got one!!

---

### Post by Kyranor on 2007-06-08
> **pebo said:**
> If you go into System->Administration->Network and go to the DNS tab does it list your DNS servers? (You can forget about the command line stuff and enter the servers here)

i inputted the primary+secondary DNS servers of my isp in here... Hope thats correct

*sorry earlier i said firefox gives a timed out message, it doesnt it says "server not found" *


*edit*

 I starting to think its the firewall, but even with that switched off Still the same problems, and traceroute doesnt work either, even though ping does.

---

### Post by Kyranor on 2007-06-08
> **pebo said:**
> 
Edit: that's odd - I've got one!!


Got a  /etc/resolv.conf  you mean?

---

### Post by Kzap333 on 2007-06-09
> **Kyranor said:**
> Please can anyone help me.

I am trying to set up internet connection sharing in XP so that my second pc (ubuntu) can acces the internet.

I have a USB adsl modem connected to my XP PC and a ethernet network connecting the two pc's through a hub.

I can send files over the network no problem, also I can ping various websites on the ubuntu PC (only IP addreses though),  which does not work when the USB modem on the XP PC is disconnected, so I know the connecting must be ok, is that right?

I have the network IP of my XP PC (192.168.0.1)  in as the gateway and DNS on the ubuntu PC, is this correct?

Please help me... pulling my hair out here... 

I am here right now so if anyone could talk me through mabye? Im completely new to linux. used to windows sorting everything out for me.

Thank you

I am havine the same problem I am running a LiveCD of Ubuntu and when I finaly manged to connect to my network (well I think I did) I cannn't get internet. I don't know if it is a problem with FireFox or what.

---

### Post by the_lad on 2007-06-11
i too have the same problem... ics set up correctly on a Win XP machine (I've previously gotten another XP machine to use ICS without dramas), Ubuntu on my other machine, can ping and traceroute both IP addresses and domain names, and yet Firefox will not load any pages. Firefox is able to resolve the domain names (can watch this in the status bar, and when I type in [www.firefox.com](www.firefox.com) it says "Waiting for www.mozilla.com" so I guess it can resolve it fine) but it seems it just won't load any more data than that...

---

### Post by the_lad on 2007-06-16
bump...

---

### Post by fuzzybunny on 2007-06-18
quick qustion, what hardware are you using as a modem? 
After days and days of battling I have diacovered from the techies at vodafone that my huawei e220 will not be able to share its connection :(

Correction: the techies don't know much... :) shared and happy!

---

### Post by SRTS on 2007-06-21
The above advice is not good, because usually your ISP assigns DNS servers automatically, and they may vary. That's why you also never have to define DNS servers in your dial-up connection: They will be assigned automatically!
What you have to do is to set your DNS to the same adress as your "standard gateway", 192.168.0.1 for ICS. I have a windows 2000 machine connected to a windows 2003 Server R2 with ICS, and it works perfect. That way you don't have to (and you actually shouldn't) worry about which DNS servers your provider is going to assign.

Edit: I just replaced the windows 2000 machine by an Ubuntu 7.04 machine, and strangely enough it will not do any DNS lookups, I can only ping IP adresses, although it's configured exactly like the win2000 machine -_- What's up with that?
Also, what command-line tool allows you to add/delete DNS servers? I just used the GUI to set it to the default gateway.

Edit: Ok, when I manually added the DNS servers I got from my ISP it actually worked. Does that mean a brandnew system like ubuntu 7.04 is unable (unlike old windows 2000) to work with setting the DNS to same IP as def.gateway for using the automatically assigned DNS servers? I cannot believe that though. If anyone know how to make it work, please reply though.

---

### Post by dechef on 2007-06-21
Just do this ma son : go to the XP machine and do the Network sharing , then at some point click on the "All other computers use this machine [XP MACHINE] to connect to the internet . Then reboot the XP box.

go to the UBUNTU box and then browse , make sure to turn your home page to any of  yo choice . op it works for u bro .

---

### Post by StGeorge on 2007-06-21
You shouldn,t need to.
When I installed Ubuntu on my Laptop and had Win98se with internet connection sharing on my desktop I simply connected to the internet on my desktop, plugged in my ethernet to the laptop, installed Ubuntu and the connection was made during install.
My problem now is the opposite.
I now have Ubuntu on my desktop with 98SE also on my desktop.
I cannot when I am in Ubuntu get Ubuntu to give internet access to my wifes XP on the network.
A real Pain.

---

### Post by fuzzybunny on 2007-07-05
Just for reference
I battled for ages to share my Huawei E220 connection and it just would not, even to a second XP box.

Eventually I installed ccProxy and that worked like a charm. Free for 3 connections.
I belive proxy+ will allow 10 free.

---

### Post by rakeshinx on 2007-11-16
maybe this will help
[http://theuselessstuffblog.blogspot.com/2007/11/connecting-to-your-windows-ad-hoc.html](http://theuselessstuffblog.blogspot.com/2007/11/connecting-to-your-windows-ad-hoc.html)

---

