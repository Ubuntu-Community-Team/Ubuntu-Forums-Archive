---
title: "Epson Stylus printing problem."
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by kikapu on 2007-05-03
Hi to all,

i am trying to use my printer on Feisty and i have not luck whatsoever.
This printer is an Epson Stylus Photo R300 one, it is attached to my router (i connect to this printer at:   [http://192.168.0.1:1631/printers/EpsonStylus](http://192.168.0.1:1631/printers/EpsonStylus) )and it is working correctly when used under Windows.

In Feisty, i go to the System/Administration/Printing and through the wizard i choose the correct model, i choose the driver from the combo box ("High Quality Image (Gutenprint CUPS) (Simple) and then i have my printer displayed as "Default" and ready.

But it can never print anything...At the "Connection" tab on printer properties, i see that it's type is declared as 'IPP printer or printer on CUPS server (IPP)". At the "General" tab, says that printer is off-line.

I am stuck...Has anybody any idea for this, what i am doing wrong or what else must be done so i can use the printer ??

---

### Post by kikapu on 2007-05-04
No one is using that kind of printer here ? I bet even a similar one will just do!

---

### Post by chili555 on 2007-05-04
192.168.0.1 looks like the IP address of your router, not a device *attached* to your router. What is the IP address of the printer under Windows?

---

### Post by kikapu on 2007-05-05
The printer is usb-attached to the router (modem-router). I use the same configuration when i print under windows, i do not change anything. In the same way i access the internet, with the same ip addresses both declares in Windows and Ubuntu.

Any ideas ??

---

### Post by lazyart on 2007-05-05
Are you specifying the port (:1631) with the IP address in Ubuntu?  If so, have you tried it without?  Or vice versa?

Also, check out this bug report: [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/57822](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/57822)

---

### Post by kikapu on 2007-05-05
I use the [http://192.168.0.1:1631/printers/EpsonStylus](http://192.168.0.1:1631/printers/EpsonStylus) to connect to the printer, in Windows is working just fine and is a, well, standard way to access printers in this configuration.

I will check at the link above. It's just that i have solved "problems" like Bluetooth, development software and all these and ijust  cannot print anything...:(

---

### Post by kikapu on 2007-05-06
I enabled the SSH service on the router to no avail...I checked the above link about downgrading the cups software and i am not sure that is the right thing to do in Feisty...
It's a pity though, i never have thought that printing will be such a problem...

---

### Post by chili555 on 2007-05-06
I think the problem is port 1631. CUPS expects all printing to use port 631. For example, if you open a browser and type:```
http://localhost:631
```The CUPS admin pages pop up. Try the same with localhost:1631 and you get nothing.

Just to satisfy yourself, try:```
http://192.168.0.1:**631**/printers/EpsonStylus
```I don't think it matters what works perfectly in Windows here; we want it to work perfectly in Ubuntu. Please post back so other network printing noobs will know the outcome.

---

### Post by kikapu on 2007-05-06
> **chili555 said:**
> I think the problem is port 1631. CUPS expects all printing to use port 631. For example, if you open a browser and type:```
http://localhost:631
```The CUPS admin pages pop up. Try the same with localhost:1631 and you get nothing.

Just to satisfy yourself, try:```
http://192.168.0.1:**631**/printers/EpsonStylus
```I don't think it matters what works perfectly in Windows here; we want it to work perfectly in Ubuntu. Please post back so other network printing noobs will know the outcome.

I did what you told me ( [http://192.168.0.1:631/printers/EpsonStylus](http://192.168.0.1:631/printers/EpsonStylus) ) and got nothing back from firefox, an "unable to connect" message. So, you mean that i change router settings for the printer and set 631 instead of 1631 ?

I tried to set uo the printer through the page at [http://localhost:631and](http://localhost:631and) it seems to behave the same. Seting up  print job but after a few seconds the job is "held" and nothing happens...

---

### Post by kelvin spratt on 2007-05-06
why don't you just use a usb port as i do go to printers add printer it will find R300 it has drivers then go to printer properties set your pref but if i'm missing something let me know as if there is a better way I'd really like to know

---

### Post by chili555 on 2007-05-06
I meant that when you set up the printer under System -> Administration -> Printing, use the URL as [http://192.168.0.1:631/printers/EpsonStylus](http://192.168.0.1:631/printers/EpsonStylus) rather than 1631. I've never used a printer attached to the router directly, so I am unaware of any router settings you may have to make, if any.

Another option might be to *sudo gedit /etc/cups/cupsd.conf* to change this line:```
Listen localhost:631
```So it reads:```
Listen localhost:1631
```Restart cupsd:```
 sudo /etc/init.d/cupsys restart
```Then see if the CUPS admin pages appear at [http://localhost:1631](http://localhost:1631)

I have never tried to force CUPS to a different port, so you may be a trail-blazer. If it doesn't work, you can always change it back.

---

### Post by kikapu on 2007-05-06
> **kelvin spratt said:**
> why don't you just use a usb port as i do go to printers add printer it will find R300 it has drivers then go to printer properties set your pref but if i'm missing something let me know as if there is a better way I'd really like to know

Because there are other computers that through that router have internet access and printing. I would not want to change this setup, other are printing from Windows and others are (still trying) to print from ubuntu...

---

### Post by kikapu on 2007-05-06
> **chili555 said:**
> 
Another option might be to *sudo gedit /etc/cups/cupsd.conf* to change this line:```
Listen localhost:631
```So it reads:```
Listen localhost:1631
```Restart cupsd:```
 sudo /etc/init.d/cupsys restart
```Then see if the CUPS admin pages appear at [http://localhost:1631](http://localhost:1631)


I did that and yes, the admin page is indeed displayed at [http://localhost:1631](http://localhost:1631).
I again added the printer through this page and, again, i try to print a test page, and it remains in "Printing job-printing" state...

EDIT: the funny thing is that in Printer Properties, it displays as Epson is "Connected at 192.168.0.1..."

---

### Post by kelvin spratt on 2007-05-06
i see now its just that i use more than one computer all printing on one printer and i duel boot on this one and i've always used it this way but i see your point as i use mainly ubuntu the wife uses xp on her lap top i find it easy on ubuntu through her wireless conection but i see your way as well with multi setup that could make mine impossibly  easier i wll keep an eye on this let me know how you get on

---

### Post by kikapu on 2007-05-06
> **kelvin spratt said:**
> i see now its just that i use more than one computer all printing on one printer and i duel boot on this one and i've always used it this way but i see your point as i use mainly ubuntu the wife uses xp on her lap top i find it easy on ubuntu through her wireless conection but i see your way as well with multi setup that could make mine impossibly  easier i wll keep an eye on this let me know how you get on

You said the magic words: "My wife uses xp on her laptop"...So, i have to leave the setup-up as is. I am fighting this from early afternoon and no printed pages yet :(

---

### Post by fde on 2007-07-30
Hi!
Still no solution? That would interest me...

---

### Post by kikapu on 2007-07-30
Unfortunately no.

I have gave it enough time (and GOOGLE usage...) but i just cannot print.
It is one of 2-3 annoying things that keeps me from abandon Windows completely...:(

---

### Post by fde on 2007-07-30
It seems some people found a solution, which is using CUPS version 1.2.0. I saw that [here]("http://ubuntuforums.org/showthread.php?t=141456") and [on this italian website]("http://www.linuxzine.it/forum/index.php?topic=634.msg6330") (could anyone translate the solution they found? It sounds like they downgraded CUPS from 1.2.2 to 1.2.0, but maybe this solution is a lil' bit too tricky for me - moreover, the CUPS version used in Feisty is 1.2.8 ).

---

### Post by fde on 2007-07-30
Ok. According to [this]("https://bugzilla.novell.com/show_bug.cgi?id=217215"), the IPP protocol used by USR print server is not the standard IPP protocol, but an "IPP-like" protocol designed to fit the one used in Microsoft products. In older versions of CUPS, a "bug" in the IPP protocol made it compatible with the "IPP-like" protocol of USR, but now that is corrected, therefore it is not compatible anymore...

---

### Post by kikapu on 2007-07-30
> **fde said:**
> ...therefore it is not compatible anymore...

And we cannot print anymore...:(

---

