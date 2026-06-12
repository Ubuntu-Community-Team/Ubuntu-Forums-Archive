---
title: "E170 Huawei Modem on O2 Broadband?"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by daithi81 on 2008-08-03
Hello, I am totally new to Linux and I am trying to get the above mentioned modem working, but to no avail. I have asked around on other forums, but all I get are scattered suggestions of code and drivers, of which none of them seem to work. It doesn't help that I'm not exactly a computer programmer or anything, so all of this code that is thrown at me can be quite confusing at times. I understand that I need to tell Ubuntu 8.04 that my modem is in fact a modem and not a hard drive. So could someone help me do that for a start?

[-o<

---

### Post by geraldvillorente on 2008-08-03
i think huawei has no driver yet in ubuntu...coz we have the same problem...im using ubuntu 8.04 and still i cant use my mobile modem...maybe on the next release of ubuntu(8.10)

---

### Post by daithi81 on 2008-08-03
Cool, any idea when this will be released?

---

### Post by geraldvillorente on 2008-08-03
ubuntu release is every six months... if you noticed on its numbers
7.04 = 2007, april
7.10 = 2007, october
8.04 = 2008, april
8.10 = 2008, october

---

### Post by geraldvillorente on 2008-08-03
[http://ubuntuforums.org/showthread.php?t=823687]("http://ubuntuforums.org/showthread.php?t=823687")

try to read this thread dude maybe it can help us

---

### Post by daithi81 on 2008-08-03
Yeah, I have been trying the recommendations but its breaking my heart!

:(

---

### Post by GeorgeVita on 2008-08-04
Hi,

to "drive" the E170 from ubuntu, please check my post:
[http://forum.huawei.com/jive4/thread.jspa?threadID=322982](http://forum.huawei.com/jive4/thread.jspa?threadID=322982)
(or search for "ubuntu" on forum.huawei.com)

Also I had some problems with E170 on my laptop (connecting/disconnecting from usb port at Vista) fixed with decoupling capacitors. Not all the problems are Software! This problem was my first "road" to ubuntu, trying to find a "hardy" solution, now I have a working modem with a nice OS!
My post for this h/w fix is:

[http://forum.huawei.com/jive4/thread.jspa?threadID=321295](http://forum.huawei.com/jive4/thread.jspa?threadID=321295)

Regards
George

---

### Post by daithi81 on 2008-08-04
Thanks, I will try that.

---

### Post by Sealbhach on 2008-08-04
I had a Huawei E220 modem working on Hardy 8.04.

I used Gnome-PPP, a graphical interface for dial-up modems using wvdial.

To install it type in the terminal:

```
sudo apt-get install gnome-ppp
```

You'll find it in the Menu under Internet.

Then plug in your modem, type in the terminal:

```
sudo wvdialconf
```

Now open up Gnome-PPP and get it to autodetect your modem, it should find it on ttyUSB0.

To find what settings you should put in Gnome-PPP, have a look at your wdial.conf file:

```
cat /etc/wvdial.conf > ~/Desktop/modem_settings
```

This will place the settings in a text file called "modem_settings" on your desktop.

Make sure that you tick "ignore terminal strings" (stupid mode) in Gnome-PPP.

You can also view the connection log in Gnome-PPP to find out where your dial-up sequence is at.

Hope this helps.


.

---

### Post by daithi81 on 2008-08-04
> **GeorgeVita said:**
> Hi,

to "drive" the E170 from ubuntu, please check my post:
[http://forum.huawei.com/jive4/thread.jspa?threadID=322982](http://forum.huawei.com/jive4/thread.jspa?threadID=322982)
(or search for "ubuntu" on forum.huawei.com)

Also I had some problems with E170 on my laptop (connecting/disconnecting from usb port at Vista) fixed with decoupling capacitors. Not all the problems are Software! This problem was my first "road" to ubuntu, trying to find a "hardy" solution, now I have a working modem with a nice OS!
My post for this h/w fix is:

[http://forum.huawei.com/jive4/thread.jspa?threadID=321295](http://forum.huawei.com/jive4/thread.jspa?threadID=321295)

Regards
George

I tried that out George and it actually worked... for a few seconds. I was trying to load up gmail so I could find this thread and thank you and the following happened:

```
--> Connect time 0.2 minutes.
--> pppd: ï¿½ï¿½[06][08]ï¿½ï¿½[06][08]Ø¨[06][08]
--> pppd: ï¿½ï¿½[06][08]ï¿½ï¿½[06][08]Ø¨[06][08]
--> pppd: ï¿½ï¿½[06][08]ï¿½ï¿½[06][08]Ø¨[06][08]
--> Disconnecting at Mon Aug  4 13:18:43 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Disconnecting at Mon Aug  4 13:18:43 2008
```

I tried a few times and the same thing happened. Any ideas?

---

### Post by daithi81 on 2008-08-04
> **Sealbhach said:**
> I had a Huawei E220 modem working on Hardy 8.04.

I used Gnome-PPP, a graphical interface for dial-up modems using wvdial.

To install it type in the terminal:

```
sudo apt-get install gnome-ppp
```

You'll find it in the Menu under Internet.

Then plug in your modem, type in the terminal:

```
sudo wvdialconf
```

Now open up Gnome-PPP and get it to autodetect your modem, it should find it on ttyUSB0.

To find what settings you should put in Gnome-PPP, have a look at your wdial.conf file:

```
cat /etc/wvdial.conf > ~/Desktop/modem_settings
```

This will place the settings in a text file called "modem_settings" on your desktop.

Make sure that you tick "ignore terminal strings" (stupid mode) in Gnome-PPP.

You can also view the connection log in Gnome-PPP to find out where your dial-up sequence is at.

Hope this helps.


.

I have tried to install gnome ppp, but when I follow the first command you gave me it says 'command not known/found'. I even copy and pasted the exact text from Ubuntu into terminal and still the same problem.

---

### Post by Sealbhach on 2008-08-04
> **daithi81 said:**
> I have tried to install gnome ppp, but it doesnt appear to be on ubuntu for me. I also tried to download the file and manually install but I couldnt get it to work, for some reason.

Was it a deb file? Did it give any reason for not installing. For me, Gnome-PPP was by far the easiest way.


.

---

### Post by daithi81 on 2008-08-04
> **Sealbhach said:**
> Was it a deb file? Did it give any reason for not installing. For me, Gnome-PPP was by far the easiest way.


.

It was a .tar file. Could you point me to the one you used?

---

### Post by Sealbhach on 2008-08-04
Well I just got it from the terminal:

```
sudo apt-get install gnome-ppp
```

But if you need to get it using windows or something, then download it from here:

[http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-ppp/](http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-ppp/) 

and put it on  a USB drive.

.

---

### Post by GeorgeVita on 2008-08-04
> **daithi81 said:**
> I tried that out George and it actually worked... for a few seconds. I was trying to load up gmail so I could find this thread and thank you and the following happened:

```
--> Connect time 0.2 minutes.
--> pppd: ï¿½ï¿½[06][08]ï¿½ï¿½[06][08]Ø¨[06][08]
--> pppd: ï¿½ï¿½[06][08]ï¿½ï¿½[06][08]Ø¨[06][08]
--> pppd: ï¿½ï¿½[06][08]ï¿½ï¿½[06][08]Ø¨[06][08]
--> Disconnecting at Mon Aug  4 13:18:43 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Disconnecting at Mon Aug  4 13:18:43 2008
```

I tried a few times and the same thing happened. Any ideas?


YES! I thing that now you faced the h/w problem!!

If you could try the same modem (E170) on the same laptop with Vista you could hear the sounds of USB connect/disconnect (blim-blom). This (in my case) was caused by a "ripple" or "spice" in the power line of the USB port.

Do you have any experience on Electronics (h/w) or do you have a friend to make the "power supply filter" for you?  Can you just check the above (if this problem exists in the same hardware modem & laptop)?

Also I have to note that I am not familiar with Linux commands but as you see it works fast & clean. Before posting the above I was re-formating the HD, install the ubuntu from the start, and keeping notes. I am very sure that when you have an empty laptop (I mean without many USB peripherals, modems, rooters etc.) you can realize that the E170 works, BUT for the h/w reason you cannot be sure. Dont try external USB hubs etc. because the "power supply ripple" (the crash reason) remains.

---

### Post by daithi81 on 2008-08-04
> **Sealbhach said:**
> Well I just got it from the terminal:

```
sudo apt-get install gnome-ppp
```

But if you need to get it using windows or something, then download it from here:

[http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-ppp/](http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-ppp/) 

and put it on  a USB drive.

.

Ok, I got Gnomeppp installed, but I am having trouble with the settings. I copied in whatever seemed relevant from my wvdialcon file, but when I attempt to dial it it stalls on 'sending password'. When I look at the log it says 'please enter password'. I looked at the settings for O2 Broadband (attached) and I see no username or password. Any ideas?


EDIT: Those attachments didnt come out very well, I will type it out:

APN = Static : open.internet
Access number : *99#
User Name:
Password:

---

### Post by Sealbhach on 2008-08-04
Hi Daithi,
I believe you can put anything you like in the username and password fields. Gnome-PPP requires something in there but when I was using my E220 to dial-up three.co.uk, it was irrelevent. So just put anything in, just don't leave it blank.

Your APN looks OK. Make sure you have selected Stupid Mode as well.


.

---

### Post by daithi81 on 2008-08-04
> **Sealbhach said:**
> Hi Daithi,
I believe you can put anything you like in the username and password fields. Gnome-PPP requires something in there but when I was using my E220 to dial-up three.co.uk, it was irrelevent. So just put anything in, just don't leave it blank.

Your APN looks OK. Make sure you have selected Stupid Mode as well.


.

Yeah, I have selected stupid mode. I tried putting in my own username and password and I got the same message in the log:

```
--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","open.internet"
AT+CGDCONT=1,"IP","open.internet"
OK
--> Modem initialized.
--> Please enter password (or empty password to stop):
```

I tried entering the password after the colon, but nothing happened.

:confused:

---

### Post by daithi81 on 2008-08-04
I got it working, yaaaaaaaaaaaaaaaaaay!

Thanks for your help everybody!

---

### Post by Sealbhach on 2008-08-04
> **daithi81 said:**
> I got it working, yaaaaaaaaaaaaaaaaaay!

Thanks for your help everybody!

That's good. What was the story with the password?


.

---

### Post by daithi81 on 2008-08-04
> **Sealbhach said:**
> That's good. What was the story with the password?


.

The username and pass are both 'gprs'

The phone number is *99#.

I still get the disconnection problem, but I think that is a hardware problem with this desktop, because it doesnt happen on my laptop.

---

### Post by GeorgeVita on 2008-08-05
Good morning,

IF you still have randomly disconnects, read the following, ELSEIF discard!
bye

The disconnects are a possible h/w problem that exists on your post#10

<quotes>
I tried that out George and it actually worked... for a few seconds. I was trying to load up gmail so I could find this thread and thank you and the following happened:

Code:

--> Connect time 0.2 minutes.
--> pppd: ï¿½ï¿½[06][08]ï¿½ï¿½[06][08]Ø¨[06][08]
--> pppd: ï¿½ï¿½[06][08]ï¿½ï¿½[06][08]Ø¨[06][08]
--> pppd: ï¿½ï¿½[06][08]ï¿½ï¿½[06][08]Ø¨[06][08]
--> Disconnecting at Mon Aug  4 13:18:43 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Disconnecting at Mon Aug  4 13:18:43 2008

I tried a few times and the same thing happened. Any ideas?

<quotes>

a. you were connected for 12 seconds!
b. the modem hung up
c. and trying to disconnect it was not on the USB port! (cannot open /dev/ttyUSB0)
d. to fix this you had to remove and reinsert the modem

Finally: This is a crash that most E170 have, caused by a ripple or spike on the power line.

Check again my post#15 (not all problems are s/w driven!)

---

### Post by daithi81 on 2008-08-05
I appreciate your effort. But I can't perform the fix you are describing, nor do I know of anyone who could. So I'm afraid that option is not a possibility.

Thanks anyway.

---

