---
title: "Feisty, Wifi, WPA --&gt; which network card/stick to buy?"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by SkyScrap on 2007-06-08
Hi,

after hours and days of wasted time trying to get either of my two USB WLAN sticks working (one with a RT73 chip, the other one with a SIS), I'm ready to invest into new hardware.

This is a Tower PC, so also PCI cards are ok. My only requirements are that it should work with Feisty (out of the box, if possible), support WPA and should use the network manager for configuraiton.

What shall I buy? I'f browsed the [List of supported cards]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), but it seems that each and every card has some problems of it's own.

What about the D-Link WDA-1320. That seems to work ok, based on the [discussions]("http://ubuntuforums.org/archive/index.php/t-211780.html"). 

A "purchase recommandation" wiki page would be a nice thing, IMHO.

---

### Post by almark on 2007-06-08
I've got a 3com 3crusb10075 with a zydas chipse and zd1211rw diiver, works fine for me.  I followed the instructions here [http://ubuntuforums.org/archive/index.php/t-288753.html](http://ubuntuforums.org/archive/index.php/t-288753.html) allthough I didn't have to compile stuff myself. If you're using network-manager better un-install that first  because it doesn't work very well with the 3com...

Regards
Mark

---

### Post by SkyScrap on 2007-06-08
> **almark said:**
> I've got a 3com 3crusb10075 with a zydas chipse and zd1211rw diiver, works fine for me.  I followed the instructions here [http://ubuntuforums.org/archive/index.php/t-288753.html](http://ubuntuforums.org/archive/index.php/t-288753.html) allthough I didn't have to compile stuff myself. If you're using network-manager better un-install that first  because it doesn't work very well with the 3com...

Hi, thanks for the feedback. Good to know that this is working, but as I've written, I'm looking for the easiest possible solution, including network manager and WPA support. If I'm investing money I would like to get the most value out of it.

Is there even such a thing working in Feisty? I have my doubts at the moment.

---

### Post by SkyScrap on 2007-06-08
I've found a couple of reports in another thread, where it works, sometimes even out of the box:

[LIST]
[*]D-Link DWL-G650: [http://ubuntuforums.org/showthread.php?p=2744624&highlight=WPA#post2744624](http://ubuntuforums.org/showthread.php?p=2744624&highlight=WPA#post2744624)
[*]D-Link  DWL-650: [http://ubuntuforums.org/showthread.php?p=2657113&highlight=WPA#post2657113](http://ubuntuforums.org/showthread.php?p=2657113&highlight=WPA#post2657113)
[*]Linksys WPC5: [http://ubuntuforums.org/showthread.php?p=2721112&highlight=WPA#post2721112](http://ubuntuforums.org/showthread.php?p=2721112&highlight=WPA#post2721112)
[*]Belkin f5d 7050 v4: [http://ubuntuforums.org/showthread.php?p=2571869&highlight=WPA#post2571869](http://ubuntuforums.org/showthread.php?p=2571869&highlight=WPA#post2571869)
[*]Atheros MiniPCI: [http://ubuntuforums.org/showthread.php?p=2568602&highlight=WPA#post2568602](http://ubuntuforums.org/showthread.php?p=2568602&highlight=WPA#post2568602)
[*]Broadcom 4306: [http://ubuntuforums.org/showthread.php?p=2551766&highlight=WPA#post2551766](http://ubuntuforums.org/showthread.php?p=2551766&highlight=WPA#post2551766)
[*]D-Link DWL-G520: [http://ubuntuforums.org/showthread.php?p=2540178&highlight=WPA#post2540178](http://ubuntuforums.org/showthread.php?p=2540178&highlight=WPA#post2540178)
[/LIST]

I'll continue my research from here. As a tendency, the Atheros chipset and madwifi driver seem to work quite well.

---

### Post by SkyScrap on 2007-06-08
I'm kind of using this thread now for documenting my own research results. My PC doesn't have a PC-Card slot, unfortunatly, they seem to be well supported.

[LIST]
[*]PCMCIA
[LIST]
[*]D-Link DWL-G650
[*]D-Link DWL-650
[*]Linksys WPC5
[/LIST]
[*]USB
[LIST]
[*]Belkin f5d 7050 
[/LIST]
[*]PCI
[LIST]
[*]D-Link DWL-G520
[/LIST]
[*]Chipsets
[LIST]
[*]Broadcom 4306
[*]Atheros MiniPCI
[/LIST]
[/LIST]

---

### Post by SkyScrap on 2007-06-08
Another interesting source of information:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

This is proposing four more options for the PCI Interface:
[LIST]
[*]Belkin F5D7001
[*]Belkin F5D7000 v. 5100
[*]CompUsa RealTek 8185L
[*]D-Link WDA-1320
[/LIST]

---

### Post by SkyScrap on 2007-06-08
*Sigh* Just called my local PC dealer about the price of the D-Link WDA-1320, only to find out that this is not available at all in germany! How sick is that! So I guess I will be going with the DWL-G520 now. Let's see what kind of reports I find for that in the net.

---

### Post by SkyScrap on 2007-06-08
Ok, finally some decision seems to be dawning. Found another page on the same hunt:
[http://ubuntudemon.wordpress.com/2007/02/19/searching-for-wireless-pciusb-card-which-supports-wpa2/](http://ubuntudemon.wordpress.com/2007/02/19/searching-for-wireless-pciusb-card-which-supports-wpa2/)

First it seems that atheros chipset is a must. I've found two nice cards, which are in stock at my dealer, and suppsedly are supported quite well:
[LIST]
[*][D-Link DWL-G520]("http://madwifi.org/wiki/Compatibility/D-Link#DWL-G520")
[*][Netgear WG311T (which is WG311TGR in Germany, I suppose)]("http://madwifi.org/wiki/Compatibility/Netgear#WG311T")
[/LIST]

I'll keep you posted, maybe somebody is interested :)

---

### Post by sundial on 2007-06-08
I would like to add my 2 cents here.  I have 7.04 running nicely on my old laptop BUT i cannot get the WIFI card I have to work.  Cards are Linksys WCP 11 Ver 3 and WCP 11 Ver 4.  I also am looking for an OUT OF THE BOX solution however I must have a PCMICIA card solution.  

I checked out the NDISWRAPPER for my WPC 11 Ver 4 card but I am a new to Linux and everthing i read on installing this read like techno gibberish.

Without WiFi, the Ubuntu OS is not useful and I need to consider going back to Win2000, a place I do not want to be since Ubuntu runs so much faster on this old Laptop.

Can someone point me to a solution that I can deal with given my low level of Linux knowladge?

---

### Post by SkyScrap on 2007-06-08
> **sundial said:**
> I also am looking for an OUT OF THE BOX solution however I must have a PCMICIA card solution.  

As indicated in one of my previous posts, these cards seem to be working:
    * D-Link DWL-G650
    * D-Link DWL-650
    * Linksys WPC5

---

### Post by thor111 on 2007-06-08
--------------------------------------------------------------------------------

I found this article VERY helpful for a noob like me, and I used it to install my wireless card a few days ago. It steps through EACH process, and lets you know what you should see. BTW the TrendNet card I installed is working very well, and it was fairly cheap.

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Hope this helps.

---

### Post by sundial on 2007-06-08
Thanks for the note on the three PCMCIA cards that apparently work with 7.04.  I can get a DLink G650 and that, you think will work "Out of the Box" --  Have you tried it?

---

### Post by specv on 2007-06-08
> **SkyScrap said:**
> I've found a couple of reports in another thread, where it works, sometimes even out of the box:

I'll continue my research from here. As a tendency, the Atheros chipset and madwifi driver seem to work quite well.

thats what i use, from everything ive read and tried atheros is the way to go

the gigabyte one on ebay for like $30 works great

---

### Post by sundial on 2007-06-08
> **thor111 said:**
> --------------------------------------------------------------------------------

I found this article VERY helpful for a noob like me, and I used it to install my wireless card a few days ago. It steps through EACH process, and lets you know what you should see. BTW the TrendNet card I installed is working very well, and it was fairly cheap.

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Hope this helps.

Thanks for the response.  I took a look at the site listed above and still cannot seem to get the details right.  For one, i made a directory in /home called ndiswapper.  When i tried to copy the file to it, i found the folder was restricted and would not permit me to copy files into it.  So now these files are untarred and are sitting in a folder on my desktop.  I am stuck and can go no further.

Also, too often the directions are not complete for a new user.  Using crypto language in a statement just confuses a new person.  an example I saw earlier is "$ sudo do what ya gotta do" as if this is a linux command.   The same goes for using the ~ in place of a complete statement.
Crypto nonsense like this wastes hours of my time.

---

### Post by sundial on 2007-06-08
> **specv said:**
> thats what i use, from everything ive read and tried atheros is the way to go

the gigabyte one on ebay for like $30 works great

The one advertised on EBay has the "prism chipset" is this the same as the "atheros " chip set?

---

### Post by oxalá on 2007-06-08
> **sundial said:**
> Thanks for the response.  I took a look at the site listed above and still cannot seem to get the details right.  For one, i made a directory in /home called ndiswapper.  When i tried to copy the file to it, i found the folder was restricted and would not permit me to copy files into it.  So now these files are untarred and are sitting in a folder on my desktop.  I am stuck and can go no further.

Also, too often the directions are not complete for a new user.  Using crypto language in a statement just confuses a new person.  an example I saw earlier is "$ sudo do what ya gotta do" as if this is a linux command.   The same goes for using the ~ in place of a complete statement.
Crypto nonsense like this wastes hours of my time.

i'm trying to figure this stuff out too, but (sadly?) that tutorial was clearer than many i've seen so far.

---

### Post by sundial on 2007-06-08
If you can make any headway, please report it on this site.  Apparently there are many who have the same issues we have with 7.04.  The WiFi drivers are not working well and the OS is very picky about which chip set it will work with.  Its a real shame because it is such a nice OS in other regards

---

### Post by thor111 on 2007-06-08
I didn't have to download the ndiswrapper part since it came bundled with "Feisty".    Check out [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28internet%29%7C%28without%29%7C%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28internet%29%7C%28without%29%7C%28ndiswrapper%29)

[COLOR="Red"]2.3. Without Internet access
Without an Internet connection, you can still install ndiswrapper-utils from the Desktop CD. If you installed from that, the repository in which ndiswrapper-utils is found is on the CD, but not within the live session. You need to boot into your new Ubuntu installation and then reinsert the Desktop CD. You will be asked if you want to add the packages on the CD to your list of repositories. 

If you installed using the Dapper Alternate CD, those packages except ndisgtk are included on it. 

Put the CD into the drive, click System > Administration > Synaptic Package Manager and search for ndis. If you don't know how to install applications,  read this guide. [/COLOR]

---

### Post by SkyScrap on 2007-06-08
Success!!!! :biggrin:

I now bought the D-Link DWL-G520 (Rev. B4). Plugged it in, driver was loaded automatically. I selected my SSID in network manager, it asked me for the WPA key. WORKS :) 

Life can be so easy, when you buy the right hardware! How many sleepless nights could have been saved and were wasted. 

@sundial -- I have not tried it myself, but previously in this thread I linked experiences from other users, and they apparently were happy with it: 

> **SkyScrap said:**
> I've found a couple of reports in another thread, where it works, sometimes even out of the box:

[LIST]
[*]D-Link DWL-G650: [http://ubuntuforums.org/showthread.php?p=2744624&highlight=WPA#post2744624](http://ubuntuforums.org/showthread.php?p=2744624&highlight=WPA#post2744624)
[*]D-Link  DWL-650: [http://ubuntuforums.org/showthread.php?p=2657113&highlight=WPA#post2657113](http://ubuntuforums.org/showthread.php?p=2657113&highlight=WPA#post2657113)
[*]...
[/LIST]

---

### Post by sundial on 2007-06-08
> **thor111 said:**
> I didn't have to download the ndiswrapper part since it came bundled with "Feisty".    Check out [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28internet%29%7C%28without%29%7C%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28internet%29%7C%28without%29%7C%28ndiswrapper%29)

[COLOR="Red"]2.3. Without Internet access
Without an Internet connection, you can still install ndiswrapper-utils from the Desktop CD. If you installed from that, the repository in which ndiswrapper-utils is found is on the CD, but not within the live session. You need to boot into your new Ubuntu installation and then reinsert the Desktop CD. You will be asked if you want to add the packages on the CD to your list of repositories. 

If you installed using the Dapper Alternate CD, those packages except ndisgtk are included on it. 

Put the CD into the drive, click System > Administration > Synaptic Package Manager and search for ndis. If you don't know how to install applications,  read this guide. [/COLOR]

I tried to use the Distro disk as suggested.  I found the ndiswrapper packages on the disk and them when I tried to install them the installation failed.  

I am tempted to go but a DLink DWL G650 and try it but I fear that it too may not work on my system and then I am stuck with another PCMCIA.

---

### Post by SkyScrap on 2007-06-09
> **sundial said:**
> I am tempted to go but a DLink DWL G650 and try it but I fear that it too may not work on my system and then I am stuck with another PCMCIA.

Maybe you can take your laptop to the store and try it out there right away? Or trust the user reports here, it worked for me.

---

### Post by sundial on 2007-06-09
> **SkyScrap said:**
> Maybe you can take your laptop to the store and try it out there right away? Or trust the user reports here, it worked for me.

Thanks for the suggestion.  I ordered yesterday.  Worts case is I have another PCMCIA WiFi card to play with.

---

### Post by SkyScrap on 2007-06-11
> **sundial said:**
> Thanks for the suggestion.  I ordered yesterday.  Worts case is I have another PCMCIA WiFi card to play with.

Don't forget to post your results :)

---

