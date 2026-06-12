---
title: "Dell wireless connection problem using version 8.04"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by chrismic3 on 2008-05-29
Hello I just installed ubuntu on my Dell 600m laptop and it is amazing. The only problem though is that I have no wireless connection. Here is what I know about my system after using the lshw -C network. Ill take a picture and show it to you. I will also show you my modem and router if that helps. I have no idea on what to do. I even called a ubuntu rep/tech support guy and he had no idea lol. Any help would be great and I really appreciate your time. FYI its a linksys modem.

P.S I am really bad with tech names so be easy on the directions try to keep the Acronyms down to a minimum please:)I hope the pictures are here.

[ATTACH]72113[/ATTACH]

[ATTACH]72114[/ATTACH]

[ATTACH]72115[/ATTACH]

[ATTACH]72116[/ATTACH]

---

### Post by chrismic3 on 2008-05-30
sorry that I have to bump but does anyone have any ideas?

Thanks

---

### Post by Ayuthia on 2008-05-31
You should just be able to enable the b43 driver through System-Administration->Hardware Drivers.  If you do not see anything there and you have a wired internet connection through Ubuntu, you can also do the following:
```
sudo apt-get install b43-fwcutter
```It will ask you if you want it to find the firmware for you.  Say yes and it will install it for you.  I think that it will tell you to reboot afterwards.  If not, you can just try to start it up by typing (in the Terminal):
```
sudo ifconfig wlan0 up
```

If you don't have a connection, you can try this [link]("http://ubuntuforums.org/showthread.php?t=779754") and look for Option 2.

---

