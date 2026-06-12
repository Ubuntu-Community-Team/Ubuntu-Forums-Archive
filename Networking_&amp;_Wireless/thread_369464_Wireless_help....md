---
title: "Wireless help..."
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by cessna_89702 on 2007-02-24
Hey,
Im running Ubuntu 6.06 on my computer and i need some help getting on the internet with wireless. I bought a Linksys compact wireless -G USB Adapter. If I just plug it in to the usb it doesn't detect it at all it looks like. (is there a command I can run to see if it is detected?)
I have the install cd with the drivers etc..except its in the form or .exe and other window formats. Can I use ndiswrapper or another program to change the format of the drivers so I can install it and use this for internet? Details on how to would be nice.
Thanks.

---

### Post by Floppyjoe on 2007-02-24
You can enter the command:
```
lsusb
```
To see the available usb devices on your computer. Also:
```
iwconfig
```
will show if any of your interfaces is recognized as a wireless interface.
You will not be able to install the driver like you do in windows by running the .exe file.
If you are able to extract the necessary files from the .exe than you may be able to use ndiswrapper to make it work.
This requires you to install cabextract and unshield and possibly another which I can't remember offhand.

Post the output of the lsusb command and the iwconfig command here. Then further help can be given.

---

### Post by beanworks on 2007-02-24
Unfortunately, Linksys is not very Linux-friendly.  I have the same router, but set it up using a macintosh (no problem).  It will also set up on a Windows machine.  Once it's set up, you don't need the macintosh or windows machine.

But you might try just opening a browser and typing  192.168.1.1 in the address bar and see if it connects (that's the default IP for that router).  If that doesn't work, try configuring the ethernet connection to set 192.168.1.1 as a host, and try the browser again.

I'm curious to know if it works. :-)

Of course, the ***FIRST*** thing you need to do on the router is reset the password.

Oops, just noticed you are connecting with a USB  See Floppyjoe's post. :-)

---

### Post by cessna_89702 on 2007-02-24
To floppyjoe when i ran lsusb i got ```
Bus 002 Device 002: ID 13b1:0020 Linksys
```

Then I ran iwconfig and got ```
lo no wireless extensions     eth0 no wireless extensions sit0 no wireless extensions
```

---

### Post by Floppyjoe on 2007-02-24
I found this Url which says it works for your device.

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

I hope this helps you.

Floppyjoe

---

### Post by cessna_89702 on 2007-02-24
I have no internet on the computer with Ubuntu im typing from another computer so I cant get the updates. I might have to try to connect with a phone line but i never have before

---

### Post by Floppyjoe on 2007-02-24
> **cessna_89702 said:**
> I have no internet on the computer with Ubuntu im typing from another computer so I cant get the updates. I might have to try to connect with a phone line but i never have before
This is why a network cable sometimes comes in handy if you don't already have one. I have several in case I need to run from one end of the house to the other for this reason.

---

### Post by cessna_89702 on 2007-02-24
I have but when i just plug into the computer and phone it doesnt do anything..

---

### Post by Floppyjoe on 2007-02-24
A network cable and a phone cable are two different things. The network cable has a larger plug on the ends. Does your computer in question not have a network interface card for lans? i.e. wired ethernet, that you can run a network cable to your router with?

---

### Post by cessna_89702 on 2007-02-24
Im assuming this is a network cable. I take this cord and put one end into my computer and the other end in the hole where the phones cable would usually go.
[IMG]http://i20.photobucket.com/albums/b214/zach333/nbbnbnb002.jpg[/IMG]
[IMG]http://i20.photobucket.com/albums/b214/zach333/nbbnbnb001.jpg[/IMG]
How do I connect when I do that?

---

### Post by Floppyjoe on 2007-02-24
I believe that is probably a telephone cable because a network cable would not fit into a phone jack. So you probably do not have a wired ethernet card in your computer.


Edit:
It may be possible to pull the necessary files off the install CD by clicking on System/Administration/Synaptic Package Manager. Then click on Edit/ADD CDROM. Then click reload. Then search for the files in the howto guide.

---

### Post by cessna_89702 on 2007-02-24
Is it possible to get internet with a telephone cable? My friend has gotten internet using that cord.

---

### Post by Floppyjoe on 2007-02-24
Do you have a dial-up internet account? If yes then you should be able to connect to the internet with it.
Possibly your high speed internet provider has roaming plan for Dial-up.

[http://www.ubuntuforums.org/showthread.php?t=308098](http://www.ubuntuforums.org/showthread.php?t=308098)
This Url show how to get dial-up working.

---

### Post by cessna_89702 on 2007-02-24
We dont have Dial up. I we connect with cords we use DSL high speed is that the same or not?

---

### Post by Floppyjoe on 2007-02-24
That cable you showed me. It is connected from your phone line to your DSL modem. Then you have a network cable that connects from the DSL modem to either a router or the back of your computer somewhere. If your connection has a router then there is a network cable that connects from the router to your computer. If the computer you are trying to connect has a larger network cable jack on it then you should be able to connect it to your router or your DSL modem with a network cable.

---

### Post by Dracar on 2007-02-24
nvm, i didnt c the 2nd page...

---

### Post by cessna_89702 on 2007-02-24
Thanks I sent this with Ubuntu! Although im not wireless yet. Something went wrong on that tutorial, I think ill try again later or look for another tutorial

---

