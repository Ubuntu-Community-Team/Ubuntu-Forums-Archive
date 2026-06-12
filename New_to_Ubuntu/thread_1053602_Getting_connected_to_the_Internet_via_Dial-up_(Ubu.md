---
title: "Getting connected to the Internet via Dial-up (Ubuntu 8.0.4)"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by lexmetroid on 2009-01-28
Hello, all.

As a beginner with Ubuntu, I constantly run into obstacles. Most of the time, I am able to find a way to overcome them, but there is one problem that I cannot resolve, no matter what I try.

At the moment, I have both Windows XP and Ubuntu 8.0.4 installed on my approximately 3-year-old Compaq Presario. I would love to use Ubuntu for general tasks such as e-mail and web browsing, as Ubuntu boots up much faster than XP does, but there is one major problem: connecting to the internet.

I connect to the internet via dial-up. More specifically, AOL. Now, I understand that there is a tremendous amount of dislike for AOL, and many would recommend switching to another provider. I respect that opinion, but in my case, it is not possible. Currently, AOL's basic $9.95 plan is the only feasable method for connecting online.

For hours, I have scoured the net hoping to find an easy way to connect online via Ubuntu, but apparently no method truly exists. I would like to know if there is anyone who has been successful in connecting online via Ubuntu, and how that was acheived.

I have tried penggy, but I am unsure at how to use it correctly. I realize that it is a command-line based program, and that creates an enormous amount of difficulty. To make matters worse, I can only connect to the internet while using Windows XP, and therefore cannot directly download files from the net using Ubuntu.

If there are any easy to follow tutorials explaining how to connect to the internet using AOL as an ISP, it would be much appreciated. However, I have a feeling that even the best of tutorials would be difficult for me to understand. (Command line prompts are almost impossible for me to follow.) If possible, could a checklist be provided of what is necessary to get online using Ubuntu? 

For example, I know that these steps must be followed before connecting:

-Identifying the modem (Conextant HSF 56k Data / Fax Modem)
-Installing modem drivers (Still have not been able to successfully install these)
-Installing Penggy and modify the connection settings (Unsure how to accomplish this)

...but there may be other steps that I may have missed.

Ok, I think I'm done now.

Thanks in advance for any help! ;)

---

### Post by Arylon on 2009-01-28
I also have a Conexant modem. Dell makes closed-source modem drivers available, you can get the one for 8.0.4 at
[http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem_7.68.00.09oem_i386.deb]("http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem_7.68.00.09oem_i386.deb")
Once downloaded, just double click to install.

I'm not sure about Penggy, because I'm using [gnome-ppp]("http://packages.ubuntu.com/hardy/gnome-ppp") instead.

---

### Post by lexmetroid on 2009-01-28
Thank you for responding so quickly.

Should the Dell drivers work right out of the box, or are there any additional files that I may need to download?

Another question, is gnome-ppp compatible with AOL? Do I need any additional files to get gnome-ppp to work?

Thanks again!

---

### Post by Arylon on 2009-01-28
The drivers should work right out of the box. Same with gnome-ppp. All the files they need are part of the default Ubuntu install.

I believe AOL is compatible with standard dial-up software these days, so as long as you know your AOL login name, password, and telephone number you should be set.

---

### Post by mrbiggbrain on 2009-01-28
I rember there being a ppp like system just for AOL, iv had it before when i was attempting to connect on my ps3 over AOL (though i never got my modem up and running)

---

### Post by Arylon on 2009-01-28
I almost forgot something very important. The Dell modem drivers are very sensitive to the kernel version. I'm using kernel version 2.6.24-19, and I don't think the modem drivers work with newer versions of the kernel. So I usually have to ignore any package update where the package name starts with "linux-"

---

### Post by lkraemer on 2009-01-28
There is a good article in the December 2006 issue (page 12) of
PCLinuxOS magazine about configuration for AOL.  

[http://www.pclosmag.com/index.php?op...iles&Itemid=73](http://www.pclosmag.com/index.php?op...iles&Itemid=73)

Maybe it will help you with setting up AOL.

Internal modems can be a bugger.  Why not get a used USR 5686 External
Modem from Ebay and save yourself the trouble?

This may also help:
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)
osdir.com/ml/ubuntu.doc/2005-04/pdfuHGgEItwtF.pdf


wvdial info:
[http://en.wikipedia.org/wiki/Wvdial](http://en.wikipedia.org/wiki/Wvdial)
[http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)
[http://tldp.org/HOWTO/PPP-HOWTO/x314.html](http://tldp.org/HOWTO/PPP-HOWTO/x314.html)
[http://www.squarebox.co.uk/cgi-squarebox/manServer/wvdial.conf.5](http://www.squarebox.co.uk/cgi-squarebox/manServer/wvdial.conf.5)

If you don't have a serial port, or want to use a USB port check out
the following:

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a N82E16812156008
SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter Model SBT-USC1M - Retail @ $8.99.

These work wonderful with wvdial, etc.

Basically you will need to do the following:
Configure wvdial with:

sudo wvdialconf

the config file will be at /etc/wvdial.conf
to configure your ISP's telephone number, login & password etc.

You can later edit your personal information with:
$ sudo gedit /etc/wvdial.conf

Open a Terminal window (you will leave it open the total time
you will be connected via dialup)

dial out with:
$ wvdial

SURF!!!
You can go back to the open terminal window and do a CNTRL C
to terminate the connection/session, then close the terminal window.

lkraemer

---

### Post by antmenj on 2009-01-28
External modems are good.  Many people are throwing these out now.  Often available in op shops (second hand shops run by charitys etc).  No drivers to install.

If you have an old computer laying around like a pentium 1 you could build a smoothwall box and connect via network.  These are great for windows on dialup when you have to reboot reboot reboot every time you install stuff + with a router you can run many machines of a dialup connection + you have a firewall built in:D.

---

### Post by lexmetroid on 2009-01-29
I installed the Dell drivers, and downloaded and installed Gnome-PPP. Some progress was made, as the modem actually dialed out, but once connected it would instantly disconnect. I'll try and post the error log when possible.

Buying another modem really isn't in the cards at the moment, but the advice is appreciated nonetheless.

Thank you! :)

---

### Post by Paul_world10 on 2009-01-29
US Robotics makes a nice product for all your dial-up needs. 

the model number  is       5610b

---

### Post by editrix on 2009-01-29
> **lexmetroid said:**
> I installed the Dell drivers, and downloaded and installed Gnome-PPP. Some progress was made, as the modem actually dialed out, but once connected it would instantly disconnect.

The connection may be dropping because of authentication. Check your 
/etc/ppp/options file. If there's a line that says **auth,** change it to **noauth.** Back up your original first, and you'll have to be root to edit the file.

---

### Post by stalkingwolf on 2009-01-29
I  got one a couple months ago off craigslist. Just paid the postage.
Got one on ebay about the same time for 15.00 including postage. I had
both hooked up and 2 laptops online using Gnome ppp in about 15 min.
But then I use worldverge for dialup. regular and accelerated accounts
12.95 mo. regular is 9.95.

---

### Post by xbesnard on 2009-01-30
Hello to all,

   I use this driver for Hardy and it works perfectly with the DELL hsfmodem package. 

Hovewer, I would like to switch to Intrepid, but I didn't find any hsfmodem package.

     I tried many soulutions without success including that tuto [http://ubuntuforums.org/showthread.php?t=1015673]("http://ubuntuforums.org/showthread.php?t=1015673")

    Does some find a solution to operate that modem under Intrepid?

    Many thanks for your answers. Xavier

---

### Post by lexmetroid on 2009-02-09
Okay, so I'm back... with some good news!

I took a look at the article in the PCLinuxOS Magazine, and printed out the article. I followed the instructions, and with some minor tweaking, I was finally able to successfully connect to AOL with Ubuntu 8.0.4! Turns out that Penggy is actually pretty good for AOL dial-up... as long as you know how to use it.

So, I would like to take this opportunity to thank you all who contributed. I now know that AOL dial-up does work in Ubuntu, although I'm still not sure why this information isn't much easier to find - there are probably many others who have the same problem I had, and it would help them tremendously to read the article in PCLinuxOS.

All the best,

lexmetroid

---

### Post by lkraemer on 2009-02-09
lexmetroid,
Yes, the PCLinuxOS Article fits the bill, but I just accidentally
stumbled across it a month or so ago.  I've sent lots of PM's
to folks on this forum that had AOL and were wanting to get it operational.
But, most of those posts were a year old or older.  Just a few
were current.

Good to be able to help.

lkraemer

---

