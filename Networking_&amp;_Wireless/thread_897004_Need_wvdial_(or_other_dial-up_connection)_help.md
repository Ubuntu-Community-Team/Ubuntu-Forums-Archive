---
title: "Need wvdial (or other dial-up connection) help"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by A2JC4life on 2008-08-21
I bought a new modem, and wvdial seems to recognize it easily, so that issue is finally out of the way.  However, I still cannot seem to configure a dial-up connection.  (Ubuntu *really* needs to have gnome-ppp or something along those lines built in as a default, given that the other methods for making a dialup connection are so complicated and it's nearly impossible to do anything else in Ubuntu without a working internet connection.)

I tried the Network Admin method, but that gives such bizarre options, scattered in such stange tabs and such, that I can't even figure out what to input there.  And it is apparently not possible to set up a connection through there without DNS information, which PeoplePC refuses to give out.

So I tried to install gnome-ppp, as per the instructions at help.ubuntu.com/community/DialupModemHowto/SetUpDial..., and was told that the file(s) could not be found.

So I tried to use the direct wvdial method, following the instructions from the same site.  The following instruction:

```
$ sudo wvdialconf /etc/wvdial.conf
```

detected the modem with no problem.  It tells me that the modem is found at /dev/ttyACM0, and that its maximum speed is 460800.  So far, so good.  So I run the next thing in the instructions:

```
$ sudo nano /etc/wvdial.conf
```

and input my dialup number, username, and password.  (I had no idea if I should keep the angle brackets or not, so I tried it both ways.)  I saved the file and exited and ran:

```
sudo wvdial
```

only to be told (both times, with the angle brackets and without) that there is no valid telephone number, no valid username, and no valid password.

Please help!

---

### Post by Stemp on 2008-08-21
> And it is apparently not possible to set up a connection through there without DNS information, which PeoplePC refuses to give out.

You could use OpenDns adresses :
208.67.222.222
208.67.220.220

What others problems do you have with network-admin ?

---

### Post by A2JC4life on 2008-08-22
What are OpenDNS addresses?  (I get how to use them; I'm just curious.)

The network-admin is not allowing me to have it detect my modem or anything.  A serial modem is the only modem option.  (I have a USB modem.)  I'm not sure if I'm properly locating the connection once I've created it, because nothing shows up anywhere with the name that I assigned to it.  And I'm not sure why there are multiple tabs *and* a "properties" button - it confuses me, as far as what information I do and don't need and what is connected with what.

---

### Post by Stemp on 2008-08-22
> What are OpenDNS addresses? (I get how to use them; I'm just curious.)

OpenDns are free and ISP independant DNS : [http://en.wikipedia.org/wiki/Domain_Name_System](http://en.wikipedia.org/wiki/Domain_Name_System)
If you can't find your ISP DNS, you could use those.

> The network-admin is not allowing me to have it detect my modem or anything. A serial modem is the only modem option. (I have a USB modem.) I'm not sure if I'm properly locating the connection once I've created it, because nothing shows up anywhere with the name that I assigned to it. And I'm not sure why there are multiple tabs and a "properties" button - it confuses me, as far as what information I do and don't need and what is connected with what. 

Using network-admin, you select serial modem, enter the phone number, user and password. In the Modem Tab, you select /dev/ttyACM0. In the options Tab, you check evrything (for now).

---

### Post by A2JC4life on 2008-08-22
/dev/ttyACM0 is not an option in the list.

---

### Post by Stemp on 2008-08-22
try to type /dev/ttyACM0

If it's not working, maybe you should try pppconfig : [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#Alternative%20Way%202%20(using%20pppconfig%20&%20pon/poff)](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#Alternative%20Way%202%20(using%20pppconfig%20&%20pon/poff))

---

### Post by timcredible on 2008-08-22
gnome-ppp is in the repos, just go to system->administration->synaptic, do a reload and search for gnome-ppp and install it.  works fine.

as for having gnome-ppp on the cd by default, i agree with you.  on the positive side, the next version of ubuntu will have an improved network manager that may solve this problem.

---

### Post by A2JC4life on 2008-08-22
Tim, is gnome-ppp actually *there*, or does it only work if you're connected to the internet?  'Cause the whole problem is that I can't get connected to the internet.  (I had this same problem with my last distro.  Except that time it was the attempt to install the modem driver which, thankfully, is not necessary with this modem.)

I tried pppconfig.  All in all, I like it *much* better than the other options I've looked at so far.  It bears a much stronger resemblance to what I'm used to working with, so I don't feel like I'm trying to set the thing up in a foreign language.  But when I try to run pon, it says that /dev/ttyACM0 is an "unrecognized option."  (I tried /dev/modem, too, and got the same error.)  It will only accept the plain old "numbers" as options: i.e. /dev/tty1, /dev/tty2, etc.  Now what?

---

### Post by Stemp on 2008-08-22
There is something about verizon and pppconfig.
Maybe it could help you.
[http://www.aselabs.com/articles.php?id=224](http://www.aselabs.com/articles.php?id=224)

---

### Post by A2JC4life on 2008-08-22
I started a new thread with a new title, for the pppconfig issue.

---

### Post by _duncan_ on 2008-08-22
Can you post the contents of /etc/wvdial.conf? Just replace your login info with * but leave everything else as is.

My hunch is there is a comment character ";"  at the start of the line that's why wvdial is treating the whole line as a comment. I'd also like to look over the other settings. Who knows, maybe we'll get lucky.

---

### Post by A2JC4life on 2008-08-25
Ah, now that is quite a logical theory.  I'll check it.  Is there an easy way to copy the contents so I can paste them?

---

### Post by _duncan_ on 2008-08-25
> Is there an easy way to copy the contents so I can paste them?

I'm assuming you have other ways of connecting to the internet from Ubuntu other than your problematic dial-up modem. Tell me if you don't and we'll figure something else out.

1. open the file from the terminal using gedit. Here's the terminal command:
```
sudo gedit /etc/wvdial.conf
```

2. highlight the entire content (CONTROL-A using the keyboard), then click on the copy button on the top toolbar.

---

### Post by A2JC4life on 2008-08-26
Well, I thought I had saved it to an OpenOffice file, but when I opened the file in Windows, it was empty.  Drat.  

You were right, though; those lines were commented out.  I removed the semicolons and it works like a charm!  I was doing the happy dance.  :)  Literally, I was dancing here. (My six-year-old thought I'd lost it. hehe)  I've been trying to get online with Linux for 6-8 YEARS, so this was huge!  I still have to come here (Windows) to get on the web, though, because I have a weird Firefox issue.  (It's in another thread.)

I have a couple questions about wvdial.  The first time I tried it, I got a "no carrier" message.  I'm assuming that means that the number is no good.  (I accidentally entered the wrong one first, instead of the primary number I usually use from here.)  The second time, I got a "busy" message.  Both times, it tried again and again and again to connect, ad infinitum, and I couldn't get it to stop.  Even exiting the terminal didn't work; I had to unplug the modem.  Is there some command that will tell it to stop trying?  Also, is there any way to give it backup numbers to try, besides editing the wvdial.conf file every time?

Thank you so much!

---

### Post by _duncan_ on 2008-08-26
Are you saying you can now connect to the internet (i.e. send/receive emails, update/add/remove packages using Synaptic, etc) but just can't browse the web from Ubuntu using firefox?

This is important coz instead of trying to figure out the quirks with wvdial, we can now try installing other dialers to see if the same problem crops up. Same thing with your firefox problem. Instead of firefox, you can try using opera, which is available from the Ubuntu repos. Being able to connect to the repos will open up a whole slew of possible solutions that would otherwise be difficult to do if you're not connected.

---

### Post by A2JC4life on 2008-08-26
Yes, that's correct.  I downloaded some packages last night as means of verifying that the connection was working.  I downloaded gnome-ppp, but I haven't tried it yet.

And I uninstalled and reinstalled Firefox, but it's still not working right.  Silly me; I didn't even think to try installing another browser. That would make this easier, because I wouldn't have to keep booting back into Windows to ask questions!

---

### Post by _duncan_ on 2008-08-26
gnome-ppp is the graphical front-end to wvdial. Theoretically, if wvdial works, gnome-ppp should also work. Don't worry about gnome-ppp overriding your now working wvdial settings. gnome-ppp keeps a separate configuration file in your home directory.

If you're still getting the "no carrier" error, you can try turning "Stupid Mode" on in gnome-ppp and see if that solves the problem. This is a bit iffy coz some modems require that setting, some don't. Not too familiar with your particular modem.

Tell me if you're having problems with gnome-ppp. I still have a few tricks up my sleeves.

----------------

Another possibility to solving the firefox problem is to install the earlier version of Firefox (version 2.0) from the repos. I'm assuming you are using Hardy with the default Firefox 3.0?

---

### Post by A2JC4life on 2008-08-26
Stupid mode didn't help.  But I think maybe the phone number was bad, because this one works.

I am using Hardy with Firefox 3.0, yes.  But I don't want to have to go back to FF 2.0. :(  I've been using 3.0 (on Windows) since the day it came out, and I *like* it!

---

### Post by _duncan_ on 2008-08-26
> I am using Hardy with Firefox 3.0, yes. But I don't want to have to go back to FF 2.0.  I've been using 3.0 (on Windows) since the day it came out, and I like it!

Yeah, FF 2.0 is a bit clunky for my taste too. However if FF2 works and FF3 doesn't, it might give us some insight why FF3 is misbehaving. If both versions give the same error, it could mean a config file shared by both versions is corrupt. It's all in the spirit of being able to narrow down the FF3 problem.

---

### Post by A2JC4life on 2008-08-26
Gotcha!  (Sure wish I weren't on dialup. lol)  Can I have them installed simultaneously, or do I need to remove FF3 again first?

---

### Post by _duncan_ on 2008-08-26
From what I read on other posts, they (FF2 and FF3) can both exist on the installation. Never tried it myself though, so you'll have to take this comment with a grain of salt.

Personally I'm more optimistic about trying out Opera first before FF2 but it's just a matter of preference.

Here's another option: I understand there is a Firefox 3 linux installer from the firefox website. The installation process is probably going to be more complicated than installing from the Ubuntu repos, but if you're running out of options, it's something worth considering. Can't help you with the step-by-step coz I never tried it.

---

### Post by ritmi on 2008-08-27
kan i download gnome/pppoe

---

### Post by ScorpKing on 2008-09-30
This is what I use on my box. Search the forums for wvdial.conf to see other examples. You might also have to add "127.0.0.1 localhost" to /etc/hosts if only some programs can connect because networkmanager needs eth0 up before you will have dns (or just configure eth0 manually). I also had to change files in /etc/ppp/* before i could actually connect. 

###### START OF FILE wvdial.conf for mobile phone and 3G USB modem #####

[Dialer Defaults]
Init1 = ATZ
Init2 = AT+CGDCONT=1,"IP","Internet",,0,0
Modem Type = USB Modem
Stupid Mode = 1
New PPPD = yes
Baud = 921600
ISDN = 0
Carrier Check = no

#### ---- This number will work for Vodacom and MTN networks ---- ####
Phone = *99***1#

Password = ''
Username = ''

#### ---- Use this modem setting for Mobile phones ---- ####
#### ---- Run `sudo wvdial phone` in konsole ---- ####

[Dialer Phone]
Modem = /dev/ttyACM0

#### ---- Use this modem setting for E220 USB Modems ---- ####
#### ---- Run `sudo wvdial 3g` in konsole ---- ####

[Dialer 3G]
Modem = /dev/ttyUSB0

######### END OF FILE ########

---

### Post by uganda on 2008-11-07
Hi,

thanks for this post, it helped me figure out I needed to run wvdial!

I am new to Ubuntu and after having a bad experience with Windows (loosing some data due to a crash last week was the last straw) decided to switch to Ubuntu, since I have heard good things about it. After installing on my laptop with internal modem, it took me a while to figure out I had to get a modem driver (very confusing that the Ubuntu documentation talks about "System->Administration->Network" which doesn't exist in Ubuntu 8.10 !), so following "scanModem" and the instructions in ModemData.txt (attached) I downloaded hsfmodem_7.68.00.14full_k2.6.27_7_generic_ubuntu_i386.deb (and transferred via USB memory stick).

Once this post helped me figure out I had to configure wvdial first, I did that and then ran wvdial and I could hear it dial and it connected, yay!!!  I verified by going to a few sites in Firefox and all seemed fine, but slow - I figured because of the unregistered driver. So, I went and paid for the full version and entered the license.

I then rebooted and started wvdial again, but now it does not get a carrier anymore and I cannot hear it dial or anything.  Here's the output from running wvdial:

--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT086727234
--> Waiting for carrier.
ATDT086727234
NO CARRIER
--> No Carrier!  Trying again.

I tried a few times and verified with another Windows laptop next to it that the cable/connection still worked (could still dial-up fine with that one).

The wvdial.conf looks like this:
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/modem
ISDN = 0
Phone = 086727234
Password = ***
Username = ***

but that hasn't changed since I ran wvdialconf.  I then tried pon (I had previously configured "provider" via pppconfig) and for some reason it worked.  So, I changed the Baud in the wvdial.conf to 115200 as well and now (not sure whether it was related), that one works, too!  So far, so good!

I can now (using either pon or wvdial) connect, and it sounds like it's using 56k (I know these dialing sounds quite well after years of dial-up ;-), hoorah! (looks like the $20 was worth it).  The I was stuck for a while, because even though I could verify my connectivity by pinging things (like the DNS server of my ISP or google.com), Firefox did not load any web pages.  It turned out, it was stuck in offline mode (I unticked "Work Offline" and then it worked) - I don't understand why Firefox wouldn't figure that out automatically (never had this issue in Firefox for Windows). Setting "toolkit.networkmanager.disable" to true fixed it, though.

So, now I was so relieved, I was finally online with Ubuntu (the hurdles related to dial-up/modem connectivity have been quite exhausting!), but then the connection dropped and since then I'm back to the original scenario where dialing doesn't do anything (can't hear any dial tone or dialing sounds) and it ends up saying NO CARRIER (see further above).

I have not changed any configuration between the one attempt that worked and now.  I have tried plugging in/out the cable, trying the Windows laptop (which does connect fine), trying various connection rates, "stupid mode", wait/no wait for dial tone, etc. and I'm now out of any other things to try.  Any suggestions or help much, much, much appreciated!

Cheers,
Tom

PS: Why am I writing all of this down?  So it just *may* help someone else ...and so, I can remember myself ;-)

PPS: I gave up on the internal Conexant-based soft modem/WinModem in the end and bought a PCMCIA-modem which works fine - see [http://ubuntuforums.org/showthread.php?p=6282592#post6282592](http://ubuntuforums.org/showthread.php?p=6282592#post6282592)

---

