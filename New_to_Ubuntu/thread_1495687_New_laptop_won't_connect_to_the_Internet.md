---
title: "New laptop won't connect to the Internet"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by mameshiba on 2010-05-28
I'm posting this in this forum because although I've been using ubuntu for some time I'm still more of a 'user' than anything. Feel free to move it if it's in the wrong place.

I recently bought a new Stylenote laptop. I ordered it without an OS because I wanted to install Ubuntu, which I did by downloading the ISO from [hyar]("http://www.ubuntu.com/getubuntu/download"). It installed fine and seems to be working without any issues, but I can't get it to connect to the internet.

It has a StyleNote 10/100 lan & wireless 802.11G card, and I am trying to make it work by plugging in my cable modem by ethernet cable. How do I check it's working and how can I fix it? The 'synch' light comes on on the modem when it's plugged in and the laptop is switched on, which I presume means the modem can see the laptop, but I don't know.

Any and all help will be greatly appreciated!

---

### Post by jerrrys on 2010-05-28
hardwire it and pull up firefox, should work out of the box...

---

### Post by mameshiba on 2010-05-28
I just tried again, but it isn't. It won't bring up any of the web pages I type in. I thought I might need to manually enter my network settings as per the advice in the help file, but when I check the settings on my desktop PC it's set to Automatic (DHCP)...

---

### Post by halitech on 2010-05-28
what is the output of
```
lspci
```
and
```
sudo ifconfig
```

---

### Post by jerrrys on 2010-05-28
nevermind

---

### Post by mameshiba on 2010-05-28
This is what I get from putting the codes in terminal:

[IMG]http://i191.photobucket.com/albums/z147/crazyspideylady/temp/Screenshot-1.png[/IMG]

Automatic (DHCP) option is found in System > Preferences > Network Connections > Wired

---

### Post by cgb on 2010-05-28
Is their a Router Involved or just the Cable modem?  If it is just directly to the calbe modem like it sounds from your post and the modem was previously connected to another PC, then you probably need to power cycle the modem to get it to release its bind.  Basically unplug the power to the modem for 60 seconds and plug it back it.  Then try again...

---

### Post by lavinog on 2010-05-28
according to this thread: [http://ubuntuforums.org/showthread.php?t=1308484](http://ubuntuforums.org/showthread.php?t=1308484)
You might need to lower the mtu settings.

Post the output of ifconfig.
```

ifconfig>ifconfig.txt

```
Then you can copy the ifconfig.txt file to the computer you are using to paste the output instead of taking a screenshot.

---

### Post by mameshiba on 2010-05-28
Woo! Thanks, that worked! Good ole switching it off and on again (^-^) Thanks all for your help!:guitar:

---

### Post by cgb on 2010-05-28
No problem..  If you are going to be switching between computers often then it would be best to get a router in the picture.   Otherwise everytime you switch connections to the internet between PC's you will need to reboot the modem.  Basically a security setting of the modem that locks it to a MAC address to prevent others from hijacking your internet connection.

---

### Post by mameshiba on 2010-05-28
No, it's okay, the PC is old and is going... but thanks (^-^)

---

