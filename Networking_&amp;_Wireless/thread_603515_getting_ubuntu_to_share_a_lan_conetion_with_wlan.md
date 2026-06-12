---
title: "getting ubuntu to share a lan conetion with wlan"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by Kzap333 on 2007-11-05
I have now got my brother Ubuntu (on his HP talbet) and he is pluged (though a lan cable) into out livebox (the wireless on out livebox does now work so)
I need to get his computer to share the internet that is pluged in though the lan over a wireless network. One thing I noticed is I can't get Ubuntu to connect to both LAN and wireless at the same time.
Do I have to download a new aplication or something to do this?

I need to get this done as soon as posible and prebly without any terminal code to me the Ubuntu tag line it "Just Works" means you don't need to load up a terminal just to share a LAN connection.
At the moment Ubuntu is turning out to be a hell of a lot for complex than it fist seem, it's ok but I would have preferd it if it jsut told the troth insteed of saying it 'Just Works'' like it does.

Anyway I don't mind doing a bit of teminal but I need to know what to put in.
Also I can only go online at school ('casue I 'ant got internet at home 'cause of this problem) and I only have short amounts of time on my brothers computer becasue it' his.

Anyway thanks for the help.

---

### Post by az on 2007-11-05
So, as I can understand, the internet goes from the outside world, to your livebox, through a cable into the HP tablet, and you would like the HP tablet to share this connection via wireless?  So the tablet has a wireless device?

I tried to do this once at my father-in-law's house.  He was using windows XP at the time.  It was a complete nightmare.  I had to boot his computer into Ubuntu for it to actually work.

What you need to do is set up a wireless peer-to-peer (called ad-hoc) connection between the HP tablet and the other computer you want to access the internet.  You will also need to share the internet with that connection.  You can use Firestarter for that.

[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

---

### Post by Kzap333 on 2007-11-05
> **az said:**
> So, as I can understand, the internet goes from the outside world, to your livebox, through a cable into the HP tablet, and you would like the HP tablet to share this connection via wireless?  So the tablet has a wireless device?

I tried to do this once at my father-in-law's house.  He was using windows XP at the time.  It was a complete nightmare.  I had to boot his computer into Ubuntu for it to actually work.

What you need to do is set up a wireless peer-to-peer (called ad-hoc) connection between the HP tablet and the other computer you want to access the internet.  You will also need to share the internet with that connection.  You can use Firestarter for that.

[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

Yep I think you got it.
Strange though I did it in XP really easily (I hate M$ but even so it was simple) all I did was create network bridge and bingo.
I'll try the link but when I click to create a wireless network it disconnects the wired network and visa-versa.

---

### Post by Kzap333 on 2007-11-05
> **az said:**
> So, as I can understand, the internet goes from the outside world, to your livebox, through a cable into the HP tablet, and you would like the HP tablet to share this connection via wireless?  So the tablet has a wireless device?

I tried to do this once at my father-in-law's house.  He was using windows XP at the time.  It was a complete nightmare.  I had to boot his computer into Ubuntu for it to actually work.

What you need to do is set up a wireless peer-to-peer (called ad-hoc) connection between the HP tablet and the other computer you want to access the internet.  You will also need to share the internet with that connection.  You can use Firestarter for that.

[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

MY GOD THAT LOOKS COMPLEX!
Is there no easier way all I want to do is share an internet connection and it's about a page of commands.

---

