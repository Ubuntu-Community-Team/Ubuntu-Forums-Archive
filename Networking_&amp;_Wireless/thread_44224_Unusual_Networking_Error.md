---
title: "Unusual Networking Error"
date: 2005-06-25
forum: Networking &amp; Wireless
---

### Post by deat on 2005-06-25
I slowly ceased use of Ubuntu because of a rather queer networking error.

Seems that ever since the day I installed Ubuntu, Ubuntu has had trouble connecting to my network. The thing is, I know it finds a connection, because it connects to the website where it gets the date and time just fine. But it won't load any internet page, the weather ticker doesn't load, and GAIM doesn't work either. So there goes the main use of Ubuntu for me.

Then, to make things worse, when I try logging back into Windows, Windows incounters the same problem. It won't load pages, Trillian will only connect to YIM and AIM (MSM for some reason will never connect after using Ubuntu). So in order to fix this, I stay on Windows and reset my router, which is a hassle because I have to keep running around undoing and redoing cables.

Any help to get this user back on Ubuntu would be enough to make me idolize you.

---

### Post by Lunde on 2005-06-25
[QUOTE=deat]I slowly ceased use of Ubuntu because of a rather queer networking error.

Seems that ever since the day I installed Ubuntu, Ubuntu has had trouble connecting to my network. The thing is, I know it finds a connection, because it connects to the website where it gets the date and time just fine. But it won't load any internet page, the weather ticker doesn't load, and GAIM doesn't work either. So there goes the main use of Ubuntu for me.

Then, to make things worse, when I try logging back into Windows, Windows incounters the same problem. It won't load pages, Trillian will only connect to YIM and AIM (MSM for some reason will never connect after using Ubuntu). So in order to fix this, I stay on Windows and reset my router, which is a hassle because I have to keep running around undoing and redoing cables.

Any help to get this user back on Ubuntu would be enough to make me idolize you.[/QUOTE]
 Can you also post the details of the network card, maybe it needs special drivers. 

Goto your terminal and type:

$ ifconfig 

..and post the output here

---

### Post by deat on 2005-06-25
[QUOTE=Lunde]Can you also post the details of the network card, maybe it needs special drivers. 

Goto your terminal and type:

$ ifconfig 

..and post the output here[/QUOTE]
 See, it does give me a connection, but sporadically. I don't know what I did to keep the connection up, but it did work various times before.

---

### Post by janrinok on 2005-06-25
Deat
Nobody can help you if you do not provide the information that they need.  We know that the network card works 'sometimes' but we are trying to help find out why it doesn't work all of the time.  Please provide the information asked for by Lunde.  Can you be more specific with the problem.  Not wishing to insult you, but do you know how to use 'ping'? If so, when you are connected, can you 'ping' your router, another website or whatever?  Are you setting your card's IP manually or are you using DHCP?  If you are not sure, then just say so.  HTH Jan.

---

### Post by alastair on 2005-06-25
Maybe the problem is elsewhere but your PC.

But :

a) explain your network configuration (h/w, cabling/wireless, topology etc.). Static, DHCP? etc.
b) ifconfig -a
c) route -n

and have a look at the messages printed in /var/log/syslog (especially during/after problems).

---

