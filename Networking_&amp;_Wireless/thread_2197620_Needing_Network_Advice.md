---
title: "Needing Network Advice"
date: 2014-01-04
forum: Networking &amp; Wireless
---

### Post by dave80 on 2014-01-04
[SIZE=2]I’m new to Linux and Ubuntu.  I have a couple of Windows XP boxes (Ethernet), a MacPro (Ethernet), a Ubuntu box (Ethernet) and a MacBook Pro (Apple’s Airport Wireless).[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]I need to network all of my boxes and I’m looking for advice on which Linux (Ubuntu) network I should install.  Microsoft did make it easy to create a MSHOME peer-to-peer.  If possible, I would like to access any box from any other box including any files and directories.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]From what I have read, Samba seems easiest to install.  However, I would really like some guidance that draws a balance between ease of administration & installation versus functionality.  Can someone give me some direction on which network I should install, and point me to some links that will give me installation instructions using fairly layman language?  I’m comfortable using terminal commands.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]Now that Microsoft has decided to stop support on XP in April, and my recent total dissatisfaction with Apple, I see no alternative be to embrace Ubuntu as a total replacement.  I also don’t see myself overspending on Apple hardware since it appears to me that Ubuntu will do everything that my Mac’s will do on a box that cost’s 75% less, not to mention software costs that don't even compare.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]Security is not a major concern since this is an in-home network, and will remain a home network until I’m comfortable enough with my knowledge level to deploy it to my business.  I don’t need a network that provides DOD level security at the cost of being so sophisticated that I need to get a Doctorate from MIT just to install it.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]Thanks very much.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]Dave[/SIZE]

---

### Post by Morbius1 on 2014-01-04
Well, the only thing on the surface that ties all those together is Samba but you don't necessarily have to use it exclusively.  For example:

*** Liunx - Windows you are pretty much stuck with Samba. Creating a Samba share in Ubuntu is as simple as creating a Windows "simple share":

Open Nautilus ( File Manager ) > right click a folder you own > select "sharing options" > click on some boxes and you created a share. It will even install the correct version of samba for you automatically if it's not installed already.

*** But Ubuntu can access an afp sharepoint natively so you don't necessarily have to create a samba share in OSX ( which is good because there seems to be some quirks in the samba server in Maverick ). And just because you access the MacBook through afp doesn't mean the MacBook can't access the Linux box through Samba ( which thankfully still works like it used to ).

*** You will likely get a number of posts that state that Samba is only for Windows and NFS is the way to go. I'll let them make that argument as I haven't used nfs is a generation. 

I should point out though that Apple gave Linux a gift ( actually 2 - the other is CUPS ) in the form of Avahi ( what apple calls Bonjour ) and with that host discovery between Linux boxes and between Linux and OSX boxes can become as simple as 2 macs finding each other. At that point you are running Samba without any Windows components at all.

---

