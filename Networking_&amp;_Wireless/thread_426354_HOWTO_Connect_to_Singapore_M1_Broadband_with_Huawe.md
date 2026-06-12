---
title: "HOWTO: Connect to Singapore M1 Broadband with Huawei E220 USB Modem on Ubuntu Dapper"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by rykel on 2007-04-28
**_UPDATE (3 February 2008)**_

For both Huawei E220 (M1) and E270 (Starhub), you can now run the official **Vodafone Mobile Connect for Linux** here:
**[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)**

Look for the .deb file, install it accordingly and you will have a software just like the one in Windows.

The best part about using this VMC is that you do NOT need to reboot your PC everytime you unplug the Huawei.

I have personally tested the program with Starhub E270 and others have done so with the E220.

Good luck.


**_UPDATE (11 October 2007)_**

For those of you on Singapore Starhub MaxMobile and Ubuntu Linux Dapper Drake, simply:

[INDENT][LIST=1]
[*]Start your PC with the modem plugged in.
[*]Launch GNOME PPP. (See Screenshot)
Username: star
Password: hub
Phone Number: *99#
[*]Connect
[/LIST][/INDENT]

That's all!

NOTE: The M1 Broadband Huawei E220 is LOCKED, which is one reason why you cannot use the Starhub data card on it, and because it is on loan, it is illegal for you to unlock it. (Why would you, anyway?) The Starhub device is NOT locked, however.


**_ORIGINAL POST_**

Hi,

This post is for those of you who are using the M1 Broadband with the Huawei E220 USB modem in Singapore on Ubuntu Dapper Drake. Thanks to previous posters who have contributed to this subject.

All terminal commands are in **bold**.

1.	Deactivate Wireless, Ethernet (through System/Administration/Networking) and SIM card PIN request (OFF by default), if necessary.

2.	Set up the configuration files.
[INDENT][B]sudo chmod -c a+rwx /etc/wvdial.conf
sudo chmod -c a+rwx /etc/ppp/pap-secrets
sudo chmod -c a+rwx /etc/ppp/chap-secrets
sudo gedit /etc/wvdial.conf[/B] (just make sure it looks like the text below)

[Dialer hsdpa]
Phone = *99***16#
Username = 65
Password = user123
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
[/INDENT]
3.	Plug in the modem and eject the "CD-ROM".
[INDENT][B]sudo rmmod usb-storage
sudo modprobe usbserial vendor=0x12d1 product=0x1003
ls -la /dev/ttyU*[/B] (should give a list of USBs - must have!)
**wvdial hsdpa**
[/INDENT]
To start the modem after a reboot, simply plug in the modem, eject the "CD-ROM" and:
[INDENT]**sudo modprobe usbserial vendor=0x12d1 product=0x1003** (now plug in the modem)
**wvdial hsdpa**[/INDENT]

[I]NOTE: If you do not want to remove usb-storage, you might like to check out the E220 Activator at
[INDENT][http://www.kanoistika.sk/bobovsky/archiv/umts](http://www.kanoistika.sk/bobovsky/archiv/umts)[/INDENT]

Simply go into the folder containing the files, then:
[INDENT][B]sudo ./huawei*386.out
cat /proc/bus/usb/devices[/B][/INDENT][/I]

Now, I need YOUR help... does anybody know how to:

[INDENT]1.	Start up the modem using GNOME-PPP or the default Network Settings?
2.	Track the data usage. (see Note below)[/INDENT]

NOTE: Kindly be informed that M1 Broadband is **NOT** an unlimited plan. It has a cap of 5GB data usage per month (yes, IMHO a miserable 5GB per month) and if you use the service in Linux, I do not know of a way to keep track of your usage.

---

### Post by arti47 on 2007-05-06
Hi, I seem to be having problems even after following your guide. Really appreciate if someone can provide me with some help... :) thanks!

I post the error msg i get in the terminal after the wvdial hsdpa command:

--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99***16#
--> Waiting for carrier.
ATDT*99***16#
ERROR
--> Invalid dial command.
--> Disconnecting at Sun May  6 22:03:39 2007

anyone knows what I did wrong?

---

### Post by rykel on 2007-05-06
Could I have a look at your **/etc/wvdial.conf** file please?

---

### Post by arti47 on 2007-05-07
Hi... this is all that is in my wvdial.conf file:

[Dialer hsdpa]
Phone = *99***16#
Username = 65
Password = user123
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

thanks so much!

---

### Post by rykel on 2007-05-07
> **arti47 said:**
> Hi... this is all that is in my wvdial.conf file:

[Dialer hsdpa]
Phone = *99***16#
Username = 65
Password = user123
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

thanks so much!

It seems like you are just one step away from success, since your wvdial.conf file is virtually the same as mine, and your PC is apparently dialing the modem already... It seems like your problem lies in either the "Phone=" or "Dial Command=" line.

Try changing the phone number to:
[INDENT]**Phone = *99***8#**[/INDENT]
and see if it works. (the number was given to me by a M1 staff)

---

### Post by arti47 on 2007-05-07
Hi,

Still not working! Haha... i also don't noe wat is the problem. Did you call M1 to ask about the number? What does the Dial Command, the user, password and the Phone mean anyway?

---

### Post by arti47 on 2007-05-07
Hi!

I changed the Phone to Phone = *99***1# and i was able to connect immediately! 

Thanks so much for your help! Really appreciate the time taken to help me narrow down the problem! Yipee

---

### Post by rykel on 2007-05-07
> **arti47 said:**
> Hi!

I changed the Phone to Phone = *99***1# and i was able to connect immediately! 

Thanks so much for your help! Really appreciate the time taken to help me narrow down the problem! Yipee

Hey congratulations!

Well, I have no idea why the change in phone number works, but well, it works!   :lolflag: 

Seriously, perhaps it is the plan you are on... each SIM card (ie. Phone number) is tagged to a Phone Number for dialing in, I believe. In your case, your dial-in number is "xxxxxx1#".

Just for your information, the Phone Number refers to the number for your modem to dial in to, Username and Password obviously refers to the username and password that is recognised by the phone your modem is dialing in to and the Dial Command defines the type of dialing your modem is making. (ATDT probably stands for AT Dialing TONE. The other type is Dialing PULSE. Look under any residential phone, and you should be able to find the 2 types of dialing function.)

p/s. Check out [http://www.ubuntu.sg](http://www.ubuntu.sg) for the Singaporean Ubuntu community.

---

### Post by arti47 on 2007-05-07
Ahh.. i see. Thanks thanks! I'll check out the site too!

---

### Post by richardjackson on 2007-05-31
Hi

I am using Vodaphone Unlimited tariff in the UK and have used this procedure in conjuntion with 

the E220 Activator at
[http://www.kanoistika.sk/bobovsky/archiv/umts](http://www.kanoistika.sk/bobovsky/archiv/umts)

as I was unable to see and eject the cdrom aspect of the e220 .. and it works very well and reliably ..

Just a note of thanks to you guys ...

Richard Jackson

---

### Post by aseem on 2007-06-02
I have been reading this and other topics on this forum, but can't seem to get my Huawai E220 to work.  It works on Windoze with the bundled winApp.  btw, I'm using Netcom in Norway.

This is the output from wvdial:
[PHP]ase@ase-ubu:~$ wvdial hsdpa
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
[/PHP]


Here is a copy of my wvdial.conf file.
[PHP]ler Defaults]
Phone = *99#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer hsdpa]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
[/PHP]

ls -la /dev/ttyU*  only lists ONE ttyUSB device

I could really need som help on this, and appreciate any suggestions.

---

### Post by svenkatesan on 2007-06-02
[http://ubuntuforums.org/showthread.php?t=346766](http://ubuntuforums.org/showthread.php?t=346766)

see here,this is how I made it work..in Singapore.
Hope this helps.

---

### Post by svenkatesan on 2007-06-03
see here too..
[http://ubuntuforums.org/showthread.php?t=354670](http://ubuntuforums.org/showthread.php?t=354670)

---

### Post by oozie on 2007-06-15
Hi Everybody! 

If you dont want to get into details or dont want to play with HUAWEI e220 again after reinstallation, take a look at my little project:

[http://oozie.fm.interia.pl/pro/huawei-e220/](http://oozie.fm.interia.pl/pro/huawei-e220/)

I tested it today on Ubuntu 6.06 (old one, I know) and it worked out of the box. The package also contains configuration files for pppd and wvdial, so the next thing you do after "make install_ubuntu" and replugging your USB modem is connect to the internet! 

pppd call huawei-e220

And you are there!

---

### Post by rykel on 2007-06-21
> **oozie said:**
> Hi Everybody! 

If you dont want to... [http://oozie.fm.interia.pl/pro/huawei-e220/](http://oozie.fm.interia.pl/pro/huawei-e220/)


brother, your website link does not work...

one minor hassle i have currently is that the PC needs to reboot (and with the huawei plugged in) in order to "activate" the modem... otherwise, i get a "modem not responding" problem... along with that, if i disconnect it using CTRL-C, i might not be able to start it again, and then have to reboot as just mentioned.

---

### Post by elfgoh on 2007-06-22
Hi check out this blog post:

[http://www.tectonic.co.za/view.php?id=1596](http://www.tectonic.co.za/view.php?id=1596)

Basically u can try the driver from 

[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)

Works like a charm. So no more tinkering with wvdial. Just need to change APN host to sun surf.

However, currently I have a problem. When I want to check internet stats, the program just opens an empty page on firefox. Is this happening to any1 else?

---

### Post by rykel on 2007-06-22
> **elfgoh said:**
> Hi check out this blog post:

[http://www.tectonic.co.za/view.php?id=1596](http://www.tectonic.co.za/view.php?id=1596)

Basically u can try the driver from 

[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)

Works like a charm. So no more tinkering with wvdial. Just need to change APN host to sun surf.

However, currently I have a problem. When I want to check internet stats, the program just opens an empty page on firefox. Is this happening to any1 else?

Hi, I would indeed like to use the software you recommended, because rebooting the PC just to "reset" the Huawei for wvdial is getting on my nerves... however, the program you mentioned only caters to Edgy and Feisty... could you please make a version for Dapper? Thank you!!!

---

### Post by oozie on 2007-06-22
Hi ! 

> **rykel said:**
> brother, your website link does not work...

Thanks for checking anyway, rykel. Well it's a non-profit business and I'm hosted on a non-profit ISP, which is down for the last 24hours and nobody knows when it's going to be up again. The only thing I can offer you in reference to huawei e220 is an alternate location of the package. Please download [SIZE="3"]**[huawe.tar.bz2 from here]("http://hackpospolita.webpark.pl/huawei.tar.bz2")**[/SIZE], or visit my blog post, which tells about the actual status of the package: 

[http://thewinningmove.blogspot.com/2007/06/huawei-e220-hsdpa-3g-modem-in-linux.html](http://thewinningmove.blogspot.com/2007/06/huawei-e220-hsdpa-3g-modem-in-linux.html)

Meanwhile the udev rule was tested on 3 different Ubuntu's (among other linuxes ofcourse) - 6.06, 6.10, 7.10 and works fine for all of them.
The sample log from installation of it will be available [**here**]("http://oozie.fm.interia.pl/data/huawei.log"), right away after my site is up again. I'm terribly sorry for all inconvenience. I promise you, that on these pages you will not come across any stupid advertisements, popups g-ads or whatever.

---

### Post by rykel on 2007-06-23
> **oozie said:**
> Hi ! 



Thanks for checking anyway, rykel. Well it's a non-profit business and I'm hosted on a non-profit ISP, which is down for the last 24hours and nobody knows when it's going to be up again. The only thing I can offer you in reference to huawei e220 is an alternate location of the package. Please download [SIZE="3"]**[huawe.tar.bz2 from here]("http://hackpospolita.webpark.pl/huawei.tar.bz2")**[/SIZE], or visit my blog post, which tells about the actual status of the package: 

[http://thewinningmove.blogspot.com/2007/06/huawei-e220-hsdpa-3g-modem-in-linux.html](http://thewinningmove.blogspot.com/2007/06/huawei-e220-hsdpa-3g-modem-in-linux.html)

Meanwhile the udev rule was tested on 3 different Ubuntu's (among other linuxes ofcourse) - 6.06, 6.10, 7.10 and works fine for all of them.
The sample log from installation of it will be available [**here**]("http://oozie.fm.interia.pl/data/huawei.log"), right away after my site is up again. I'm terribly sorry for all inconvenience. I promise you, that on these pages you will not come across any stupid advertisements, popups g-ads or whatever.

Hi Bro,

I am sorry but I have no idea how to install/activate the program you wrote... would you be able to release an autopackage ([http://www.autopackage.org](http://www.autopackage.org)) version as well, so that it is just a graphical click and install for newbies like me?

Meanwhile, could you please advise me on what I should do to set up the driver? Thank you!

---

### Post by elfgoh on 2007-06-23
> **rykel said:**
> Hi, I would indeed like to use the software you recommended, because rebooting the PC just to "reset" the Huawei for wvdial is getting on my nerves... however, the program you mentioned only caters to Edgy and Feisty... could you please make a version for Dapper? Thank you!!!

So sorry, I have no idea how to make deb  packages. But you could compile from source. Or even try using deb packages from earlier packages.

Btw, y aren't u upgrading to edgy or feisty? I upgraded from dapper to edgy to feisty. Seems fine to me. Stable and faster too.

---

### Post by oozie on 2007-06-23
Hi! 

> **rykel said:**
> Hi Bro,
I am sorry but I have no idea how to install/activate the program you wrote... would you be able to release an autopackage ([http://www.autopackage.org](http://www.autopackage.org)) version as well, so that it is just a graphical click and install for newbies like me?


I get what you are saying, but I rather include four lines you need to put from the console in order to install it.
Ubuntu is still a unix-like system, where tarballs is something sooner or later you will have to do with.

1. You download the package [**huawei.tar.bz2**]("http://hackpospolita.webpark.pl/huawei.tar.bz2") to your home directory
2. You open the terminal window or you press CTRL+ALT+F1 and login
3. You should be in your home directory now. Put the following from the command line:

```
$  sudo bash
# tar xjvf huawei.tar.bz2
# cd huawei
# make install_ubuntu

```
4. You replug or reboot your PC 
5. Now you can test the configuration from the COMMAND LINE too! (In case something goes wrong,
I will know exactly what was that, you know) by logging as yourself and typing
```
$ sudo pppd call huawei-e220
or 
$ sudo wvdial --config /etc/wvdial-huawei.conf.

```
It's not really a program, it's a rule for UDEV system, which 'activates' your modem without a need
for installing anything.

---

### Post by rykel on 2007-06-26
Hi ladies and gentlemen,

Just wanted to report back here that the huawei script by oozie works better (apparently) than the "wvdial hsdpa" method I initially proposed, in that now, I simply need to plug in the modem, leave it plugged in (no need to detach) and the following 2 commands are bound to activate it:

$ sudo modprobe usbserial vendor=0x12d1 product=0x1003
$ sudo wvdial --config /etc/wvdial-huawei.conf

In the past, if I disconnect the modem using Ctrl-C, I have to reboot the PC with the item plugged in in order to reactivate it. NO GOOD (TM).   :popcorn:

---

### Post by oozie on 2007-06-28
Hi! 

Short update:
I've just published statistics interface for HUAWEI.
[IMG]http://oozie.fm.interia.pl/img/he220stat.jpg[/IMG]
Program available here: [http://oozie.fm.interia.pl/pro/huawei-e220/]("http://oozie.fm.interia.pl/pro/huawei-e220/")

Best Regards,
OOZIE

---

### Post by elfgoh on 2007-07-11
> **elfgoh said:**
> Hi check out this blog post:

[http://www.tectonic.co.za/view.php?id=1596](http://www.tectonic.co.za/view.php?id=1596)

Basically u can try the driver from 

[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)

Works like a charm. So no more tinkering with wvdial. Just need to change APN host to sun surf.

However, currently I have a problem. When I want to check internet stats, the program just opens an empty page on firefox. Is this happening to any1 else?

Well just to update, the driver from vodafone works great.

And I found a solution to the resetting of computer to detect the modem.

Not sure about the others, but my modem when just on will show green light (seems to be starting up status) . After that will show blue light (seems to be ready status). I notice that sometimes the modem hangs my pc.

So I connect the modem to an externally powered usb hub. On the hub, wait for the light to be blue, then on the pc. Problem solved.

Sometimes the network goes down. So I disconnect the hub from the pc, off and then on the hub to re-initialise the modem, then plug back the hub when the light is blue. This works and modem is correctly detected. Previously had to restart the pc.

Perhaps some1 can try and tell me if this help you too.

---

### Post by rykel on 2007-09-28
Hi all,

I just bought a Starhub data card, and will experiment with it to see if it will work with the M1 Huawei E220... the Starhub modem, as those of you from Singapore knows, is the Huawei E270.

If you have already successfully logged onto the Starhub network using the M1 E220 modem, please post your experience here.

btw, according to Starhub staff, the Starhub dial-up number is *99#.

Hope this leads somewhere!

---

### Post by rykel on 2007-09-28
Hi all,

This is the information I managed to gather about the Starhub MaxMobile service.

    Phone = *99#

    Username = star

    Password = hub


HOWEVER, I cannot use the Starhub card with the M1 Vodafone Huawei E220 modem as the device has been locked by M1, as usual. On the other hand, it is my understanding that you can use the data card from ANY provider on the Huawei E270 sold by Starhub.

If you factor in the unlimited usage with 6 months of free use and the free Huawei E270 modem, then the 24-month contract with Starhub does seem like a good deal.

Then we will need to rename this thread to "HOWTO: Connect to Singapore M1 Broadband and Starhub MaxMobile with Huawei E220 and E270 USB Modems".

:lolflag:

---

### Post by manualvin on 2007-10-03
Hi i just signed on for the starhub plan yesterday, worked well but i doubt that it actually goes up to 7.2 as it advertises.

Still, it's a good plan which is unlimited, versus the other 2 competitive offerings.

Is there any linux driver on ubuntu that will work with the Starhub Huawei e270 3.5G modem? Anyone tried?

Cheers

---

### Post by rykel on 2007-10-11
Hi pals,

Once again, Starhub forever!!

To use Starhub-Huawei E270 in Ubuntu Linux Dapper Drake, simply:

[INDENT][B][LIST=1]
[*]Start your PC with the modem plugged in.
[*]Launch GNOME PPP.
Username: star
Password: hub
Phone Number: *99#
[*]Connect
[/LIST][/B][/INDENT]

That's all!

btw, the M1 Broadband Huawei E220 is LOCKED, which is one reason why you cannot use the Starhub data card on it. (Why would you, anyway?) The Starhub device is NOT locked, however.

And yes, the speed can make it.    :guitar:

---

### Post by capiscuas on 2007-12-22
Just a brief comment. M1 broadband plan is now unlimited.:popcorn:

---

### Post by capiscuas on 2007-12-22
I've just installed the .deb package from the Official GPL linux driver from Vodafone and it works like charm (see screenshot). I went out of my mind when I saw the software offering to login to M1 Broadband (it recognized automatically). And the best of all, it's GPL. Thks to vodafone Spain team.

Driver:
[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)

---

### Post by duxton88 on 2007-12-30
I'm using the Singtel Mobile Broadband Huawei E220 modem.  Anyone knows if it will work on Feisty?
I'm a noobie here so any help is appreciated!  Thanks and have a nice day.

PS  I tried plugging the modem into the USB port but it doesn't seem to work.

---

### Post by rykel on 2008-02-01
> **capiscuas said:**
> I've just installed the .deb package from the Official GPL linux driver from Vodafone and it works like charm (see screenshot). I went out of my mind when I saw the software offering to login to M1 Broadband (it recognized automatically). And the best of all, it's GPL. Thks to vodafone Spain team.

Driver:
[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)

Hi,

Have you tried the Official Linux driver from Vodafone with the StarHub MaxMobile Huawei E270?

---

### Post by capiscuas on 2008-02-01
I haven't try, pls try it first. Or put a question into their forum.
[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)

---

### Post by rykel on 2008-02-02
> **capiscuas said:**
> I haven't try, pls try it first. Or put a question into their forum.
[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)

Tried. It works. Wonderfully.    : )

---

### Post by meepok88 on 2008-02-27
I am using Singtel Huawei E220 too. It works on Gutsy. 

If Feisty kernel is version 2.6 then it should not be a problem. The connection is very straight forward. Make sure you connect the modem when you started up. It doesn't work by hot-plug. 

If you are using old PC, like mine P3, with USB 2 adapter, make sure you connect     it to USB 1.0. The modem doesn't work on the USB 2.0 adapter and I don't know why.

The wvdial.conf is locate at /etc/ 

You can cut and paste the below wvdial.conf

Here is the wvdial.conf I use:

      [Dialer anyname-you-like]
     # replace the anyname-you-like to your choice

     Phone = *99#
     Username = 123
     Password = 123
    Stupid Mode = 1
    Dial Command = ATDT
    Modem = /dev/ttyUSB0
    Baud = 115200
    Init2 = ATZ
    Init3 = ATQ0V1E1S0=0&C1&D2+FCLASS=0
    INIT5 = AT+CGDCONT=1,"IP","internet"
    ISDN = 0
    Modem Type = Analog Modem

#### end ###


At the terminal window, just type:

      sudo wvdial anyname-you-like

To terminate the connection: ctrl C

Hope this help.

> **duxton88 said:**
> I'm using the Singtel Mobile Broadband Huawei E220 modem.  Anyone knows if it will work on Feisty?
I'm a noobie here so any help is appreciated!  Thanks and have a nice day.

PS  I tried plugging the modem into the USB port but it doesn't seem to work.

---

### Post by turbolink on 2008-05-12
Thanks a lot, meepok88! This worked nicely for Ubuntu 8.04 on AMD 64 with Huawei E220

---

### Post by junionwoon on 2008-06-13
Hi,

Can anyone help? I initially installed the vodafone mobile Connect card driver. After that I was able to authenticate the card but unable to connect. 

So I tried the configuration steps from the first post but I have the following messages after performing the steps indicated...

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Jun 13 13:47:34 2008
--> Pid of pppd: 7165
--> Disconnecting at Fri Jun 13 13:47:34 2008
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)


And after this, i tried to use the vodafone mobile connect card driver program again and received permission denied messages indicating that the chap-secrets and pap-secrets need to have mode 0660 mode but now is 0777.

Please help. THanks.

---

### Post by beerboi85 on 2008-07-22
hi all, i just had the singtel huawei usb thing. I've also downloaded and installed the vodafone mobile connect program. I could connect but i couldn't get firefox to load any page? Can someone please tell me how to solve this problem? thanks a lot :)

---

