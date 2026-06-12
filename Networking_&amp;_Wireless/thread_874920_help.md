---
title: "help"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by analyzer92 on 2008-07-30
I currently use opensuse 11.0 but wish to switch over to ubuntu. First however, I want to try to get my wireless network working on the live CD so when I install ubuntu 8.04, I can easily get it to work right the first try.

My wireless card is a Linksys WMP54GS. I downloaded a folder of drivers for the card and used bcmwl5.inf. I used this in ndiswrapper on opensuse and it worked out. So I am sure that I have the right driver.

However, I noticed after installing the driver by typing in "ndiswrapper -i bcmwl5.inf" it said the driver and hardware present. However, when I type in "lshw -C network", for my card "wlan0", the driver was listed as b43 not ndiswrapper. I am new to ubuntu and don't know how to set ndiswrapper as the driver for my card, I knew how to do it in opensuse through YaST but I guess I might need to know the command line way to do it.

I am sure that this is the problem and I will be able finish off the setting up. Just one last question though, I heard somewhere that in wpa_supplicant, when you do the driver ndiswrapper is wext or something like that. Is this true? My connection is wpa that is why I ask.

Thanks in advance.

---

### Post by superprash2003 on 2008-07-30
its pretty difficult to setup wireless without installing ubuntu, as it may require you to sometimes reboot your pc for wireless to work.. which is not possible through a live cd

---

### Post by kdorf on 2008-07-30
After you set up with ndiswrapper, try this:

> sudo modprobe -r b43
sudo modprobe ndiswrapper

Also, read the link in my sig, particularly the section regarding post titles.

---

### Post by analyzer92 on 2008-07-30
Thanks, I will remember to make a better title next time.

Anyway, I installed ubuntu. I decided to try the b43 driver this time. So I installed b43 and b43-fxcutter. I then went to the network manager applet and when I left clicked, I saw my wireless network was there. I clicked on in and entered my password, it tried to connect but didn't. I kept trying and retrying and even tried doing the manual configuration. Eventually one time when I clicked on the network and typed in the password it connected but it says 0%. This was strange because the bar in the applet before I connected was over halfway filled. I made a screenshot of this. [IMG]http://i24.photobucket.com/albums/c1/smob/Screenshot.png[/IMG]

What can I do? Also, I was wondering when I type in the password it asks for type and the options are TKIP or Automatic (Default). Which one of these options should I use

Thanks in advance.

---

### Post by superprash2003 on 2008-07-30
please give your ifconfig and iwconfig outputs

---

