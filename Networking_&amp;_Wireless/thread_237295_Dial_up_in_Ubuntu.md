---
title: "Dial up in Ubuntu"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by thilina on 2006-08-15
Coz lots of people are saying Ubuntu is free,I installed Ubuntu 5  on my PC.Of course I think its great!!.But there is a big problem for me,How to create a dial-up connection???
        In system---->Administration--->Networking I was able to create a dial-up connection( actually a pppo connection ).But when I click on Activate the pc says that it was activated,But the phone does not show any signs of activation(I am using a CDMA phone to dial-up).Even the modem is not detected by the pc.
I hav plugged my modem in to Serial port 1(/dev/ttyS0).When I try to autodetect the modem it wont get autodetected too.
So wat could be the cause of the problem??
Wat can I do to activate the dial-up connection??

---

### Post by thilina on 2006-08-16
no one to help??
I thought this place is crowded with experts,but now,I cant see any!!!!

---

### Post by Fittersman on 2006-08-16
well im not sure because i cant get my modem to work but have you tried going into the terminal and typing something like pon or ppon or pppon (i cant remember how many p's there are) i dunno something like that and to shut it off you type poff or ppoff...

hope that helps and, what modem do you use?

---

### Post by thilina on 2006-08-16
Well guys,i waz able to create a connection via the command "sudo pppconfig".And the modem succesfully dials via the command "sudo pon provider_name".But nothing can be gained from this.Firefox cant go to a web site,Evolution cant get e-mail,Gaim cant chat,Even a network activity is not shown in the system moniter.I even tried tha firefox ipv6 trick,but waz no use.Can anybody help me??????????????????????

---

### Post by thilina on 2006-08-16
what modem do you use?

I am using a CDMA phone which has a built in modem to dial-up.In windows it uses generic windows drivers.The brand is "Aiji systems".Model is AP-110.

---

### Post by thilina on 2006-08-16
no one to help??

---

### Post by mpvano on 2006-08-16
Deleted - thread is too deep to be read coherently

---

### Post by Dana on 2006-08-16
> **thilina said:**
> Well guys,i waz able to create a connection via the command "sudo pppconfig".And the modem succesfully dials via the command "sudo pon provider_name".But nothing can be gained from this.Firefox cant go to a web site,Evolution cant get e-mail,Gaim cant chat,Even a network activity is not shown in the system moniter.I even tried tha firefox ipv6 trick,but waz no use.Can anybody help me??????????????????????

You may need to open /etc/resolv.conf and enter your servers with the appropriate IP addresses:

nameserver xxx.xx.xx.xxx
nameserver xxx.xx.xx.xxx

---

### Post by zxee on 2006-08-16
Also check out the link in my sig for help creating a dial up connection.
What version of ubuntu are you using? 6.06.1 has some bug fixes and if you use the sudo pppconfig command and set up your modem and provider correctly it should just work.

---

### Post by thilina on 2006-08-18
You may need to open /etc/resolv.conf and enter your servers with the appropriate IP addresses:

nameserver xxx.xx.xx.xxx
nameserver xxx.xx.xx.xxx

I am using a dial up connection.No Ip address is given to me.
I dial the number #777

---

### Post by thilina on 2006-08-18
To ZXEE

Wat is the url for your site??

---

### Post by Dana on 2006-08-18
Check with your ISP for the DNS used for your dial-up connection.

I use dial-up as well. But my ISP connection via dial-up is through one of two DNS. When I forgot to put them in my resolv.conf after setting up wvdial, my modem dialed out, made the connection with the ISP modem farm... and then just sat there until it timed out. No ability to do anything via the internet, because I wasn't on the internet. It sure seems as if yours is a similar situation. But hey, I've been wrong many times before. What's one more time.

Take care. Dana

> I am using a dial up connection.No Ip address is given to me.
I dial the number #777

---

### Post by mszl_1 on 2006-12-19
i just installed ubuntu ce and configured my dail up moden via kppp. i tried to configure the network settings but it fails to save the settings after i got the modem activated. rather frustrating since i get so far as activating the modem but as soon as i close the window it deactivates the modem?????!!!!! any ideas to keep the settings once the activation is complete?
thanx:confused:

---

