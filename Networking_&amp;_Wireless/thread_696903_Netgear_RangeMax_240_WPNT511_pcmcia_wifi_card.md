---
title: "Netgear RangeMax 240 WPNT511 pcmcia wifi card"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by Cha1n5aW on 2008-02-14
I just purchased this netgear WPNT511 pcmcia wireless adapter & I find out its not supported by Ubuntu gutsy 7.10.  I have another adapter I can use, but since I have netgear router & netgear range extender, I would very much like to be able to use my netgear pcmcia card.  Also the netgear card is vastly superior to my linksys card in every way.  Anyways, I would like to know how to install this card (if at all possible).  I am not very experienced with linux, but I do have a basic understanding of things.
Any support, links, or direction is greatly appreciated.

Thanks

- Shawn

---------------------------UPDATE----------------------------------------------------
Thanks, I figured it out myself.  I had to install the ndiswrapper-common, ndiswrapper-utils-1.9, and ndisgtk (frontend) from synaptics package manager.  Then since this card is native to windows (no drivers at netgear site), I had to download its chipset drivers (airgo_drivers.exe) from [http://www.laptopvideo2go.com/files/wlan/]("http://www.laptopvideo2go.com/files/wlan/") then used a windows box to extract the files from the downloaded archive, transferred them back to a folder on this system.  After that I simply ran the "windows wireless drivers" icon in my System menu (ndiswrapper frontend) loaded the "/whereIputit/airgo_drivers/airplus_drivers/Utility/Driver/tmimo3p.inf" driver .inf and viola, it all worked like a charm!  Not too shabby for a linux amatuer.
I hope this little tutorial helps others who are using the same/similar cards.  I imagine this process will work with most cards that have no linux drivers.  The card connects to my wireless G network here and works fine (wpa-psk), but not entirely sure about any additional functionality or features.

- Shawn

PS - to configure card I used this tutorial
[Kevdog's manual wifi how-to]("http://ubuntuforums.org/showthread.php?t=684495")

---

### Post by craigford on 2008-07-12
hey, i am having the same prob. u were having exactly! I also have the same wifi card as you...i used the link to the airgo.exe files-->downloaded all three airgonet tru mimo driver files...the airgonet ASUS client utility, the airgonet v1551 and the v1556 exe.'s as well....the problem ive run into, and i know this is going to sound dumb but im very new to linux as well, I cant figure out how to extract the inf. files from the exe. files...through a window as u described...what window/s...im stuck..ive tried to open with ever possible program/utility it will allow me to, but nothing works...there is no option to open it with windows...i hope you can help me...this is too frustrating for me to crack...

i am using ubuntu 8.04 LTS x86 version, thats all i know...thanx for any help!

---

