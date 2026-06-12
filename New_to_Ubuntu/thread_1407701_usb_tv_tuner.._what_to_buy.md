---
title: "usb tv tuner.. what to buy"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by rflores2323 on 2010-02-15
Just wanted to see what you guys are using for tv tuners?  I bought a hauppage 950Q however cant get it to work. 

Anyone have any recommendations on an usb stick that will work out the box?  I want digital and analog.  dont care about recording 2 shows at once, 1 is enough imo.

Any help.

---

### Post by JerichoKru on 2010-02-15
> **rflores2323 said:**
> Just wanted to see what you guys are using for tv tuners?  I bought a hauppage 950Q however cant get it to work. 

Anyone have any recommendations on an usb stick that will work out the box?  I want digital and analog.  dont care about recording 2 shows at once, 1 is enough imo.

Any help.

According to here: [http://www.hauppauge.com/site/support/linux.html](http://www.hauppauge.com/site/support/linux.html) the 950Q should be supported.

Though, I noticed here on the forums that there has been problems getting it to work.

Perhaps Google to see if you can get a resolution.

---

### Post by rflores2323 on 2010-02-15
> **JerichoKru said:**
> According to here: [http://www.hauppauge.com/site/support/linux.html](http://www.hauppauge.com/site/support/linux.html) the 950Q should be supported.

Though, I noticed here on the forums that there has been problems getting it to work.

Perhaps Google to see if you can get a resolution.

I have been searching for the last week probably 2 hours a day at home trying to get the 950q to work with no success.   Seems like no one has it working as I get no response from poeple on support.  

Would running a Virtual machine on ubuntu be a solutoin maybe???

what usb tv tuner do you recommend?

---

### Post by anaconda on 2010-02-15
I dont have the same card than you, but it seems that you will need the firmware file (driver) copied to 
/lib/firmware
Have you already copied it to there?

The file for your card seems to be (???):
dvb-fe-xc5000-1.6.114.fw
eg from:
[http://kernellabs.com/firmware/xc5000/](http://kernellabs.com/firmware/xc5000/)

Many tv-tuners need the correct firmware file in the /lib/firmware folder to work
And if the kernel supports the device, the firmware file is all that is needed.

I have 2 dvb usb cards, another is hauppauge wintv nova-t usb2 (the older big box thing, not the small one)
and a fuj:tech stick, which is the cheapest I have ever seen. (less than 20&#8364;).. the brand name varies, but the firmware it needs is: dvb-usb-af9015.fw
Both of these cards need the correct firmware in the /lib/firmware folder, and both of these work perfectly.. I have heard that some cards dont need the firmware though.

After having the firmware you can eg. install kaffeine, and then configure your TV. (select the signal source from a list. (country/city)

oh. and dmesg will show the name of the firmware file you will need, then you can find it easily with google
eg. type in terminal: (either) 
tail -f /var/log/messages
(or dmesg)

and THEN insert your DVB stick to the computer and you will see what is happening .. eg. what firmware file the kernel is trying to load..

PSS: sorry if my explanation is not clear.. (I may have drunk a little too much wine..)

---

### Post by bkratz on 2010-02-15
Here is a thread about the 950Q;  maybe some help???

[http://ubuntuforums.org/showthread.php?t=1369146](http://ubuntuforums.org/showthread.php?t=1369146)

---

### Post by rflores2323 on 2010-02-15
ok here is my dmesg log

[http://paste.ubuntu.com/377255/](http://paste.ubuntu.com/377255/)

I checked my lib/firmware folder I do have the file already in there as it was installed with karmic already.

I try to open kaffeine and scan for tv channels and the program says no suitable device found.

---

### Post by steveneddy on 2010-02-15
I think I had to install Kaffeine to watch TV on my lappie with the same USB TV tuner.

---

### Post by rflores2323 on 2010-02-15
> **steveneddy said:**
> I think I had to install Kaffeine to watch TV on my lappie with the same USB TV tuner.

do you remember what you did to get it working??  I tried kaffeine and scan channels and it says no suitable found.  

weird

---

### Post by steveneddy on 2010-02-15
> **rflores2323 said:**
> do you remember what you did to get it working??  I tried kaffeine and scan channels and it says no suitable found.  

weird

Hmmm - I'm on 7 at the moment. Let me turn off the VM and look at the Ubuntu side and try and remember what I actually did to get this going.

It actually works very well and I use it on the road often.

BRB

---

### Post by steveneddy on 2010-02-15
What version of Ubuntu are you using?

---

### Post by steveneddy on 2010-02-15
I think there are some drivers you need to get and I'm still looking for them, but here is a few lines from the Kaffeine web FAQ:

> 20. I have a DVB device but Kaffeine does not display DVB features. Why?
1) make sure your device is recognized and proper drivers are loaded. Check dmesg for DVB messages, if all goes fine it should end with a message like "DVB: registering frontend 0".
2) check permissions of the device files "/dev/adapterX/*".
3) start Kaffeine from a shell and look at messages about DVB. If there is no such messages then your Kaffeine version was compiled without DVB support. See README.dvb in sources package.

21. My DVB device is detected, i have succesfully scanned for channels, but channels names are greyed out. Why?
Live DVB playback only works with the xine engine. Go to Menu->Settings->Engine and choose "Kaffeine-Xine". Then restart Kaffeine. If there isn't any "Kaffeine-Xine" entry, you have to install it: it should be labelled "kaffeine-xine" or similar.

---

### Post by steveneddy on 2010-02-15
According to this web page:

[http://www.linuxtv.org/wiki/index.php/ATSC_USB_Devices](http://www.linuxtv.org/wiki/index.php/ATSC_USB_Devices)

the 950Q should be supported on every kernel from Intrepid on.

although here are the drivers you can install if you need them from this web wiki:

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q#Making_it_Work](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q#Making_it_Work)

I believe these are the steps I had to take to get this working.

don't forget to restart after installation to get the kernel modules to load correctly.

Enjoy.

---

### Post by rflores2323 on 2010-02-16
> **steveneddy said:**
> According to this web page:

[http://www.linuxtv.org/wiki/index.php/ATSC_USB_Devices](http://www.linuxtv.org/wiki/index.php/ATSC_USB_Devices)

the 950Q should be supported on every kernel from Intrepid on.

although here are the drivers you can install if you need them from this web wiki:

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q#Making_it_Work](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q#Making_it_Work)

I believe these are the steps I had to take to get this working.

don't forget to restart after installation to get the kernel modules to load correctly.

Enjoy.

I already have the firmware as it was installed by default in karmic.  I installed kaffeine and then went to scan channels. it found some channels. I then went to play the channels and it gives me a device not found pop up.

---

### Post by anaconda on 2010-02-16
what kind of antenna are you using?

The antenna that came with the USB-DVB is mostly a joke, and I prefer connecting it to a  real TV antenna socket..

With the small antenna you can only get the strongest channels, and only if you have good reception..

---

### Post by rflores2323 on 2010-02-16
> **anaconda said:**
> what kind of antenna are you using?

The antenna that came with the USB-DVB is mostly a joke, and I prefer connecting it to a  real TV antenna socket..

With the small antenna you can only get the strongest channels, and only if you have good reception..

Yes I am using the antenna that came with it.

---

