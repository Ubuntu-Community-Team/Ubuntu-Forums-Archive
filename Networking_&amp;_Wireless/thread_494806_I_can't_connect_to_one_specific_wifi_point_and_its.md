---
title: "I can't connect to one specific wifi point and its the one i own."
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by Death_Sargent on 2007-07-07
I live in a community covered in current so whever i use network admin (gnome) i get a good list of wifi spots

well i was living else where for a week using a different wifi spot. 

when i return home i go to network admin to alter my settings and low and behold my network is not listed. 

reboot not listed. 

manually enter it not usable. 

suddenly i can't connect to my home network. 

other things i had with me such as my psp and ps3 connected just fine. 

yes my network is encrypted but i can see other encrypted networks.

any help?

------------------edit--------------------

I am usingan atheros wireless built in latop card on my toshiba satellite p35 6929.

it worked in edgy and in feisty but recently stopped working (not using gusty).

-----resolution-----
the firmware on the router was bad and i needed to edit my firestarter settings.

---

### Post by Death_Sargent on 2007-07-07
**push**

seriously come on i need help

---

### Post by Death_Sargent on 2007-07-09
**push**

anybody

---

### Post by Death_Sargent on 2007-07-09
come on im stumpted. i have no way to figure this out please help

---

### Post by t4thfavor on 2007-07-09
get rid of network-manager, and install wicd. 

Seems like I hear this same post alot. 


sudo apt-get remove network-manager; sudo apt-get install wicd;

DejaVu?

---

### Post by stchman on 2007-07-09
> **t4thfavor said:**
> get rid of network-manager, and install wicd. 

Seems like I hear this same post alot. 


sudo apt-get remove network-manager; sudo apt-get install wicd;

DejaVu?

Are there any reviews/howtos on this wicd?

Thanks

---

### Post by imdano on 2007-07-09
The official site is here [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

There's an FAQ there that basically covers everything you normally need for installation, and the forums have a lot of good info as well.  Not sure of any reviews, aside from people on these forums saying it worked/didn't work (though it usually works!) for them.

---

### Post by stchman on 2007-07-09
> **imdano said:**
> The official site is here [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

There's an FAQ there that basically covers everything you normally need for installation, and the forums have a lot of good info as well.  Not sure of any reviews, aside from people on these forums saying it worked/didn't work (though it usually works!) for them.

They have a .deb to download, is that usable by Ubuntu?

---

### Post by imdano on 2007-07-09
Yes, wicd is designed specifically for Ubuntu.  Just make sure you uninstall network-manager before running the installer.

---

### Post by fredj on 2007-07-10
I think network manager would work. Click on the network icon in the system tray it will show the
list of available networks. Then choose 'Connect to Other Wireless Network' from the menu below the 
list and enter the ESSID of your network.

---

### Post by Death_Sargent on 2007-07-10
wicd is great but it still des not solve my problem even when i manually enter my ssid which i already tried thanks anyway fredj.

please this is going to be a real problem very soon and i need it solved.

---

### Post by kevdog on 2007-07-10
Lets just see something

Can your card even see your own network??
iwlist scan

---

### Post by Death_Sargent on 2007-07-10
actually i found there was new firmware for my network so now i can connect to it via wicd.

new problem i can't gain internet connectivity or atleast not with wicd.

nor can i connect with network-manager

---

### Post by Death_Sargent on 2007-07-10
just incase you read the edit please no that neither solutions work

---

### Post by imdano on 2007-07-10
You can connect but there's no internet?  Are you connecting via DHCP or are you giving it a static ip?

edit: Also, you don't have both network-manager and wicd installed do you?  They conflict with each other.

---

### Post by Death_Sargent on 2007-07-10
no just one or the other

and yes i am using DHCP

---

### Post by imdano on 2007-07-10
Are you getting an IP address from the router, or are you just able to see the network?  What type of encryption are you using?  And what kind of wireless card / driver are you using?

---

### Post by Death_Sargent on 2007-07-10
yes i am geting an ip adress, wep ascii 64bit, atheros with the madwifi driver "ath0"

---

### Post by imdano on 2007-07-10
Are you able to connect without any encryption?

edit: What are you using as the wpa supplicant driver as wicd?

---

### Post by Death_Sargent on 2007-07-10
your question makes very little sense aside the encryption part

I could not even connect sans wep

please explain how i did not answer your question when i said I was using the ath0 madwifi driver

---

### Post by imdano on 2007-07-10
Should have read "What are you using as the wpa supplicant driver IN wicd?", sorry.  As in, when you open the wicd gui and click preferences, what's selected in that dropdown menu.

---

### Post by Death_Sargent on 2007-07-10
ok well that is kinda moot now that i can connect vai wifi turns out it was working the whole time i just needed to reconfigure firestarter (firewall) to use my wifi as internet instead of my wired port

---

### Post by imdano on 2007-07-11
Oh, awesome.  Glad it's working.

---

