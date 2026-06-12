---
title: "HP 6310 Printer Problems..."
date: 2011-04-15
forum: New to Ubuntu
---

### Post by WarbyK8 on 2011-04-15
Hey Ubuntu Crew!
Name is Kate and about a month into Ubuntu - which I LOVE!  Have Printer which is giving me grief!  Two things are happening:
1. Have to keep going into Printer Properties and ticking 'enabled' nearly every time I'm trying to print
2. Document will print 1/2 page and then stop
Any clues how to fix this problem?
Thx K8
:rolleyes:

---

### Post by cavh on 2011-04-15
1. Go System, Administration, Hardware Drivers and see if any new drivers are available for installation. This may well not fix the problem because I think the HP drivers are baked in to the kernel, i.e. they are not proprietary.

2. Presuming that doesn't fix it, check out [http://hplipopensource.com/hplip-web/index.html]("http://hplipopensource.com/hplip-web/index.html")

3. welcome to the forums!

---

### Post by herdivet on 2011-04-18
I am having the same problem as WarbyK8 on a PC I set up with Mint10 for my neighbor.  I was tired of supporting his Windows PC so I convinced him to go with Mint.  He's happy with everything except this printer problem.  He's even willing to just buy a new printer since his OJ6310 is rather old.

I followed the link, I found another report of the problem in Launchpad at
[https://answers.launchpad.net/hplip/+question/151936](https://answers.launchpad.net/hplip/+question/151936)

but I didn't find any answer to it.  

I did have a question for WarbyK8 - when you're printing, is it a PDF document as well?  I don't have 24x7 access to my neighbors PC so I can't try a multi-page document, so it *might* be a problem with the document-reader program.  I'm not confident this is it, because the last thing I tried with his was to print a test page, and it stopped halfway through and disabled the printer...  :<

I hesitate to recommend a new printer, most HP models *should* work with Linux, so this is confounding me.  I don't see many reports of problems with this model, so I'm wondering if it's something in Mint 10 or the kernel release it's on?

Anyone who has a solution, it would be most welcome.

---

### Post by Locke_99GS on 2011-04-18
My HP printer worked in Lucid after getting the latest HPLIP, and in Maverick out of box. My only suggestions would be to use the above-mentioned website to make sure you have an adequately recent HPLIP fo ryour printer, and if not, get the latest. (Might get the latest anyways?)

Remove and reinstall *hplip*, and run *hp-setup* 

Thats the only advise I can offer. Sorry - Hope it works out for you.

---

### Post by herdivet on 2011-04-18
Thanks Locke_99GS, I downloaded the latest version of hplips, however when I went to install it, the installation reported that a dependency for GCC was not met and requested it be installed.  I ran sudo-apt get install gcc and was told that the most recent version is already installed.

---

### Post by sandyd on 2011-04-18
> **herdivet said:**
> Thanks Locke_99GS, I downloaded the latest version of hplips, however when I went to install it, the installation reported that a dependency for GCC was not met and requested it be installed.  I ran sudo-apt get install gcc and was told that the most recent version is already installed.
Copy and paste into Applications -> Accessories -> Terminal.
Password doesn't show up when your typing it.
For the HP setup, just press enter for each option to accept defaut.
```

sudo apt-get remove hplip hplip-*
sudo apt-get install build-essential
sudo apt-get build-dep hplip
cd ~
wget -c http://surfnet.dl.sourceforge.net/project/hplip/hplip/3.11.3a/hplip-3.11.3a.run
bash ./hplip-3.11.3a.run

```

---

### Post by WarbyK8 on 2011-04-19
> **herdivet said:**
> I am having the same problem as WarbyK8 on a PC I set up with Mint10 for my neighbor.  I was tired of supporting his Windows PC so I convinced him to go with Mint.  He's happy with everything except this printer problem.  He's even willing to just buy a new printer since his OJ6310 is rather old.

I followed the link, I found another report of the problem in Launchpad at
[https://answers.launchpad.net/hplip/+question/151936](https://answers.launchpad.net/hplip/+question/151936)

but I didn't find any answer to it.  

I did have a question for WarbyK8 - when you're printing, is it a PDF document as well?  I don't have 24x7 access to my neighbors PC so I can't try a multi-page document, so it *might* be a problem with the document-reader program.  I'm not confident this is it, because the last thing I tried with his was to print a test page, and it stopped halfway through and disabled the printer...  :<

I hesitate to recommend a new printer, most HP models *should* work with Linux, so this is confounding me.  I don't see many reports of problems with this model, so I'm wondering if it's something in Mint 10 or the kernel release it's on?

Anyone who has a solution, it would be most welcome.
Hello There!

Yep, having problems with printing PDF's as well!...

---

### Post by WarbyK8 on 2011-04-19
Thank you for all your responses to my cal for assistance!  Guys, let to need you know one thing..... I am NOT a computer guru, therefore all your wonderful suggestions are in another language! :confused: 

I'm reading all the info, yet I don't understand how to apply it.  Do they have an 'Ubuntu for Dummies book'?! :-k 

I can follow step by step instructions OK though! :P

Many thx once again ):P
K8x

---

### Post by herdivet on 2011-04-20
Sandyd - I was unable to get the build-dep hplip to run successfully.  

I found this forum had a response that worked for me.

[http://forums.linuxmint.com/viewtopic.php?f=51&t=25762&p=411191#p411191](http://forums.linuxmint.com/viewtopic.php?f=51&t=25762&p=411191#p411191)

You go to localhost:631 and add the printer.  I choose he 6300 series and the 3.10.6 driver and it appears to be working fine now.

I can't guarantee anything, but you might want to try this Warbyk8.  Once you put 'localhost:631' in your web browser you'll be able to click on the choices to install the printer.  

Good luck!

---

### Post by sandyd on 2011-04-20
> **herdivet said:**
> Sandyd - I was unable to get the build-dep hplip to run successfully.  

I found this forum had a response that worked for me.

[http://forums.linuxmint.com/viewtopic.php?f=51&t=25762&p=411191#p411191](http://forums.linuxmint.com/viewtopic.php?f=51&t=25762&p=411191#p411191)

You go to localhost:631 and add the printer.  I choose he 6300 series and the 3.10.6 driver and it appears to be working fine now.

I can't guarantee anything, but you might want to try this Warbyk8.  Once you put 'localhost:631' in your web browser you'll be able to click on the choices to install the printer.  

Good luck!
oops.
my bad.
Im not a ubuntu user (I use gentoo), so its quite easy to forget that your supposed to enable the source packages as well (uncomment the deb-src lines in /etc/apt/sources.list) before attempting that.
doh!

---

