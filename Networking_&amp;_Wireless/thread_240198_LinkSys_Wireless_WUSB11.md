---
title: "LinkSys Wireless WUSB11"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by Timmeh on 2006-08-20
I have a Wireless WUSB adapter (connected via USB) and I have Kubuntu installed.

Kubuntu isn't recognizing my wireless adapter and it's starting to frustrate me. Anyone have any tips on how to get it working?

---

### Post by infocom on 2006-08-20
I have a LinkSys WUSB11v4, just purchased the other day (because neither of my other 2 wireless cards worked). I thought it was compatable but think I got the wrong version of the WUSB11 as it did not work right away. 

Anyway, I did manage to sort of get it working using ndiswrapper. Using ndiswrapper and ndisgtk I installed the Windows driver that came with the CD for the card.

To get ndiswrapper working I used ndisgtk which is the graphical interface for ndiswrapper. I think I had to also install ndiswrapper-utils. I had to download them from the internet on another machine as I could not connect to the internet on my Ubuntu machine of course, and I couldn' tfind them on the LiveCD. Maybe ndiswrapper is on the live cd, I cant remember.

Anyway, once ndisgtk was installed I could get ot it under System -> Administration -> Windows Wireless Drivers.

To install the Windows driver I had to first run the .exe setup file on on the wireless card setup CD on Windows machine to unzip the files. Then burn them on CD rom to transfer to Ubuntu.

Then using Windows Wireless Drivers install the .inf driver file for this device.

It all worked, I can see the card, I can configure it etc. I can also run commands to see the wireless networks in my range. So it must be working. I used Wifi Radar to try to connect to the access points. 

BUT it is not being assigned an IP address by my router (the final step!). So I still cant connect.

Laurie

---

### Post by Timmeh on 2006-08-20
Any other suggestions?

---

