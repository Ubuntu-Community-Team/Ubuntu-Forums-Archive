---
title: "What modem for dial up with ubuntu 8.04"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by copas on 2009-01-04
I have been unable to get ubuntu 8.04.1 LTS to recognize my modem. It is an: ESS ES556H-P1
I have gone through downloading scanmodem and have been unable to make it work. so:
I have dial up and wondered if anyone else has used this modem?
Also If I buy another modem; What brand do you have experience with? So I can be confident it will work for me.
Thanks for any advice.
Copas

---

### Post by cmnorton on 2009-01-05
Is your modem a WinModem? If it is, it's going to give you trouble. I cannot remember if there are Linux drivers available that will now support WinModems, but you need a modem that has all the stuff built-in. WinModems rely on Windows drivers to do a lot of their work.

---

### Post by wizard10000 on 2009-01-05
Winmodems work with Linux - at least some of them do.

Look here -

[http://www.faqs.org/docs/Linux-HOWTO/Winmodems-and-Linux-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Winmodems-and-Linux-HOWTO.html)

and here -

[http://linmodems.org](http://linmodems.org)

Good luck -

---

### Post by Lisa Y on 2009-01-05
...modem...

---

### Post by copas on 2009-01-05
> **Lisa Y said:**
> ...modem...

eh???

---

### Post by ModelM on 2009-01-05
My advice would be to abandon your ESS modem & purchase a hardware modem. You may get your ESS modem working after finding & compiling the correct driver files. But, even then, you are always dependent on being able to re-build your driver every time there is a new kernel update. If some change in the new kernel breaks your driver, it also breaks your modem.

You don't say what options you have for connecting your modem. There are not many internal PCI modems which are hardware modems, but the USR 5610 is one & works very well.

If you have an RS232 serial port, you have many choices. Lots of folks are using the Trendnet TFM-560X. It is a reasonable price & works very well. The US Robotics Sportster model 5686 is one of the most popular modems on the planet. But any modem connecting via RS232 should work.

For modems connecting via USB, you need to be more careful. Not all USB modems are hardware modems. The US Robotics USR5637 is one and also the Rosewill RNX-56USB. Either of these modems work perfectly in Ubuntu 8.10. I own one of each.

EDIT: The Rosewill modem mentioned above will not work out-of-the-box with Ubuntu 8.04 as it's not supported in the Kernel. I did not see until I posted that you are running 8.04. I have used the US Robotics USR5637 in 8.04 & it works quite well.

When you are shopping watch for phrases like "hardware modem" or "controller based", these indicate a hardware modem which would work under Linux.

---

### Post by lkraemer on 2009-01-05
It is easy to use a USB to serial Adapter to get a functional
serial connection for an External USR Modem.

The Softmodems and Internal modems can be a bugger, so why not
look on Ebay for an External USRobotics USR5686D, then Flash it to
the latest firmware, and use a USB to Serial Converter to get
online via Dialup using wvdial. Granted it's extra equipment, more cables,
Wall Wart, and Serial Cable but it at least works Great. Ebay has
them for ~$20.00 at times.

The USB to Serial Converter is from www.newegg.com and is a N82E16812156008
SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter Model SBT-USC1M - Retail @ $8.99.

These work wonderful with wvdial, etc.

you will need to do a
sudo wvdialconf
the config file will be at /etc/wvdial.conf
to configure your ISP's telephone number, login & password etc.

You can later edit your personal information with:
$ sudo gedit /etc/wvdial.conf
and dial out with:
$ wvdial
in a terminal window.....just leave that terminal window open for
the time you are connected. You can go back to the open window
and do a CNTRL C to terminate the connection. I think you will
be surprized by the speed if you migrated from XP w/Dialup.

lkraemer

---

### Post by s3a on 2009-01-05
Try using Dell's .deb modem drivers. Not so long ago when I was a dial-up user, they worked for me in 32 bit and 64 bit!

---

### Post by helmut_hed on 2009-01-07
copas, I have a HOWTO on the ESS modem driver:

[http://ubuntuforums.org/showthread.php?t=185079](http://ubuntuforums.org/showthread.php?t=185079)

Unfortunately it is a little out of date and now it is so old I cannot edit it... however, the instructions are correct if you get this file:

[http://tx.technion.ac.il/~raindel/ess_2.6-v0.5.tar.gz](http://tx.technion.ac.il/~raindel/ess_2.6-v0.5.tar.gz)

I cannot be sure from the information you have given whether your modem is supported, but the HOWTO will tell you how to know for sure.

Good luck,
Jeff

---

### Post by slibuntu on 2009-01-07
Jesus, my heart is with you having to use dial up.

---

### Post by oldsoundguy on 2009-01-07
All good recommendations, but to save the time and grief, An external USRobotics Sportster v.92 will install out of the box and continue to work forever! (they are cheap on eBay!)

I just put mine away in 2007 after years of living on a Linux box of one kind or another. Since I was able to FINALLY go wireless and broadband on every computer in the place (I LOVE D-Link 520 wireless cards for Linux .. another that installs out of the box on a desktop!)

---

### Post by Muldarfbi on 2009-01-07
Hi Peoples...I just installed a USRobotics USB5637. But I don't know how to make it work, that's if it will...

Thanks in advance for the help.

Muldarfbi,

---

### Post by Muldarfbi on 2009-01-15
Hello everyone...

I installed a USRobotics USB Modem on my linux box...Ubuntu 8.10 Intrepid Ibex 64bit. I got it to connect but it only stays connected for a bout 3 seconds...can someone help please?

Thanks in advance for the help...

Muldarfbi...):P

---

### Post by lkraemer on 2009-01-15
You say it connects......but don't you mean the modem goes off hook,
then dials, and it never make a complete connection with your ISP?

Do you get an error message? NO CONNECTION or such?

Are you using wvidal in a Terminal window to establish the connection?
Are you leaving the Terminal window open during the session, and
terminating the session with CONTROL C?

You can also quickly pick up the handset after the modem dials, and
listen to the carrier to see if the connection is being dropped or
your ISP is answering.  It gives you an idea of what is going on.

You might have a wrong setting for your login or password in
your wvdial configuration file.  You did configure wvdial didn't you?

You using CHAP or PAP?  Is pppconf set properly for your ISP?

lkraemer

---

### Post by Muldarfbi on 2009-01-15
I'm sorry, I forgot to mention that I used GnomePPP to dial in. But yes I had already setup wvdial but it would not connect with my ISP (aol)...It shows gnomeppp dialing the number, and after a few seconds it says connected...then it shows how long I have been connected which is 3 seconds then it disconnects.

Thanks for the quick reply...
Muldarfbi...

---

### Post by ieee488 on 2009-01-15
[http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html)

looks like it isn't straightforward to use dialup to AOL from Linux

---

### Post by oldsoundguy on 2009-01-15
AOL's default browser is IE.  You can't get to some places on their site using anything BUT IE as that is the only one they support.

DUMP AOL!!  get a real ISP (at a cheaper rate).  You can keep your AOL mail (at no charge, I believe).

---

### Post by ieee488 on 2009-01-15
I know for a fact AT&T Worldnet is Linux-compatible. I used it before switching to Verizon DSL in 2007.

---

### Post by Muldarfbi on 2009-01-16
Hey oldsoundguy...

What and where is a good ISP?  I want to get away from AOHELL!

Thanks in advance for the help...

Muldarfbi...

---

### Post by Muldarfbi on 2009-01-16
Off topic...(sorry)

I am running Ubuntu 8.10 Intrepid Ibex 64bit,
I also have the full 18 or 19 disk of Debian 3.1.
Can I use the Debian disk on Ubuntu?

Thanks...

Muldarfbi...:confused:

---

