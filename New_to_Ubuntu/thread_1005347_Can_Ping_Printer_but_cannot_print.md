---
title: "Can Ping Printer but cannot print"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by sun1111 on 2008-12-08
Hi I am a new beginner to Ubuntu.

I have just install Ubuntu Desktop 8.10.
Everything works fine, open office, firefox is OK. No problem accessing the internet
The only problem is printing.

I have a Canon ImageClass 2220 (same as GP160)connected to the LAN. All PC & Notebook (Win2K, XP, Vista) can print thru this printer except Ubuntu Desktop.
I used GP335 driver as it is recommended for this printer. Host is set to 10.10.2.99:9100
From Ubuntu Desktop I can ping the printer (10.10.2.99) but can't print.
Please advice on possible remedy (or if I miss out something). All help is much appreciated.

---

### Post by gettinoriginal on 2008-12-08
Is there anything in this post to help ??  Also, do you have cups installed ??

[http://sudan.ubuntuforums.com/showthread.php?t=797508](http://sudan.ubuntuforums.com/showthread.php?t=797508)

---

### Post by sun1111 on 2008-12-09
Hi gettinoriginal
I have checked, CUPS is running fine.
Any suggestion?

---

### Post by philinux on 2008-12-09
Have a check through this.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by rlogan on 2008-12-09
I did have a similar problem until someone suggested that I try to setup cups through the web interface (for lack of a better terminology) and it all works fine here, but you have a different printer to me.

Try to login into cups but going to [http://127.0.0.1:631/](http://127.0.0.1:631/) and then try add printer and manage printers.

Hope that helps ???

Cheers

Richard

---

### Post by MrWES on 2008-12-09
Yes, defintely access CUPS via the web GUI. I also found restoring the default config file and then setting the printer parameters also works. Seems with all the configuring the conf file can get corrupted. Once I did that I was able to print wirelessly from my laptop to my wired printer on my desktop.

---

### Post by sun1111 on 2008-12-09
Thanks rlogan.

I have tried the CUPS web interface, it is quite easy to configure.
When I try the test print, alway have the below message
Imageclass 2220 "No %%Pages : Comment in header!"

I am not sure whether the driver is correct.
My printer is Canon Imageclass 2220 (AC110 V). Exact driver is not available.
GP160 (AC220V)is an equivalent model.
GP335 is the recommended model to use as indicated in
[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-GP_160](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-GP_160)
Any idea?
Thanks again for helping out

---

### Post by philinux on 2008-12-09
I would connect the printer to your ubuntu box just to prove it prints ok.

---

### Post by rlogan on 2008-12-10
Yeah prob good suggestion to hook it up directly and give it a o.

One thing that gave me grief was that my config file was modified and once restored to the default it was the start of all that is good.

I did have a Canon printer and it was a really nice printer but gave me all sorts of grief. It died and then bought a HP and it works beautifully straight out of the box when it was linked up on Hardy.

Wish I could help you more but I did check out your link but nothing definite there.

Cheers

Richard

---

