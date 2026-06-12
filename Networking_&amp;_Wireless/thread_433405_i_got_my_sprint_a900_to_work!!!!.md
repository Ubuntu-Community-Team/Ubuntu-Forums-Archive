---
title: "i got my sprint a900 to work!!!!"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by outer_space on 2007-05-04
I got my samsung a900 phone to get internet to my ubuntu laptop thru usb.  This took me about a month of fooling around.  Now I dont need windows for a damn thing!

I had connection manager working in wine, but it wouldnt detect the phone.  Then I tried wvdial and after a long time of trying different things I got it to actually talk to the phone.  But it wouldnt give me internet.  Then on gentoo forums someone suggested adding a few lines to wvdial.conf, and now my junk works.  Make this text in your /etc/wvdial.conf and put in your number and password and then you can get internet.  Might have to change USB2 to another number.

[Dialer Defaults] 
Stupid Mode = on 
Modem = /dev/ttyUSB2
Baud = 460800
Init = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = #777 
Username = [email]yournumber@sprintpcs.com[/email]
Password = yourpass
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP
Auto Reconnect = on
Carrier Check = no

---

### Post by Elif Tymes on 2007-05-05
This is Dial Up? Or can you use this to access the Sprint Power Vision?

---

### Post by outer_space on 2007-05-05
This is to get internet to my laptop with usb.  Previously only possible with 'sprint connection manager' windows-only and used to make my junk bluescreen all the time.

---

### Post by Elif Tymes on 2007-05-05
I'm working on getting this working on my A640 using Bluetooth.. Quite a doozy. I'm tempted to just upgrade to the A900 just for simplicitys sake.

---

### Post by outer_space on 2007-05-05
Its probably not that different.  I forgot to mention I also had to disable some secret menu stuff in the phone.

---

### Post by _DjScrew_ on 2007-06-04
anyone had any luck with windows mobile based phones yet? I'm using a 700wx, when I first connect it I can see it with "lsusb" but if i run the command again it's gone?

---

### Post by elephant007 on 2007-09-12
> **_DjScrew_ said:**
> anyone had any luck with windows mobile based phones yet? I'm using a 700wx, when I first connect it I can see it with "lsusb" but if i run the command again it's gone?
what version of Ubuntu are you running?  If you're running Edgy, go to [http://www.mobile-stream.com/usbmodem_wm.html]("http://www.mobile-stream.com/usbmodem_wm.html")
download their trial, you can use it with your 700wx.  I can't get mine to work on Feisty though.  Still working on it.  
*HINT* check registry for usb modem

---

### Post by bigmack83 on 2008-03-20
I have connected my Sprint Blackberry 7130e by tethering it to my ubuntu laptop (7.1 Gutsy). Here is my post

[http://ubuntuforums.org/showthread.php?p=4550979#post4550979](http://ubuntuforums.org/showthread.php?p=4550979#post4550979)

---

### Post by mjamesd on 2008-07-07
I couldn't get this working with my a900m. I know the phones are slightly different, but I know I should be able to get it working. What stuff did you have to do on the phone itself to get it to work? Also, how do you know which USB# to use? I tried 0 through 6 and it didn't work with any of them.

EDIT:
I got it working. I just ran `sudo wvdialconf` and it wrote the configuration to /etc/wvdial.conf. Then I ran `wvdial` and it just worked! I had to be disconnected from my wifi before I started wvdial. Here's my wvdial.conf:
[Dialer pulse]
Auto Reconnect = on
Dial Command = ATDP
Carrier Check = no

[Dialer shh]
Init3 = ATM0

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = on
Modem Type = USB Modem
ISDN = 0
Phone = #777
Carrier Check = no
Modem = /dev/ttyACM0
Username = [email]mytendigitphonenumber@sprintpcs.com[/email]
Auto Reconnect = on
Password = randompassword
Baud = 460800

EDIT:
Okay, I keep getting booted after a few minutes. I keep getting this error when I connect (though it still connects):
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.

And then when it drops:
--> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> Provider is overloaded(often the case) or line problem.
--> The PPP daemon has died. (exit code = 15)

In `man pppd`, exit code 15 says this:
"The link was terminated because the peer is  not  responding  to echo requests."

The same thing happened when I ran it under sudo except I didn't get the permissions errors in the first error I posted. Any suggestions?

---

### Post by mjamesd on 2008-07-07
Okay, after getting off work and searching around on these forums, I found my problem. In /etc/ppp/options I had to set lcp-echo-failure to 0 and lcp-echo-interval to 0. I am now connected and chatting on Skype while riding the bus between two cities!

EDIT:
Now I don't have to mess with the command line. I set up gnome-ppp for use with my Sprint Samsung a900m with great ease, as all the options for it had clear parallels to the /etc/wvdial.conf file. Now I have a notification in my tray instead of a terminal without any real information.

---

