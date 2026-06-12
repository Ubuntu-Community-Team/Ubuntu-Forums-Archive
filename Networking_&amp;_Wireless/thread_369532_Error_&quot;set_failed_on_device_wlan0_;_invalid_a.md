---
title: "Error &quot;set failed on device wlan0 ; invalid argument&quot;"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by soul814 on 2007-02-24
So I spent an hr and a half trying to set up the wireless myself, my wired connection works fine but i can't seem to get the wireless to work =/

im using a linksys wmp11, i set it up using ndiswrapper and it shows up in iwconfig and ndiswrapper -l shows it as installed and working fine, if i type iwlist it shows my channels but when i type

sudo iwconfig wlan0 essid "linksys" 

it gives me that error

Error for wireless request "Set ESSID" (8B1A)
"set failed on device wlan0 ; invalid argument"

---

### Post by chili555 on 2007-02-24
And what does it say when you type: sudo iwconfig wlan0 essid linksys ? That is, without the quotes?

---

### Post by Silentvoice on 2007-02-24
No need for the quotations. just "sudo iwconfig wlan0 essid linksys" will do.

---

### Post by soul814 on 2007-02-24
So after I posted I gave up and plugged in my wired ethernet cable, turned off my wireless connection in the system >> admin >> network and then I restarted my computer.

I typed iwconfig to see if anything changed and it showed up linksys, but it didnt really matter cause my wireless connection was turned off. I updated all the latest stuff and then I pulled out my wire and restarted again. 

Then I went to firefox and google loaded, whats weird is google loads and i can search for things however I cant go to any other sites. I'm like restricted to google.


well linksys is my cousins router no WEP, right now if I type it again nothing happens. however if i type my own router

sudo iwconfig wlan0 essid linksys2

I get

Error for wireless request "Set ESSID" (8B1A) :
Set failed on device wlan0 ; Invalid argument.


------ EDIT
So, I installed network manager and my wireless connection doesnt show up on it, i edited the /etc/modules file to include ndiswrapper =/

---

