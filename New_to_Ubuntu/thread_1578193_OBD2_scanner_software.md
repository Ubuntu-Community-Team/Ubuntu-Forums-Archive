---
title: "OBD2 scanner software"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2010-09-20
Hello everybody.
I have an Acer Aspire 5000, running Ubuntu 10.04.
Over the last few days, I've been seriously considering buying one of those cheapo Ebay OBD2 scanner interfaces. However, I keep searching, but none of them seem to work on anything but Windows.
Now, running Windows on my PC is not an option. First, because of hardware limitations, and second, because I don't like substandard software. ;)

So, my questions are:

Is there any software out there that would let me use an ELM 327 based interface with Ubuntu?

If there isn't any, can I run programs like ScanXL professional on Ubuntu, with Wine?

If that's possible, how should I do it? Do I just install Wine, and then the software? 
When it comes to computers and programming, I have the I.Q of a brick, so any help will be greatly appreciated.

Thanks in advance. :D

---

### Post by jtarin on 2010-09-20
> Is there any software out there that would let me use an ELM 327 based interface with Ubuntu?It's seems to be written in QT which is native KDE...so I would guess Kubuntu. Contact the author at his [website ]("http://automon.donaloconnor.net/")he seems to be working with Debian.

---

### Post by Inodoro Pereyra on 2010-09-20
Thank you Jtarin.
That project looks good, but he's still working on it. 
I started working in mechanics, and right now I'm in desperate need of a scanner ASAP, as I'm working on a car that a previous "mechanic" (or, more appropriately, "butcher") messed up completely, and it will just not start, no matter what I do to it.

Will a normal Windows compatible software run properly with Wine?
Is there a tutorial of some sort, where I can learn how to install Wine, and make everything work?

---

### Post by jtarin on 2010-09-20
You can try [here]("http://www.winehq.org/")

---

### Post by Inodoro Pereyra on 2010-09-20
Thanks again. :)

I finally figured how to use Wine, and installed Engine Analyzer Pro 3.9., and tried to install  EScan 1.19.
With the EAP, when I try to run it, I get a message "Run time error '339'  Component 'THREED32.OCX' or one of its dependencies not correctly registered: a file is missing or invalid"
With EScan, when I try to open it with Wine, it starts installing, and then, I get: "There is no Windows program configured to open this type of file"

Any comments?:(

---

### Post by jtarin on 2010-09-20
Wine issues would be better answered in the Wine Forum. It sounds as if your missing some .dll files. It's possible your application will not run at all under Wine but I recommend you visit the Forum for advice.

---

### Post by Inodoro Pereyra on 2010-09-20
Will do. Thanks again.

---

### Post by jtarin on 2010-09-20
Sorry I couldn't help more. I have my own problems from time to time with Wine and that's where I go.:)

---

### Post by Inodoro Pereyra on 2010-09-20
You helped a lot. Thank you.
We all know not everything works on Wine. I went to the wine forum, and didn't find anything. I'll just wait for the interface to arrive, and see if I have more luck with the included software. Otherwise, I'm gonna have to go back to XP... :(

---

### Post by jtarin on 2010-09-20
You could try running XP in a virtual box? :)

---

### Post by Inodoro Pereyra on 2010-09-20
Hmmm...English, please?:confused: :lol:

---

### Post by jtarin on 2010-09-20
[All the English you need.]("https://help.ubuntu.com/community/VirtualBox")

---

### Post by Inodoro Pereyra on 2010-09-20
Will check it out. Thanks again. You da man...:biggrin:

---

### Post by jtarin on 2010-09-20
Hope you can get it working.

---

### Post by CFury on 2010-09-20
If you get something working please let me know.  Scan Tool software is the only thing that would have me use an MS product again... apart from my XBox 360 that is.  :P

---

### Post by jtarin on 2010-09-20
> **CFury said:**
> If you get something working please let me know.  Scan Tool software is the only thing that would have me use an MS product again... apart from my XBox 360 that is.  :PIf it runs in Windows it will almost certainly run in Windows virtual box.

---

### Post by CFury on 2010-09-20
> **jtarin said:**
> If it runs in Windows it will almost certainly run in Windows virtual box.


I'll give it a go.  Cheers.

---

### Post by Inodoro Pereyra on 2010-09-21
Bad news: there are 2 virtual boxes for Ubuntu. One is open source, and the other one is...not.
The open source one does not support USB, so if we want to use the scanner, we have to pay. Being that I already have XP, looks like I'm going back to wubi...:(

---

