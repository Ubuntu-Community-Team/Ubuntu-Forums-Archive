---
title: "Can't install Adobe CS3 Master Collection"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by mclovin91 on 2009-03-11
I put the disc in and it recognizes its Adobe, but no autorun occurs nor will the setup.exe run. I have wine installed and have tried using it to run the setup.exe, but it times out i guess after about 10 or 15 seconds. I'm a new to Ubuntu and Linux in general and i'm wondering if i'm missing something or doing anything wrong.

---

### Post by teamcoltra on 2009-03-11
> **mclovin91 said:**
> I put the disc in and it recognizes its Adobe, but no autorun occurs nor will the setup.exe run. I have wine installed and have tried using it to run the setup.exe, but it times out i guess after about 10 or 15 seconds. I'm a new to Ubuntu and Linux in general and i'm wondering if i'm missing something or doing anything wrong.

You will not be able to install adobe products onto Ubuntu directly without the use of WINE([https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)), and even then it can be a bit sketchy, most people who rely on Adobe products as a job, dual boot ([http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing))

There are also a few free options instead of using Adobe products (free and open source is what its all about right?)

For Photoshop there is GIMP already preinstalled in Ubuntu
For Recording there is Audacity 
For Code editing there is well I honestly don't know that one, I am a gedit guy... code from scratch.

But yes there are typically free alternatives out there than using pay for solutions like adobe

Once again if you are convinced to use Adobe here are some links
[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)
[http://www.jonramvi.com/wine-status-report-photoshop-cs3/](http://www.jonramvi.com/wine-status-report-photoshop-cs3/)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584)

---

### Post by mclovin91 on 2009-03-11
Alright thanks

---

### Post by ivanvajar on 2009-03-12
Browse trough your Adobe CD and find setup.exe files for each program. Right-click and select Open with Wine Windows program loader. Photoshop, Dreamveawer and Flash should work fine. I don't think the other programs will work.

---

### Post by Alderas24 on 2009-03-12
I'm having the same problem! I mounted my iso file and it will only open up the autoprompt which seems to do no good. The whole thing times out at a certain point. I tried downloading a few files from winetricks that i saw on a few guides but nothing is working. Halp please.

---

### Post by Alderas24 on 2009-03-12
Okay, I had better luck by going into a terminal to monitor its activities. I did
```
wine '/media/ACS3MCD1/Adobe CS3/Setup.exe' 

```
I got a whole lot of 
```
fixme:msxml:domdoc_setProperty Unknown property L"async"

```

I have no earthly idea of what's going on. I'll keep tinkering with it while I await a true expert to sniff around this thread. Thank you preemptively for your time!

---

### Post by skymera on 2009-03-12
I've never got Photoshop to work in Ubuntu.

Let alone the whole collection.

---

### Post by mclovin91 on 2009-03-12
From what i read on the WINE website both are supported. I don't need to use it, i'm just used to using the programs it has. I already found the replacement programs i needed and i'm on my way to getting some stuff done. 
I was mainly wondering if anyone had tried to see if there isn't executable permission on it, and if adding it would help?

---

### Post by ivanvajar on 2009-03-12
I have Photoshop 7.1 installed in Ubuntu and it works like a dream. When you run setup.exe, does it complete the installation?

---

### Post by ivanvajar on 2009-03-12
I just did some 'Google': Photoshop 5, 6, 7, CS1 and CS2 work on Ubuntu. As I said, I use Photoshop 7.1 and have no problems.

---

### Post by Alderas24 on 2009-03-12
> I have Photoshop 7.1 installed in Ubuntu and it works like a dream. When you run setup.exe, does it complete the installation?

No it doesn't. It gives me a whole bunch of lines that talk about setting security values. Then when the java window pops up it tells me that there were critical errors in the installation and it was aborted. I'm racking my brain over here and still nothing >.<

> I just did some 'Google': Photoshop 5, 6, 7, CS1 and CS2 work on Ubuntu. As I said, I use Photoshop 7.1 and have no problems.

Do you know if those installers use Java? That could be the reason. Java has always been really sketchy on Ubuntu from my experiences.

---

### Post by ivanvajar on 2009-03-13
I don't know if those installers use Java. At this point, all I can tell is that my installation of PS7.1 works great on Ubuntu (8.04). One more thing. Did you run installer (setup.exe) for Photoshop, or for the whole Adobe collection?

---

### Post by mclovin91 on 2009-03-13
whole collection's setup.exe

---

### Post by ivanvajar on 2009-03-13
Browse your CD and find Photoshop's setup.exe. Photoshop should have it's own directory somewhere on the CD. You can't run autorun or setup for the whole collection. Good luck! :-)

---

### Post by humphreybc on 2009-03-13
I think the whole collection installer uses Java, but the individual setup files won't. (For CS3 at least.)

---

### Post by KayakJim on 2009-03-13
If you have a copy of windows, you could download and install [Sun's VirtualBox]("http://www.virtualbox.org/") and then install windows and then your Adobe CS3 within that. This gives you the benefit of running the applications in their native environment while still being in your Ubuntu environment.

---

### Post by Alderas24 on 2009-03-14
> **KayakJim said:**
> If you have a copy of windows, you could download and install [Sun's VirtualBox]("http://www.virtualbox.org/") and then install windows and then your Adobe CS3 within that. This gives you the benefit of running the applications in their native environment while still being in your Ubuntu environment.

Doesn't that kill your RAM though?

---

### Post by KayakJim on 2009-03-14
You specify how much RAM you want to allocate to the virtual machine so it is up to you and what your system has.

My system has 2GB RAM and I haven't encountered any problems running WinXP Pro SP3 with 640MB RAM with 32MB Video RAM but I also am not running Photoshop which I hear can be RAM intensive.

It really comes down to how much total RAM your system has. Give it a try and then you will know. Everything will probably take about 2 hours to install and get setup and try out.

---

### Post by ivanvajar on 2009-03-20
There is absolutely no need to install VirtualMachine just to run Photoshop. He has been trying to install Photoshop by running autorun for the entire collection. You just need to find setup.exe for Photoshop on your CD.

---

