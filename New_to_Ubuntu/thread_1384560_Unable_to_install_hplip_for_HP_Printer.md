---
title: "Unable to install hplip for HP Printer"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by stephcordova on 2010-01-18
Hi everyone -First time user and first time poster here.

I have a DELL Mini 9 netbook running Ubuntu 9.10. For the last two days, I have been trying to install hplip for my photosmart plus B209 printer.

From what I understand, after entering ```
dpkg -l hplip
```into the terminal, the terminal responds with this: ```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                    Version                 Description
+++-=======================-=======================-==============================================================
ii  hplip                   3.9.8-1ubuntu2          HP Linux Printing and Imaging System (HPLIP)

``` 
Thats how I know that hplip 3.9.8 is installed. 

Heres the problem. I have absolutely no idea how to install the printer now. From what I can tell, I know that I have to automatically or manually install it, but I have no idea where its been downloaded to! (Its definitely not on my desktop and I'm having trouble finding its location when I search for it. 

I've been paying attention to a lot of sites which give tips and advice about hplip, but I've been paying attention to this the most: [http://www.icelab.eu/en/blog/ubuntu-and-linux-12/how-to-install-an-hp-printer-on-ubuntu-79.htm]("http://www.icelab.eu/en/blog/ubuntu-and-linux-12/how-to-install-an-hp-printer-on-ubuntu-79.htm")

Anyway, I hope I explained my problem... And if I didnt.. Well lets just say that I have no idea how to install my printer and I am still really bad with using the terminal.

Thanks in advance for all of your help, guys!

---

### Post by thatguruguy on 2010-01-18
I never had to install anything to get my hp printer to work; it worked out of the box.  Go to System --> Administration --> Printing.  When the dialog pops up, press the "New" button.  See if your printer is listed.

---

### Post by stephcordova on 2010-01-18
> **thatguruguy said:**
> I never had to install anything to get my hp printer to work; it worked out of the box.  Go to System --> Administration --> Printing.  When the dialog pops up, press the "New" button.  See if your printer is listed.


Wow. I can't believe I didn't think about doing that. I think I have the tendency to make ubuntu "too hard".

I do have another question though... This printer has a wireless capability that I would like to use. I don't know how to configure my computer to wirelessly send print jobs to the printer.

Any ideas?

---

### Post by thatguruguy on 2010-01-18
I use an hp 6500 wireless.  I entered the wireless network information using the panel on the printer.  Once the printer saw the network, I went into the printer setup as mentioned before, and had ubuntu look for a network printer.  Once it found the printer, the printer was setup automatically.

---

### Post by stephcordova on 2010-01-18
> **thatguruguy said:**
> I use an hp 6500 wireless.  I entered the wireless network information using the panel on the printer.  Once the printer saw the network, I went into the printer setup as mentioned before, and had ubuntu look for a network printer.  Once it found the printer, the printer was setup automatically.

Thank you! 

You were right, I went to the printer screen, looked at my wireless settings and found my host name. Everything was smooth. 

Thanks so much for your help...

---

### Post by thatguruguy on 2010-01-18
No worries.

---

