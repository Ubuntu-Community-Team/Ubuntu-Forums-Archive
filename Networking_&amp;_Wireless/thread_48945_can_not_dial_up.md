---
title: "can not dial up"
date: 2005-07-14
forum: Networking &amp; Wireless
---

### Post by Lambert on 2005-07-14
I've recently installed hoary 5.04. I'm trying to used dial up to connect to my isp.

I've went through pppconfig and set up a file. I use pon [xxx] to connect but I can't tell if anything is happening. In a terminal it just goes to next command line with no script saying it's doing anything. There is also no other indicator saying it is initializing modem or dialing. I wait a few minutes and tried a browser but get address can't be found error. So I take it I'm not connecting.

I'm a newbie and stuck at this point. What indicators should I see saying it's dialing? Where do I go next to troubleshoot and correct?

---

### Post by jasmuz on 2005-07-14
If you want to diagnose what is happening, open another console and before typing pon, run this tail -f /var/log/messages, then hit pon and watch the messages...post them so we have a clearer idea.

---

### Post by Skrewdriver on 2005-07-14
another handy command in this situation is plog (see plog man page for details), run   it after you have run pon xxx.
myabe you could copy the output from that and post it here.

---

### Post by Lambert on 2005-07-14
[QUOTE=jasmuz]If you want to diagnose what is happening, open another console and before typing pon, run this tail -f /var/log/messages, then hit pon and watch the messages...post them so we have a clearer idea.[/QUOTE]


This is what it said

Jul 14 08:38:45 localhost pppd [30206]: pppd 2.4.2 started by todd, uid 1000
Jul 14 08:38:47 localhost pppd [30206]: Exit

---

### Post by Lambert on 2005-07-14
[QUOTE=Skrewdriver]another handy command in this situation is plog (see plog man page for details), run   it after you have run pon xxx.
myabe you could copy the output from that and post it here.[/QUOTE]


After running plog here is what i get. I'm on another machine so I can't copy unless someone wants to breifly descibe how to copy to floppy so I can use on a windows machine. I tried to save text file to floppy and it gave me an error of can't save. I'm not just a newbie to ubuntu but a true newbie to linux.

Here is short hand minus date and localhost.

pppd [30575]: pppd 2.4.2 started by todd, uid 1000
chat [30576]: Can't get terminal parameters: Input/output error
pppd [30575]: Connect script failed

---

### Post by Skrewdriver on 2005-07-14
unfortunately that doesn't tell us much, except that it craps out after 2 seconds . what did plog say?

---

### Post by Skrewdriver on 2005-07-14
okay, getting somewhere.
have a crack at running wvdial, let us know how that goes.

Edit:
It's best in this situation to run wvdial as root ie. run
```
sudo wvdial
```
... and if that works, then copy /etc/wvdial.conf to your home directory (but with the new name .wvdialrc then change ownership to the normal user  (in this case *skrewdriver.*)

```

skrewdriver@ubuntu1:~$ sudo cp /etc/wvdial.conf ~/.wvdialrc
skrewdriver@ubuntu1:~$ sudo chown skrewdriver ~/.wvdialrc

```

---

### Post by Lambert on 2005-07-14
[QUOTE=Skrewdriver]okay, getting somewhere.
have a crack at running wvdial, let us know how that goes.

Edit:
It's best in this situation to run wvdial as root ie. run
```
sudo wvdial
```
... and if that works, then copy /etc/wvdial.conf to your home directory (but with the new name .wvdialrc then change ownership to the normal user  (in this case *skrewdriver.*)

```

skrewdriver@ubuntu1:~$ sudo cp /etc/wvdial.conf ~/.wvdialrc
skrewdriver@ubuntu1:~$ sudo chown skrewdriver ~/.wvdialrc

```[/QUOTE]
 ran wvdial as root and here's what I get

WvDial: Internet dialer version 1.54.0
Warning: section [Dialer Defaults] does not exist in wvdial.conf
Cannot open /dev/modem: No such file or directory

(actually does the last line three times in a row then goes back to prompt)

---

### Post by Lambert on 2005-07-14
livecd from mepis worked from initial try using kppp. I'm new to linux and frustrated with all this configuring I have to do to make something work. I've went ahead and installed mepis and initially everything appears to be working properly.

Thanks to those who responded and tried to help me.

I like the ubuntu concept and some of the features. Maybe when I am a little more experienced or the next release I'll take a look at ubuntu again.

---

### Post by GTvulse on 2005-07-14
Grab a copy of gnome-ppp from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) copy to a diskette, load into the machine ---insert floppy, open Places->Computer, select floppy icon and then "Mount Volume" in contextual, a.k.a. right-click, menu--- copy to your home directory and install by opening a teminal  emulator and typing "dpkg -i gnome-ppp*.deb" (or what ever name the .deb file may have taken in the transfer).

Gnome-PPP does basically the same functions as kPPP, creating a proper .wvdialrc file for your ISP and managing the dial-up connection as well. The user must have the privilige to access modems (that is belong to the dialup group), you set such privilege by selecting System->Administration->Users and Groups->select user->Properties->User Privileges tab.

---

### Post by eeried on 2005-07-17
i have the same problem as Lambert.

I'm going to try using gnomme-ppp but I simply wondered if it is not already installed in Hoary Hedgehog?

I'll post again after installing this utility.

---

### Post by joshpelkey on 2005-08-18
Before using wvdial, you must first configure it.  Follow these steps:

1) sudo wvdialconf /etc/wvdial.conf

2) Note the output on the screen.  Some things may say "failed" but as long as wvdial ends up recognizing a modem at a port [ex: /dev/ttySL0], you're good to go.

3) You must now edit wvdial and enter your information.

4) sudo gedit /etc/wvdial.conf

5) Enter your info.  After which your wvdial.conf should look similar like this:

[Dialer Defaults]
Modem = /dev/ttySL0
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
; Username = <Your Login Name>
; Password = <Your Password>

**Take out** the semicolons and edit the Phone, Username, and password accordingly.

6)  For systems using the SmartLink slmodem drivers,
     the following line should be added to its /etc/wvdial.conf
     Carrier Check = no

7)  All done.  Now run it with "sudo wvdial"

---

### Post by mcrofutt on 2005-10-08
:)  THANKS for the line about smart link drivers!!!!! :D 
 I'd been having trouble with it, I hope this fixes my problem.

---

### Post by puter on 2005-11-26
if you run that tail I get " command -f " not found
sudo makes no difference either

---

