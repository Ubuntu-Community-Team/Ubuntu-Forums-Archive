---
title: "Web Pages Not Loading  (Most)"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by u2rcrazy on 2010-05-31
Hello:KS

I have a dual boot Toshiba Satellite running Windows XP and Ubuntu 10.04.  When surfing the internet I use FireFox 3.6 on both OS's.  I'm able to surf with no problems on XP, but most of the websites I attempt to visit don't load or may partially load.  The only pages that load fully are Google's Ubuntu 10.04 page and a Minx (Linux) forum page.  Whenever I click a link off of this Google page or try to load other addresses/pages, they don't load completely or at all.  

Most of the time when I go to a site, I see the: 

[LIST=1]
[*]progress bar loading between a 1/3 to 2/3 of the way
[*]the title of the page displayed in the Firefox tab
[*]a blank page most of the time or sometimes some links
[/LIST]
I later went to Ping these same sites that wouldn't load, and they all received 100% success.  This is when I don't understand.

Here's some clues:

[LIST]
[*]Problem Downloading w/ Update Manager
Being that I was experiencing this problem, I went to Update Manager to download the latest updates.  I clicked Install and the download maintained an average of 408kbs, then suddenly the the speed and time estimate changed to unknown.  I canceled the download and clicked install again which started where the last attempt left off and the same thing happened.  I kept reinitiating the download until all available resources were downloaded.  When I restarted Ubuntu these updates didn't fix the webpages not loading, but may serve a a clue as to why I'm not able to surf the web freely.
[*]Not able to load my cable modem's webpage:
Can't load my Motorola Surfboard (Model Name: SBV5222) web page at 192.168.100.1 like I have been able to previously
[/LIST]
Thanks in advance for your help!!  :P

---

### Post by lovinglinux on 2010-05-31
Normally I would recommend disabling ipv6, but it seems your network connection is being dropped, so the browser or the update manager are unable to finish downloading.

Anyway, disabling ipv6 won't hurt. See the fifth item on [this list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html).

Also check out [these threads](http://www.google.com/search?q=connection+drop+router+site%3Aubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0).

---

### Post by Flippons on 2010-07-04
I've had a similar problem with 9.04, but I'll give disabling IPv6 a try.

---

### Post by Flippons on 2010-07-05
Actually, I just tried disabling IPv6 now, and it didn't work. Any other suggestions?

---

### Post by Open4D on 2010-07-17
I too have a similar problem, trying to get Ubuntu running on an acquaintance's laptop.  (Also a Toshiba.)  Disabling IPv6 doesn't work for me either.

So far, the only workaround I have managed is to plug in an external (USB) wireless adapter.  But I still want to get the internal one to work, so I might try [https://help.ubuntu.com/community/WirelessTroubleshootingProcedure/](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure/)

Did you fix your problems, "u2rcrazy" and  "Flippons"?

---

### Post by bkratz on 2010-07-17
Found this in the bug listing, you both will probably be interested.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/544485](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/544485)

---

### Post by techunit on 2010-07-17
I have had this problem before... What I have to do was reinstall the Broadcom drivers for my wireless card and install Broadcom sta driver.. hope this helps.

---

### Post by pradeepadapa on 2010-07-18
hello,

I have found a solution to this issue, I had the same issue with the wireless connection, that though the network says that it is connected to the wireless router, I didn't have the internet access.

here is the solution which I applied:

Go to System -> Administration -> synaptic package manager 

In the search field type "network" (without the double quotes) and click on network-manager and network-manager-gnome and mark for uninstallation.

Uninstall this network manager.

Then again in the search field type "wicd" (without the double quotes), select the following for installation:

wicd
wicd-daemon

then install the above packages and restart the system.

Now you can just click on the wicd network manager at the place where the previous network manager used to be and click on it to see what wireless networks are available, click on your wireless network, give the network key and voila.. it is connected and now you can access the internet...

Hope this helps guys/gals..

---

### Post by Open4D on 2010-07-18
[COLOR=Blue]**Techunit **and** bkratz**[/COLOR] - thanks.  Your posts made me stop looking for a general fix (like disabling IPv6) and start focussing on the specific wireless device.

In this case it is the Atheros AR2413, and I found 
            [bug 568090]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568090"), whose description includes a workaround.

So I'm happy.  :)

And because I'm a good boy, I also re-enabled IPv6 ...

[B]
[COLOR=Blue]Pradeepadapa[/COLOR] [/B] - thank you for your suggestion.  My symptoms were very similar to **u2rcrazy**'s (e.g. ping worked) so I wouldn't quite say that "I didn't have the internet access".  That's not to say your suggested fix wouldn't work; it sounds quite feasible, but I came across a more specific fix first (bug 568090).

[COLOR=Blue]**Flippons **and** u2rcrazy**[/COLOR] - does either of you two have the Atheros AR2413?

---

### Post by bkratz on 2010-07-18
Glad you found your answer!

---

### Post by pradeepadapa on 2010-07-19
glad that we could be of help open4D.

---

### Post by u2rcrazy on 2010-07-19
[Open4D]("http://ubuntuforums.org/member.php?u=1114234"),

[**My wireless device is a Realtek  RTL8192se driver**]("http://ubuntuforums.org/showthread.php?t=1339877")

Thanks everybody for your help!!


[pradeepadapa]("http://ubuntuforums.org/member.php?u=82571"),

I did what you suggested and everything went as described until I went  to connect.  For some reason, it couldn't connect with the WPA  Password.  Do you have any suggestions?

---

### Post by pradeepadapa on 2010-07-19
Hello u2crazy,

what is the wireless router/modem you have? 

I have one motorola sbg901 wireless cable modem and an linsys router, I was able to connect to linksys router without any issues, however I am also having the same issue as you have regarding the connection to my motorola modem, when I give the correct key, it is saying bad password. 

I think this has to do with the modem drivers for linux, because I have to insert the modem's cd-rom into the laptop in Windows OS to configure the wireless. 

However I am unable to find the drivers for Linux OS for the cable modem..

Even I am looking for a solution to this issue, as soon as I get the solution I will put it on a thread u2crazy.

Any help regarding this issue is most welcome people..

---

### Post by jpl888 on 2010-07-19
It also sounds like a clampmss problem, but I suppose if it works in other oses then it can't be that.

---

### Post by pradeepadapa on 2010-07-19
No, its not the issue jpl888, we are able to connect to the modem in other operating systems using the modem CD , however we are unable to connect to it in Linux since the modem didn't come with driver software for Linux OS, though it says that the modem supports linux OS. everything is going on fine till we connect to the modem and give the network password and it says bad password, connection failure.

---

### Post by u2rcrazy on 2010-07-19
[pradeepadapa]("http://ubuntuforums.org/member.php?u=82571"),

Here is my Cable Modem/Telephone information.  It is a Motorola SURFboard:

Model Name: SBV5222
	  Firmware Version: 22.0.19-SCM-06
Vendor Name: Motorola
MTA Firmware name: SBV5222-22.0.19-SCM-06-SHPC
 	  Boot Version: 8.4.5
	  Hardware Version: 1
      BCMA Software Version: 00.00
	  MIB Version: II
	  GUI Version: 1.0
	  VxWorks Version: 5.4
	  Firmware Build Time: Dec  2 2008 22:11:42

Christian

---

### Post by pradeepadapa on 2010-07-22
yo buddy, finally I was able to connect to my wireless modem successfully..

here is what I did:

Go to synaptic manager and uninstall wicd and then install the normal network manager.

Restart the system.

then click on the network manager and you will find your network, if you didnt find the network (like in my case) create a new network with your modem/router's SSID name and the encryption and its network key...

Violaaaaaaa the network is connected...

Hope this helps you too u2crazy ...

---

