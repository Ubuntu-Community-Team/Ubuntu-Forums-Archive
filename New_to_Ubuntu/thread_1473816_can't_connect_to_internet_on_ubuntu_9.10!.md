---
title: "can't connect to internet on ubuntu 9.10!"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by roubman on 2010-05-05
[COLOR=black][FONT=Verdana]I am new to ubuntu and don't know much about how to fix my problems. When I started to use ubuntu 9.10 I found out that I couldn't connect to the internet which was strange because I could connect perfectly before on Windows. So I searched on the internet how to connect to linux (my network card which is netgears WN121T). So from a couple of websites like [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][[COLOR=#0000ff]https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html[/COLOR]]("https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html")[/FONT][/COLOR][COLOR=black][FONT=Verdana] and[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I am told to install the ndiswrapper and ndisgtk. So I do what they tell me to (I got them off the linux Iso CD through synaptic package manager) and also find and download the .inf and .sys files for my driver WN121T which I put into a folder until needed. I had no other drivers on my computer. I then pasted the inf. and sys. file intothe ndiswrapper. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I then went into **[FONT=Verdana]System | Administration | Windows[/FONT]** and it said that it could not see if hardware was present. Once I cilck ok on the window it showed my driver and said that the hardware was present. If I click configure network it said it could not find a network configuration tool.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Later I went to **[FONT=Verdana]System l Preferences l Network Connections.[/FONT]** I went to my connection (Wireless connection), and authenticated myself. I named it in the SSID section, the Mode was Infrastructure and I didn't include the BSSID or MAC address. I ignored the IPv6 settings. In the IPv4 settings, I already have tried both the Automatic (DHCP)(without DHCP client ID)and Manual Methods. (my security is WPA & WPA2 Personal). I then applied the changes and my computer showed the network as Availible but it wouldn't connect![/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Help me please and give me tips on how to fix this!! [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]If I left out any information you may need to know ask please!! [/FONT][/COLOR]

---

### Post by nhasian on 2010-05-05
just out of curiosity, can you download and boot from the Ubuntu 10.04 LiveCD (or usb-thumbdrive if you prefer) to see if your network adaptor will work out of the box?

---

### Post by roubman on 2010-05-05
I think you can trial first and see what would happen without any changes to your computer. Also I heard you can make a virtual bubble in which you can use linux alongside with windows. I should have done one of these I guess (but I didn't).

---

### Post by spiky001 on 2010-05-05
I take it you can connect with a wired connection if so make sure you have updated 1st

---

### Post by Michl on 2010-05-05
Yes, try Lucid live first.  If that doesn't solve
the problem, use the command prompt or gtkwifi.

Also, for what it is worth, I ran into many
instabilities in 9.10.  9.04 is a very stable
distro.  I would go with either 9.04 or 10.04.

---

### Post by roubman on 2010-05-05
> **spiky001 said:**
> I take it you can connect with a wired connection if so make sure you have updated 1st
 
 
No I have no connection what-so-ever with wired, mobile broadband or others. In wireless it shows that the network is availible yet I can't connect for some reason:mad:.

---

### Post by spiky001 on 2010-05-05
do you have an ethonet cable you can try

---

### Post by roubman on 2010-05-05
> **spiky001 said:**
> do you have an ethonet cable you can try
 
 
do you mean an ethernet cable?
[[COLOR=#2200cc][/COLOR]]("http://www.google.ca/search?hl=en&ei=UOHhS9XaGabYMPWN5f8C&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CBIQBSgA&q=ethernet+cable&spell=1")

---

### Post by spiky001 on 2010-05-05
yea sorry sausage fingers lol

---

### Post by roubman on 2010-05-05
No I can't my router is to far away to reach with an ethernet cable. (im two floors above it!)

---

### Post by roubman on 2010-05-05
The strange thing is that it shows the network, but won't connect to it. (its listed as availible)

---

### Post by spiky001 on 2010-05-05
ok you said you had mobile broadband why dose this not work? 

It is better to get net connection to update as it will cause lots of problems trying to do it by transferring files or drivers any other way

---

### Post by roubman on 2010-05-05
> **roubman said:**
> No I have no connection what-so-ever with wired,**_ mobile broadband_** or others. In wireless it shows that the network is availible yet I can't connect for some reason:mad:.
  **_:lolflag:_**

---

### Post by roubman on 2010-05-05
Do you think in IPv4 settings Autmoatic (DHCP) doesn't work because I didn't put in the DHCP Client ID? Do you have to have the client ID in order to connect?:?:

---

### Post by roubman on 2010-05-05
bye the way thanks for helping!!!

---

### Post by spiky001 on 2010-05-05
ok if you try to connect with wireless dose it give you the box for wpa password?

---

### Post by roubman on 2010-05-05
when editing the connection, each time I go to it in security (I have WPA & WPA2 Personal) I have to put in the password again. (the box Connect automaticly is checked-just to tell you). If I go to the availible networks and try to connect from there it immediatly says Wireless Network Disconnected - You are now offline.

---

### Post by roubman on 2010-05-05
:?::?:are you still there?:-|:-k

---

### Post by spiky001 on 2010-05-06
are you sure that you are putting in the correct wpa key? are you sure it's not a wep key?

---

### Post by roubman on 2010-05-07
yes im sure. I switched to ubuntu 10.4 and the problem is still there. It is exactly the same as on 9.10!!

---

### Post by spiky001 on 2010-05-07
on the router I connect to there is a wpa connection and a wep connection have you tried both of them do you have the wep key try setting it up via that, they have different network names i.e bt blah is wep     bt wahoo is wpa

---

### Post by roubman on 2010-05-08
no i don't have a wep connection. My security on my router is fixed to wpa and wpa2 personal. It has a lot of users so i can't change it.

---

### Post by spiky001 on 2010-05-08
have a look here it is in Italian but it can be translated
[http://translate.google.co.uk/translate?hl=en&sl=it&u=http://www.wilky.it/wordpress/2009/01/20/wpawpa2-con-ubuntu-810/&ei=l6_lS9C7MaG80gSh6PC0AQ&sa=X&oi=translate&ct=result&resnum=6&ved=0CDMQ7gEwBTgU&prev=/search%3Fq%3Dnetgears%2BWN121T%2Bwill%2Bnot%2Bconnect%2Bto%2Bwpa%2Bubuntu%26start%3D20%26hl%3Den%26sa%3DN](http://translate.google.co.uk/translate?hl=en&sl=it&u=http://www.wilky.it/wordpress/2009/01/20/wpawpa2-con-ubuntu-810/&ei=l6_lS9C7MaG80gSh6PC0AQ&sa=X&oi=translate&ct=result&resnum=6&ved=0CDMQ7gEwBTgU&prev=/search%3Fq%3Dnetgears%2BWN121T%2Bwill%2Bnot%2Bconnect%2Bto%2Bwpa%2Bubuntu%26start%3D20%26hl%3Den%26sa%3DN)

---

### Post by roubman on 2010-05-08
i will try this
hope it works

---

### Post by roubman on 2010-05-09
Thank you for trying... I bought a new card and I connected automatically. Im so happy. I really appreciated your efforts. So again Thank you!!!!

---

### Post by roubman on 2010-05-09
ummm...

---

