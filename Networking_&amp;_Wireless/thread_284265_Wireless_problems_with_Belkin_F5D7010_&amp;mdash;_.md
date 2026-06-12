---
title: "Wireless problems with Belkin F5D7010 &amp;mdash; Rt2500"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by squirmster on 2006-10-25
I am baffled and confused. I've been trying to get my Belkin wireless card to work for a while now. It is the Rt2500 chip model.

I tried to follow the guide here: ([http://www.ubuntuforums.org/showthread.php?t=272813&highlight=novices](http://www.ubuntuforums.org/showthread.php?t=272813&highlight=novices))
But couldn't get it to work. In an effort to start from scratch I reinstalled ubuntu and found another this one ([https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)) which says that my pcmcia card should be PNP. The device comes up as ra0 and the card is recognised when I type in iwconfig, ifconfig and lspci. So I don't think I need Ndiswrapper.

However when I plug in my card a light flashes once and disappears. After that no more lights at all.

I have gone to System > Administration > Networking to set up the wireless card ra0, activated it, deactivated the ethernet.

I found this thread ([http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=863&highlight=f5d7010](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=863&highlight=f5d7010)) which seems to have a similar problem to mine and the solution here is to "up the interface beforehand" However, being new to linux I have no idea what they are talking about. I tried iwlist ra0 scan and got 13 different connections but they seem to have no signal strength (if thats what Quality:0/100 means). Seems a little odd to not get any sig. strength at all from 13 different networks.

I found a command on another thread which was ifup, when i typed this in (sudo ifup ra0) I was told that it was already configured.

I need help as I am fast running out of ideas. Actually make that I have run out of ideas. I don't want to go back to windows but I might have to.

Thanks

---

### Post by squirmster on 2006-10-25
I have just gotten home and am tried out 'iwlist ra0 scan' and it found my home network. This still has a 0/100 quality rating even though the pcmcia card is about 1.5 metres away from the router.

set up the card in sys > admin > networking, put in the proper password and it didn't work.

The card seems to be registering activity even though the lights aren't on which indicates that it is almost working. :D Please could someone help me out. :-?  I think it is only one step away from actually working. I just cant see it.

---

### Post by squirmster on 2006-10-25
Right. Problem is now fixed. I set the home wireless to be completely open - no passwords or anything and plugged in the card.   Did sys > admin > Networks and changed the settings to match the wireless connection and the card worked.

So 2 things have been learnt by me: 
1. the lights on the card only come on when it is connected to a network.
2. Don't overcomplicate things. Find out if the driver is installed as part of ubuntu and if it is go from there and sort out the basics before trying to fiddle with things like ndiswrapper when I don't know what I am doing.
:)

---

