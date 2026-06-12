---
title: "Configuring Modem using setserial"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by Louis de Broglie on 2008-02-21
I have an internal modem and I tried configuring it using wvdial. But it says that no modem is detected and asks me to become sure that it is configured properly by setserial. Can any tell me how to use setserial?:)

---

### Post by bennettpr on 2008-03-03
I have this exact problem right now. wvdial seems to look for COM ports which external, modems are attached to, but I have an internal modem...

Can anyone offer any help here?

---

### Post by schmildo on 2008-03-04
I only know a little bit, but it might help you regardless;

On windows you have COM ports, on linux you have TTY (aka serial) ports

WINDOWS:::::LINUX
COM 1.............ttyS0
COM 2.............ttyS1
COM 3.............ttyS2
COM 4.............ttyS3

On linux; if you type;

***setserial /dev/ttyS0***

you might get something like this;

***/dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4***

In windows modems are often connected to one of these com ports. Apparently linux doesn't have to map the names as i've listed them above, but it's the way it's 'normally' done... so I assume that if in windows your modem was on com 3 then your modem will be on ttyS2 in linux.

The setserial command lets you configure how linux uses the port that the modem is plugged into, you can adjust the speed of the port and IRQ and so on... as to what values these should be I couldnt say, but setserial seems to have an autoconfigure option, perhaps you could try using that.

I've not used a modem in a linux machine for a very long time!

I don't forsee any great troubles with the internal modem, beyond finding out what /dev file to look for (which you'd have to do if it was external anyway). There must be another command to type to find out what ttyS ports are in use.

Good luck.

---

### Post by schmildo on 2008-03-04
Yey me! I found a really good guide. It shows you how to find out what /dev/ttyS[0-n] you are using and more.
 I'd try it out but i dont have a modem!

[http://www.linuxjournal.com/article/5448](http://www.linuxjournal.com/article/5448)

Let me know how you go.

Oh and incase he doesnt say; to quit minicom you type CTRL+a then 'q' to quit, or 'x' to reset the modem and quit.

I just found another site that says that you should be able to send normal AT commands directly to the device by using the echo command, the bloke on the site used this method to find which port had the modem on it...
-------------------------
echo atdt3333333 > /dev/ttyS1

You should hear some clicking noises from the modem. If it's an external modem you can also look for lights flashing.

If the modem actually dials the '3333333' number you'll quickly want to follow that command with this one:

echo ath > /dev/ttyS1 
-------------------------

the atdt command simply tells the modem to dial the following number.. i thought there should be a space between the atdt and the number but i dunno...

the ath command tells the modem to hang up.

If you tried sending the atdt command to each of the /dev/ttyS[0-n] ports/files you might find what your looking for, i think wvdial might use /dev/modem as the default modem, but this is really just a symlink to /dev/ttySx, you should be able to find out what it's currently set to by:

ls -l /dev/modem
i think you'll get something like;
lrwxrwxrwx 1 root root 6 Mar  4 03:40 /dev/modem -> /dev/ttyS1

---

### Post by bennettpr on 2008-03-04
brilliant!
Thanks for the quick follow up :)
I'll give these things a crack and let you know how I get on.

---

### Post by Chappy7777 on 2008-03-04
> **Louis de Broglie said:**
> I have an internal modem and I tried configuring it using wvdial. But it says that no modem is detected and asks me to become sure that it is configured properly by setserial. Can any tell me how to use setserial?:)

Louie, 

How new is your system? Most very likely it is new enough to have a built in winmodem. Getting a winmodem (WINmodem) to work w/Linux is 20% luck and 80% black magic, and 100% a real pain in the ****. I messed w/my last setup for quite a while, even bought a new internal modem that was supposed to be Linux compatible. No joy.

Spend the bucks, I paid 35$ for a TrendNET external serial hardware modem and it worked PNP.
Ubuntu found it and configured it for me. That and I can watch the lights and see what is happening. Alot ez-er than trying to decode beeps and crackles. 

I live in Canada and found the modem at Canadian Computers, but take a look anywhere that sells modems for an external serial hardware 56K modem. Mine works fine with XP that was already installed. Just a remove/add hardware in the Control Panel. 

Oh, and go into your BIOS and set the internal modem to off.

Good luck. Let us know what you end up doing that works. It might help the next guy.

There is a modem compatibility chart out there and the URL may be:

[http://devidal.tv/~chris/winmodems/pci_list.html](http://devidal.tv/~chris/winmodems/pci_list.html)  If this is the wrong address do a google or someone else on here will know the right address.

I'm working from memory because, Praise God, we finally got cable broadband in this tiny backwoods village.

---

### Post by bennettpr on 2008-03-05
Thanks for all the helpful posts (this forum is amazing)

installed minicom and it confirmed that no modem was found (dud driver)

I upgraded my Ubuntu release to 7.04 ($5 for the new cd) then found out which kernel version I had (the last driver wasn't compatible with my new kernel version ) by using uname -r

THEN, I revisited linuxant and downloaded the correct driver for my kernel version. Installed it, it found the modem fine and assigned it to ttySHSF0

fired up minicom, changed the port and was able to talk to the modem.

Now testing dial-out settings! woohoo!

Ill likely cough up the $20 to linuxant for the license which will allow the modem to function at "full" 56K :)

---

