---
title: "connecting 3 USB modem/ mobile broadband  in Ubuntu"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by nimonika on 2008-07-01
Dear All,

I am in the UK and I have been unsuccessfully trying to configure my 3 HSDPA modem with Hardy (8.04). Please someone pass me any available pointers.

Thanks

---

### Post by Sealbhach on 2008-07-01
Is it the three network. This is easy to do with Gnome-PPP, I use it myself. 

Just download the Gnome-PPP deb file on another computer, stick it on a usb drive , install it in Ubuntu and configure.


[http://ubuntuforums.org/showpost.php?p=5176814&postcount=7](http://ubuntuforums.org/showpost.php?p=5176814&postcount=7)


Let me know if you have any probs.

.

---

### Post by nimonika on 2008-07-01
Thanks a lot, incidentally my laptop specs are same as yours in that even I am on a Vaio, however my problem is that the modem itself is not detected in /dev as /dev/ttyU* etc. What can I do ?

Thanks for your help. It is indeed the three network. Please could you also post me your wvdial.conf file.

---

### Post by Sealbhach on 2008-07-01
OK, no probs.

Type in the terminal:

```
sudo wvdialconf
```

This should tell you that a modem has been detected.

Then try to detect it in Gnome-PPP.

I'm at work, so I can't get you my wvdial.conf but really, last time I set up the modem in Gnome-PPP I didn't need to edit config files at all.


.

---

### Post by nimonika on 2008-07-01
Cheers. I shall try and let you know how it goes.

---

### Post by Sealbhach on 2008-07-01
> **nimonika said:**
> Cheers. I shall try and let you know how it goes.


P.S. Make sure the modem is attached when you boot up, otherwise it doesn't find it and usually I have to re-boot.


.

---

### Post by nimonika on 2008-07-01
Sorry, ubuntu cannot detect the modem, I tried wvdialconf, although it was connected right throughout. I even installed gnome-ppp which was not able to detect it either. Any other thing I can try?

---

### Post by Sealbhach on 2008-07-01
> **nimonika said:**
> Sorry, ubuntu cannot detect the modem, I tried wvdialconf, although it was connected right throughout. I even installed gnome-ppp which was not able to detect it either. Any other thing I can try?

One more thing. Reboot, keeping the modem plugged in. Type in the terminal:

```
sudo modprobe usbserial vendor=0x12d1 product=0x1003
```

Then try:

```
sudo wvdialconf
```

After that, I'm out of ideas. It works for me that way.



.

---

### Post by nimonika on 2008-07-01
Everything fine, except that I do not know what to do for the username , password fields. I thought leaving it blank would work, but it does not. The modem is now detected and when I say on the command line, sudo wvdial, it shows connected and a bunch of other things, however still no connection. Any ideas here?

---

### Post by Sealbhach on 2008-07-01
> **nimonika said:**
> Everything fine, except that I do not know what to do for the username , password fields. I thought leaving it blank would work, but it does not. The modem is now detected and when I say on the command line, sudo wvdial, it shows connected and a bunch of other things, however still no connection. Any ideas here?

That's good.:D

What I do is put the phone number of my modem (the one on the SIM card) in the username, then my password is the password I use to log into [www.three.co.uk](www.three.co.uk) the website. 

I'd recommend trying to connect it with Gnome-PPP, I **_know_** that works. See my earlier post in this thread for how to configure in Gnome-PPP:

[http://ubuntuforums.org/showpost.php?p=5176814&postcount=7](http://ubuntuforums.org/showpost.php?p=5176814&postcount=7)

You can also view the connection log in Gnome-PPP, so you can see exactly where it's stopping. 

.

---

### Post by nimonika on 2008-07-01
Serious problem here is that this is a modem borrowed from a friend
who only uses it under windows and told me that I would not need any username/password to use it. Is there a way to find out the username/ phone number and set the password to blank somehow? Sorry this is longer connection related...:)

---

### Post by Sealbhach on 2008-07-01
> **nimonika said:**
> Serious problem here is that this is a modem borrowed from a friend
who only uses it under windows and told me that I would not need any username/password to use it. Is there a way to find out the username/ phone number and set the password to blank somehow? Sorry this is longer connection related...:)

I think you can get away with leaving the passwords blank, or just put any text in there, I don't think it matters that much. However, the phone number for three.co.uk is 

*99#



.

---

### Post by nimonika on 2008-07-01
I guess its just bad luck. I got everything working,gnome -ppp tried to connect, but for who-knows-what reason the connection timed out. Here is the output from the log:

--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATX3
ATX3
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT*99#
--> Waiting for carrier.
ATM1L3DT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATM1L3DT*99#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Tue Jul  1 18:00:37 2008

Another thing was that the connection was not always stable. Afte a timeout, I had to reboot everytime. reconnect the modem, and do the whole stuff again.

Surely there must be some hope for souls like me...:(

---

### Post by Sealbhach on 2008-07-02
> **nimonika said:**
> 

Surely there must be some hope for souls like me...:(

I'm not sure why the signal was lost. Are you sure you have selected stupid mode in the Gnome-PPP config?

Normally, if you get a connection, you don't need to reboot, you would only need to reboot if the modem is not detected by your computer. But if you were a able to dial up the ISP then the modem has been detected so rebooting would not make any difference at that stage.

Keep trying, I had a lot of pain when I first tried it, but now I can connect to the net in 2 minutes from a fresh install of Ubuntu. Don't lose heart, you'll learn a lot if you keep going and it sounds like you're nearly there, it's not bad luck, you just don't have the configuration exactly right yet.


.

---

### Post by nimonika on 2008-07-02
People like you keep me going!! Victory atlast !!! posting from ubuntu...:):) The only small (yet another ) problem I am having is that the connection is quite slow- is this normal. Sometimes it is moderate, but mostly slow. For someone used to working on 5 different windows, ssh and email clients simultaneously, this does not help ...;) Any ideas on how to fool the connection to get top speed?

BTW, your posts were a grand saviour. Thanks a lot!!!

---

### Post by Sealbhach on 2008-07-02
I would recommend using Swiftweasel as your browser. It is a special build of Firefox optimized for Linux.

You can download a deb file from here

[http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717](http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717)

It works just like an exe file in windows, just double click to install, make sure you choose the right architecture.

You should notice a difference... but it might be that coverage in your area is not so good.

---

