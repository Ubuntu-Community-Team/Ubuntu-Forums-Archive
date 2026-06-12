---
title: "Setting Up Wireless With Netgear WG111 and WG11T USB Dongle/ Adapter"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by dialgo on 2007-11-29
Right i've been struggling for the better part of two days now with my Netgear WG11T USB dongle. Finally i've figured out the process in which to get this device to work.
 
**First things first, for this to work you will need:**
1. Drivers for your WG11T, preferably the cd that came with the dongle, or the drivers from the website.
 
2.NDISWRAPPER (don't use the graphical interface that is NDISGTK, it tends to freeze up your system during this process.)
 
**Note**
DO NOT PLUG IN USB DONGLE TILL I TELL YOU TO!!!
 
Right so first things first, regardless of whether you have the cd drivers or the downloaded ones, you need the directory entitled **DIS5** it will be located as a sub directory on the cd or the unzipped drivers file.
 
**NOTE**
I am aware that there is a .INF file in the TOP LEVEL of the cd/downloaded drivers, don't use this. You need the file in the **DIS5** directory, if your download doesn't have them then please just PM me and i can send you a zip of the drivers you will need.
 
Right secondly copy that **DIS5** directory to your My Documents or somewhere of equal ease to get to.
 
Now for the more complicated part, if you don't follow this correctly or you encounter errors you must **DELETE** the drivers that where added in order to get your internet working, ill cover that later.
 
First of all open your **terminal** (Applications > Accessories > Terminal).
Now type in as follows:
 
```
sudo ndiswrapper
```
 
You will be promted for password (note when typing passwords in te console it will **apear as though you are not typing**, THIS IS NORMAL, type in your password and hit ENTER)
 
This will grant sudo access, and display a load of commands for ndiswrapper.
 
Now type in as follows:
 
```
sudo ndiswrapper -i /media/cdrom1/**DIS5/netwg11t.inf**
```
 
Replace */media/cdrom1/DIS5/netwg11t.inf* with the location of **NETWG11T.inf** on your computer, you can find this by going into the folder you saved DIS5, open DIS5 and then right click > properties any where in the folder to see the location, copy that location into the terminal, you'll have to add netwg11t.inf yourself though.
 
You will then see some text in the terminal reading something along the lines of '**...installing netwg11t...**' Itll be fairly instant and then a new line will begin in which you can begin typing. 
 
Now this is **IMPORTANT**, go to My Computer > File System > **/etc/ndiswrapper**
 
If the installation of your drivers worked correctly youll see a folder in there caleld **netwg11t** and perhaps a one called **auto**.
 
**DELETE ALL FOLDERS EXCEPT netwg11t!!!!!!** Especially Auto, even if its empty.
 
Now in the console you need to type in:
 
```
modprobe ndiswrapper
```
 
This will load the ndiswrapper drivers and seen as theres only one folder to execute (**netwg11t**) then you should be sorted.
 
**Now PLUG IN YOUR USB DONGLE**
 
If the light on the dongle begins to flash blue then your almost there! If it does not then skip to the end of this document and remove the drivers, check to ensure the drivers you have are correct, if they all are, then you can try to follow the next steps buts its likely that if the light isn't on then the drivers where installed incorrectly.
 
Now, this bit took me a while, and its not even complicated...
 
I COULD NOT ACCESS MY ROUTER. EVEN THOUGH DONGLE APPEARED TO BE FINE. FRUSTRATING!!!
 
My problem appeared to be that my computer was attempting to connect to the router and then stopped or sometimes prompted for a WEP/ WPA key and i had none (its possible i did and that i had forgotten it... in which case this might be the case for you? **Forgotten your WEP/WPA key?** no worries :) continue reading...)
 
If your dongle is in and flashing blue, then your little network icon in the top right of the desktop will be showing new options, if you left click it it'll have something like, WIRELESS NETWORK or NETWORKS and then a list of wireless routers in range and there respective signal strength.
 
Now i HIGHLY suggest that you reset your router to default settings, to do this press and hold the little black dot on the back of the router with a pen or similar tool, hold it for 15 seconds (10 i know but be sure...) then release it, if the reset worked your router light/lights will flash amber then go off, and in moments the router will return to life, i'm assuming you've got a netgear router for this as well, your individual routers will also likely have a reset button.
 
Now, once reset your router has **NO WEP or WPA keys**, the IP Address is now **192.168.0.1** and the password and username is **ADMIN **and **ADMIN** or **ADMIN** and **PASSWORD** (**lowercase**). The name of the router or SSID as its called is also now back to default which for netgear is **NETGEAR**.
 
So now we go back to our computer and pull out the usb dongle, give a quick restart to be sure, and then once back up plug the dongle back in, wait for it to initialise and then look in the network list, we shud see NETGEAR, now **DO NOT CLICK ON IT**! or it'll start tryingt o connect and take about 10 mins to realise it can't...
 
Do this instead, and this is (I HOPE!!) my trick lol
Left click the networks icon agian, go to manual configuration or manual setup, i forget which its called. In the list there should now be
 
**WIRELESS NETWORK**
WIRED NETWORK
MODEM CONNECTION
 
Click wireless network and then properties, when it loads you need to set it up **EXACTLY** as follows:
 
**SSID = NETGEAR**
**SECURITY/ ENCRYPTION (what ever its called) = WEP ASCII**
*now i know we have no wep, but it needs to be set to wep ascii*
**LEAVE** the passcode / passphrase and the rest of it **BLANK**. 
 
At the bottom where it has a drop down with things like **STATIC IP**, **AUTO DHCP** etc etc in it, choose the one with **AUTO** in it i think its **AUTO CONFIGURATION (DHCP)** or something like that, if its the right one the other options will gray out, now apply those changes, you can just click close or apply if its there (im not at my pc atm im at work so im doing this from memory...). once that is done you should return to the list of netowrk types, this time WIRELESS NETWORK should have a check box beside it, **MAKE SURE ITS CHECKED**, leave it about a minute to apply the settings. Load up firefox and try your internet! It should now be up, you might have to replug your usb dongle in again.
 
**BIG NOTE!**
**Sometimes your network icon can display as if no network connection is present or that the internet is disabled, ignore it! Load up firefox and see for yourself!**
 
I hope this works for anyone who needs it, some of you may not have to use the entire second half of resetting your router etc but i thought id put it in incase some of you had forgotten your WEP key etc or if you just couldn't get on the internet, and remember go to 192.168.0.1 and set up your WEP etc again, don't leave yoru network open for your neighbours!
 
**FINAL NOTE**
Removing the drivers is simple, open up the /etc/ndiswrapper folder again, and then open the terminal, type in:
 
```
sudo ndiswrapper -r netwg11t
```
 
This will remove the folder, you should see it dissapear in the folder you just opened, if it does then your ready to start a fresh.
 
ALSO
 
I have no idea why but my administration > windows wireless devices crashes whenever i load it, this might be due to my process, but regardless ive got the internet back now so i dont care!
 
Take care all, and enjoy surfing the net securely on Ubuntu Linux!

---

