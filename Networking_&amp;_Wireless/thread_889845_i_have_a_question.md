---
title: "i have a question"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by jimistephen on 2008-08-14
i have and acer aspire 3680 notebook that i just got the wireless card working after about a week, now i need to know how do i connect it to my linksys wrt54g v8.2 router with no security on it.
any help would be great...

~stephen

---

### Post by finer recliner on 2008-08-14
click the network manager icon in the upper right corner near the clock (assuming you are using GNOME). if your wifi card is turned on, you should see a drop-down list of available networks you can connect to. if you havent configured your router in any way, it's SSID (name) is probably called 'linksys'.

---

### Post by jimistephen on 2008-08-14
well i thought so also and the first time it did, and said it was connected to it but there was no sigunal

---

### Post by finer recliner on 2008-08-14
things to try:
1) bring your router & laptop closer to each other
2) make sure your router is not within a few feet of another radio device, such as a cordless telephone or baby monitor
3) move the router or laptop over just a little bit. this will affect the path of the radio wave from the router to the laptop; potentially for the better.

---

### Post by jimistephen on 2008-08-14
ok, just restarted my computer and turned on the wifi card, and it cam up with 4 options 1 HBENET which is a local guys wireless service he has, 2 linksys which has about a 75% signal, one that says MOJO and one that just say wireless linksys is the one i checked (filled in the circle on) and then the wireless bar meter came up and says "Wireless network connection to 'linksys' (0%).
the router is in the other room but the desktop computer i'm on and sitting right beside is picking up that same router and signal and it's connected at 80%. i guess i'll try moving away from this computer.  

ok, went in and set by the router, computer was about a foot away and still it didn't work...someone please help!!!!

---

### Post by finer recliner on 2008-08-15
unless i read your post wrong, there are two SSID's showing up named 'linksys'. You can find out which one is yours, but connecting to one of them and trying to log into the admin interface. you can do this by opening a web browser and navigating to [http://192.168.1.1](http://192.168.1.1) 

if that router is still using the default settings, there should be no username, and the password is 'admin'. 

go to the status page and check what the MAC address of that router is. now go your physical router, flip it over, and read the MAC address printed on the bottom. Find the one SSID has a MAC address that matches your router's.

Once you find out which SSID is your router, i recommend changing the SSID to something more personal. (as well as enable encryption, and change the admin interface password.

---

