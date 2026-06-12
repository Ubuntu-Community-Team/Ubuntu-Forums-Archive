---
title: "Lexmark Printer Woes??"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by mapes12 on 2009-08-27
Hi

I managed to convert my Dad from the Darkside to Ubu. He's running 8.04 but I forgot about his printer. It's a P4330 or P4350 (his email typing isn't very good). I've Googled for ages and been to Lexmark website where they do list .deb Linux drivers but all the links are dead :(

The Google results also reveal other Ubu posts about c**p support from Lexmark for their printers and Linux.

So, I thought I would just post this to see if anyone has had any success getting a Lexmark printer to work.

Any pointers greatly appreciated.

TIA.

Mark

---

### Post by LowSky on 2009-08-27
As per the link, that thing is a paper-weight, sorry, your out of luck, lexmark make crap products and offer almost no Linux support, which is dumb as many businesses rely on Linux for print servers.

[http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-p4350](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-p4350)

---

### Post by mapes12 on 2009-08-27
> **LowSky said:**
> As per the link, that thing is a paper-weight, sorry, your out of luck, lexmark make crap products and offer almost no Linux support, which is dumb as many businesses rely on Linux for print servers.

[http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-p4350](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-p4350)
Thanks LowSky

I found that link as well when Googling. I guess my Dad has 2 options:

1. Go back to the Darkside

2. Get a Linux supported printer. I understand HP are very good. Thoughts?

BTW- He doesn't do much printing. Just the odd stuff so he can read it more clearly.

---

### Post by LowSky on 2009-08-27
the same website I gave before is great to find out if a printer is supported. I have a HP laserjet 1018 and it works pretty well.

From consensus around here HP printers are the way to go.

---

### Post by mapes12 on 2009-08-27
> **LowSky said:**
> the same website I gave before is great to find out if a printer is supported. I have a HP laserjet 1018 and it works pretty well.

From consensus around here HP printers are the way to go.My thoughts as well. I have 2 HP printers here and both work without any tweaking. One of them also has a built in scanner but after installing ```
sudo apt-get install hpoj

```from this link [http://ubuntuforums.org/showthread.php?t=6571](http://ubuntuforums.org/showthread.php?t=6571) Xsane worked immediately.

---

### Post by bear24rw on 2009-08-27
i tried to get a lexmark to work in linux once, not even close to successful, my HP however works perfectly scanning and all

---

### Post by mapes12 on 2009-08-27
> **bear24rw said:**
> i tried to get a lexmark to work in linux once, not even close to successful, my HP however works perfectly scanning and allHello bear24rw

I agree. HP appears to be the way to go.

Thanks for your post.

Mark

---

### Post by WitchCraft on 2009-08-27
Try installing the latest kernel, as drivers are in the kernel.
Then restart.



Then, after you restarted, all you have to do is go to system > Adminitration > priting > Select local printer > 

Your lexmark 4XXX series should be listed. (make sure your USB cable is coneccted)

Select the correct model and press apply.

Now, turn off the printer and disconnect the power cable and reconnect it. 
You are ready to print.


You are ready to print.

[http://www.openprinting.org/printer_list.cgi?make=Lexmark](http://www.openprinting.org/printer_list.cgi?make=Lexmark)

PS: Try to sell the lexmark printer and buy a HP.

---

### Post by mapes12 on 2009-08-27
> **WitchCraft said:**
> Try installing the latest kernel, as drivers are in the kernel.
Then restart.



Then, after you restarted, all you have to do is go to system > Adminitration > priting > Select local printer > 

Your lexmark 4XXX series should be listed. (make sure your USB cable is coneccted)

Select the correct model and press apply.

Now, turn off the printer and disconnect the power cable and reconnect it. 
You are ready to print.

PS: Try to sell the lexmark printer and buy a HP.That's a great suggestion. Some questions:

1. How do I know what kernel version is currently running?

2. How do I find then install the latest kernel version?

TIA.

Mark

---

### Post by WitchCraft on 2009-08-27
> **mapes12 said:**
> That's a great suggestion. Some questions:

1. How do I know what kernel version is currently running?

uname -a


> **mapes12 said:**
> 
2. How do I find then install the latest kernel version?

TIA.

Mark
finger @kernel.org

This is a link to the latest kernel source:
[http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.31-rc7.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.31-rc7.tar.bz2)

Here is how to do it:
 [http://ubuntuforums.org/showthread.php?p=7295561](http://ubuntuforums.org/showthread.php?p=7295561)

---

