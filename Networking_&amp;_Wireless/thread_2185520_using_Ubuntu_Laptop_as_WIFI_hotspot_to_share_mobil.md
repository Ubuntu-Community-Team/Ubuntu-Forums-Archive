---
title: "using Ubuntu Laptop as WIFI hotspot to share mobile broadband  with Galaxy Tab via it"
date: 2013-11-03
forum: Networking &amp; Wireless
---

### Post by ask_ on 2013-11-03
Hello , 

I have a Lenov Laptop in which I have Ubuntu 12.04 installed. 
I also have a Samsung Galaxy Tab 3 (SM T211). 

I use a mobile broadband to access internet via my Ubuntu laptop. I am from India and I use a Reliance 3G netconnect USB modem.

I don't currently have a microsim card with me , so I am unable to use internet from my Samsung Galaxy tab.
Can I share my mobile broadband connection on Ubuntu Laptop with my Galaxy Tab via Wifi ? I wish to use my Ubuntu Laptop as a hotspot for that.

[http://www.howtogeek.com/116409/](http://www.howtogeek.com/116409/) I followed the instructions on this link. And created a hotspot using WEP . But my Galaxy Tab is not able to connect to the hotspot. It says WiFi not in range. This is happening even if I am sitting next to my laptop. What should I do to connect it and browse internet on my tab using Ubuntu Wifi ?

The howtogeek site says a Wi-Fi network cant be shared this way. It will work only with a wired network. Because when creating a hotspot on Wi-Fi it will close the existing Wi-Fi connection. But is it also the case for USB mobile broadband ? This doesn't seem to be the case as the hotspot was active along with the mobile broadband connection. That is the mobile broadband connection didn't disconnect after creation of hotspot . How to link the two ?

Thanks.

---

### Post by syam-nair on 2013-11-03
Instead of WEP encryption try "WPA & WPA2 Personal". this should solve the problem, else revert back :)

---

### Post by ask_ on 2013-11-03
Thanks for replying. Trouble is I am unable to save the changes when selecting WPA2 and WPA2 personal. In Ubuntu , when I select that, the 'save' button is greyed i.e unable to press it. 
I was able to select infrastructure mode but not save WPA2 in it. Is it got to do with drivers ? I have wl30 driver mostly.

---

### Post by urapain on 2013-11-04
> **ask_ said:**
> Thanks for replying. Trouble is I am unable to save the changes when selecting WPA2 and WPA2 personal. In Ubuntu , when I select that, the 'save' button is greyed i.e unable to press it.  I was able to select infrastructure mode but not save WPA2 in it. Is it got to do with drivers ? I have wl30 driver mostly.  Save is greyed out until password is long enough

---

### Post by ask_ on 2013-11-05
I changed to WPA and WPA2 still its not connecting.

By the way interestingly there was an update to WPA-WPA2 in Ubuntu updates. :guitar:

---

### Post by ask_ on 2013-11-07
Can anyone suggest solutions to my problem. I am still unable to connect my Samsung tab to Ubuntu hotspot. It says the hotspot is out of range. Can you suggest me commands which I can run in terminal and post here, so that you may better diagnose my problem. Thanks.

---

### Post by tgalati4 on 2013-11-07
Does your Ubuntu laptop's wireless card support "Master Mode"?

[https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)

Have you tried using the USB cable to connect to the Galaxy phone?  I would get that working first, then apply updates to the phone, reboot, then try wireless again.

You need to unlock USB tethering with an app: [https://play.google.com/store/apps/details?id=com.tetherunlocker](https://play.google.com/store/apps/details?id=com.tetherunlocker)

---

### Post by sbnwl on 2013-12-15
Hi ask_

It's absolutely possible to share the internet connection of Reliance Broadband USB stick. Basically your wifi card is going to serve as hospot, and Reliance USB stick has its own modem to catch the internet from Reliance network.

In short, follow this guide:
[URL="http://ubuntuforums.org/showthread.php?t=2165035"]http://ubuntuforums.org/showthread.php?t=216503
[/URL]
If your wifi card is not capable of making wifi hotspot (or supported), you will be automatically told. Just follow, and let me know.

---

