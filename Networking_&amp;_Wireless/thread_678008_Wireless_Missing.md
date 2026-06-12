---
title: "Wireless Missing?"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by Locutus_of_Borg on 2008-01-25
I've been trying to get Ubuntu running on my wife's computer. I had to use an alternate install cd, then edit the xorg.conf to even display anything.  Now I am trying to get her wireless working.  Previously it just wouldn't connect but showed that there was at least a wireless device.  An lspci later I find her card is a Broadcom Corproration Dell Wireless 1390 WLAN Mini-PCI Card.  I followed all directions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/1390") got no errors on any commands, but now the wireless device doesn't even appear.

iwlist scanning gives this output:
```
[CODE]lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```[/CODE]

and nothing else.  

network manager no longer even lists wireless, and network under system > administration, no longer lists wireless either.

any ideas?
thanks.

---

### Post by pytheas22 on 2008-01-25
are you sure the wireless is up?  in other words, did you do

```
sudo ifconfig wlan0 up
```

---

### Post by Locutus_of_Borg on 2008-01-25
i have not tried that actually.  That would keep the network applet and network settings from even listing a wireless device though?

I will give it a try when I get back to her computer this evening though. 

thanks

---

### Post by johnydoe666 on 2008-01-25
another method of installing a broadcom card, is by using the restriced drivers manager. this almost always configures your card correctly.

also, to see if the card is even there, use
```
ifconfig -a
```

---

### Post by Locutus_of_Borg on 2008-01-25
the only thing listed under restricted drivers was the graphics card...which will not enable..

i will try ifconfig -a tonight, as well

though i know there is a card as it works in windows and shows up when i run lspci

---

### Post by mojaam on 2008-01-27
I have the same problem on a dell inspiron 1501, kubuntu 7.04. I tried that same guide, It's frustrating! Might have to give up and take it to somebody with much greater linux knowledge than I myself.

---

### Post by Locutus_of_Borg on 2008-01-30
i realized a little while ago that i have to load the ndiswrapper module before it will recognize my wireless

edit the /etc/modules file and add ndiswrapper at the end, then it will load at boot automatically

---

