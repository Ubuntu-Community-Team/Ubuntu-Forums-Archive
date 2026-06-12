---
title: "Intrepid: E220 3g wireless modem problem"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by InsaneO on 2008-11-03
Ubuntu (8.10) is able to detect my E220 USB wireless modem but the connection speed is rather slow.

I am able to get a better connection with gnome-ppp. However, I noticed when it auto-detects the modem settings, it sets the baud to only 9600 (this also happens with wvdialconf). So I manualy increase it to get a good connection.

Is there a way to  increase the baud-rate with the NetworkManager Applet 0.7.0.?

---

### Post by xtremesupremacy3 on 2008-11-21
I too am having trouble.

After having upgraded to 8.10 from 8.04 all seemed well.
I used to get the connect over and done with in no time, and the light would be constant blue (not sure what speed it is, but good).

Then last week I tried to connect and got disconnected immediately afterwards, this went on for a number of hours.
Then night came and I was able to get on again, phew, however...now it connects and sticks on a green light (GPRS). Anyone tell you thats still good?! nooooo!
Anyway, checked out the settings on NM and I can see that the modem reconnects regularly :confused:
Is there no way that you can change the prefferation of your speed like in Windows and I believe mac also?

Oh and one more thing, I decided to check out my wvdial and it was empty with only default settings (also empty), maybe I don't even need to look at this but I kindof expect you do.

I am using a Telfort E220 from the Netherlands.

Any help would be appreciated guys, because if this carries on I will use the usb cable attached to it to wrap around the Telfort guys throat:lolflag:

Ciao!

---

### Post by wiebeest on 2009-02-02
> **xtremesupremacy3 said:**
> I too am having trouble....

I am using a Telfort E220 from the Netherlands.

Same problems not being able to connect to the interet through my usb modem (t-mobile in my case). When booting to Windows XP it works flawlessly. 

But understandably I did not install Ubuntu Ibex through Wubi in order to still have to use Windows for internet. Since this is on my work laptop and I need the interet for e-mail on my remote desktop. 

What solved it for me is the sollution from ToineM found here:
[http://ubuntuforums.org/showpost.php?p=6357229&postcount=9]("http://ubuntuforums.org/showpost.php?p=6357229&postcount=9")
In short: > The solution for Dummies: Disable the PIN on youre SIMcard:
...
After removing the pin code from the sim card the modem is hot plugable! in ubuntu 8.10

That solved the not connecting problem for me.
Hope that you find this sollution useful too.

Sincere greetings,

Wiebeest

---

