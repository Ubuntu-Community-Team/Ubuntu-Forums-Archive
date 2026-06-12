---
title: "USB-Modem ZTE MF 180 problem with Ubuntu 10.10"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by Tambooosh on 2011-03-23
Hey people! 
Today I downloaded the last version of Ubuntu 10.10 and everything went smoothly while installing the system on my computer till I faced a small problem 'hopefully' :(

Usually I use an USB-Modem ZTE MF 180 in Windows Seven in order to get my internet connected, but when I tried to do the same with Ubuntu 10.10 It sticks in progress "connecting"..

I can see that the system recognized the USB-Modem 'cuz by clicking at the icon nearby the clock I can see the name of the Modem and I can set my connection configurations up till the moment when I click "connect" it sticks in the progress for a minute or two, and then returns "Connection Unestablished" or something like that..
I'm using now my Windows seven, cannot wait till I turn to Ubuntu one more time..

any help or suggestions please :)

Thanks .. um, plus, I am using a "Beeline 3G USB-Modem" if that helps, a Russian operator!

---

### Post by Tambooosh on 2011-03-24
actually when I click on connect it returns "Network disconnected" after sticking in progress for a while with out success!! 

any help people :(

---

### Post by Plumtreed on 2011-03-24
You should check in Synaptics to see if 'modemmanager' is installed and you probably will also need 'usb-modeswitch'.


...best to reboot after installing!

---

### Post by allerjoyce on 2011-03-24
probably you need not only the usb-modeswitch,  a usb driver may work for you.:)

---

### Post by Tambooosh on 2011-03-24
can you guys explain more .. I am not sure what should I do!!
in addition, since my USB-Modem refuses to work with Ubuntu, I'm not capable of downloading any packages from the internet.. so :(

waiting more explanation please!

---

### Post by Hippytaff on 2011-03-24
Can you post the output of ```
lsusb
``` with the usb device plugged in. 3G modems have the driver (firmware) inside the usb device. But as is standard practice, this is the windows driver and linux only recognises the device as a mass storage device. usb-modeswitch will switch the device so that ubuntu see's it as a modem. But it's best to see if that is the case first and lsusb will tell us that

---

### Post by Plumtreed on 2011-03-24
If necessary, you can download the 'usb-modeswitch' from the web to a USB drive, or cd/dvd, using your Win connection. Then boot Ubuntu and transfer the file in order to use it in Ubuntu.

---

### Post by Tambooosh on 2011-03-24
```

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636
Bus 001 Device 002: ID 0ac8:c40a Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


Here are the returns of 'lsusb'

I hope it shows something :(

---

### Post by Plumtreed on 2011-03-24
.....Google   PeppermintOS... it will probably work without downloading anything....based on Ubuntu and you will be able to add all the things you can with Ubuntu.

---

### Post by Tambooosh on 2011-03-25
though, it is not working.. when I set my connection configurations up and tru to connect it attempts to connect then return  a message "you are offline .. Network disconnected"

can anyone explain it more?

Thanks

---

### Post by Plumtreed on 2011-03-25
I suspect that your system sees the USB modem as a storage device so fails to use it as a modem. The 'usb-modeswitch' detects this and allows it to operate properly...as a modem.

Other than downloading 'usb-modeswitch' you could try unplugging your USBModem and then reconnecting, allow about 30 seconds for a reconnect.

Do you see anything when you right click on the Networkmanager applet>Edit Connections>Mobile Broadband ?

---

### Post by Tambooosh on 2011-03-25
well, here are some snapshots I hope can be handful in the solution :p

---

### Post by Tambooosh on 2011-03-25
when I open "My computer" here how the USB-Modem is being recognized!!

---

### Post by Tambooosh on 2011-03-26
can i find help here please .. I really want to use Ubuntu but always there is a problem!!

does anybody have an idea?

---

### Post by Sevmpe on 2011-03-26
Hi,

Maybe modemmanager (the program that manages 3G etc. modems) is having trouble configuring the tty ports of your modem. That happens to me sometimes.

First check that in the file [FONT="Courier New"]/lib/udev/rules.d/77-mm-zte-port-types.rules[/FONT] you have the lines:

```

ATTRS{idProduct}=="0031", ENV{.MM_USBIFNUM}=="03", ENV{ID_MM_ZTE_PORT_TYPE_MODEM}="1"
ATTRS{idProduct}=="0031", ENV{.MM_USBIFNUM}=="01", ENV{ID_MM_ZTE_PORT_TYPE_AUX}="1"

```

If not, add them as they tell modemmanager the correct ports to use. I looked at your lsusb output to identify the lines with ATTRS{idProduct}=="0031".

If you still don't get connected, check the system logs for errors coming from modemanager. Once again, it might have problems choosing the right ports even though they are written in the above file so look for errors about ttyUSB ports. Just remove the USB stick, insert it and try to connect again until it works.

I am not versed in this subject but I made mine work and it is almost the same as yours, MF637 (rebranded MF636 for Orange).

If you are tired of networkmanager/modemmanager try [Sakis3g]("http://www.sakis3g.org/"). It just works for me.

Cheers.

---

### Post by Plumtreed on 2011-03-26
Just after your disconnection notice....

You should try to 'disconnect-reconnect' (unplug the USB Modem and then plug it back in)....wait 30 or so seconds, wait for it to reconnect, and click on the NM applet and select your 3G connection.

---

### Post by Tambooosh on 2011-03-26
Sevmpe, Thanks for your reply, I did just like you said; and found those lines already posted there in the file, I tried it more than once but not able to get connected in each time.. plus I went to try Sakis3g by downloading it on my Windows Seven then transferred it to Ubuntu but far of luck though :( couldn't force it to work :p or I did not know how :) the file was being opened with an "Archive Manager" regarding the type of it ".gz" anyway! it did not help.. :confused:


Plumtreed, thanks alot bro, I tried it more than 100 times but it keeps disconnecting at the time trying to set a connection, couldn't understand though!!
I'm even not sure how Ubuntu is recognizing the USB-Modem; as a modem or as a Flash Disk.. 

so for no luck, I wanted to work in linux environment but it always returns me problems in the face :O Windows is much simpler,,

Thanks guys for trying to help ;)


Best regards!!

---

### Post by Sevmpe on 2011-03-26
Hi again,

It's a shame it's not working. I can feel your frustration from here. Anyway, if you still want to give sakis3g a try, put the file you downloaded in your home directory in linux. Then open a terminal and type:
```

gunzip sakis3g.gz
chmod +x sakis3g
./sakis3g --interactive

```
and the program should be running. Using sakis3g is self-explanatory. It'll take you through a series of menus until it connects and they are very easy to figure out.

---

### Post by widda on 2011-03-26
The Network Connections (setting up device) setup is critical.
Even the "Which type of Plan do you have"!
For example the only one working for me as demo'd by telstra shop guy, was to tick "My Plan Is Not Listed Here'
searchPosts by me Widda containing word Telstra.
I'll show you my current working setup if you still need suggestions.

---

### Post by Tambooosh on 2011-03-27
hey buddy, I tried the Sakis3g and the program worked :p but .... couldn't set a connection, at the second attempt it returns "faild to connect" :x :x :x

that's really disappointing...


  widda, thanks my friend, it won't harm though, please if you can share me your settings who knows, it may work in the end!!! 

I'm really bored with this problem not having the solution :( :( That hurts :pP

---

### Post by vivek.pandey on 2011-03-27
right click on your network manager and see your conection type is checked or not say if it is broadband is it checked or not?
if everything is ok try unchecking and rechecking and again connecting it. you wuld even remove the modem and then insert it and try. if still there is a problem the problem may be with apn number.
see if these steps help you or not

---

### Post by Tambooosh on 2011-03-27
Finally, I got it to work !!!

The problem was in the configurations!! Ubuntu was considering APN internet.beeline.ru
but the real one was home.beeline.ru plus I changed some of the settings just like you told me and it went smoothly :D :D :D :D

widda thanks alot it worked..


Thank you all people!
vivek.pandey
Sevmpe
Plumtreed

Best regards, I appreciate it alot guys ;) ;)

---

### Post by Tambooosh on 2011-03-27
people, one more question please!!

now I got connection, but every 5 minutes it disconnects by itself!! 

why that is happening!!? any suggestions??

---

### Post by Sevmpe on 2011-03-27
Hi Tambooosh,

I am glad you could make it work. I am afraid this is all the help I can provide. I have no idea why it disconnects. Maybe low signal? Anyway, good job making it work.

---

### Post by Tambooosh on 2011-03-27
Sevmpe, thanks alot my friend :) i really appreciate it.. :) :)

---

