---
title: "[SOLVED] Dual Boot Main Page"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by pstefanini on 2009-01-08
Question:  I have a dual boot system.  Along with the latest 8.10, there's an entire page of previous versions before I get to Windows XP.  How do I remove some of these older versions.  I can't seem to edit out these additional lines.  Thank you.

---

### Post by Tim Sharitt on 2009-01-08
You can take ou these extra versions by editing you /boot/grub/menu.lst file.

---

### Post by Facetious Falcon on 2009-01-08
All menu information about the Grub boot loader is stored on a file at /boot/grub/menu.lst

If you edit this file near the bottom you'll notice there's a few lines that aren't commented out (prefixed with a '#').

Each entry should be something like:

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5666f9dd-6a46-4beb-aa59-672b3c2357c1 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

I wouldn't recommend editing this file but if you need to you can delete these entries or edit them this will change the menu on startup. Deleting them all is highly unrecommended ;)

Just to make sure these 'previous versions' are more likely to be either safe modes and/or previous kernel versions in case one fails. So to be honest I'd keep them and not edit the file at all :)

---

### Post by fooman on 2009-01-08
there is an app called "startup manager" that will clean that up for you (and can do much more if you like).  it is the repos,  so you can grab it with synaptic...or in a terminal:

```
sudo apt-get install startupmanager
```after it installs,  find it in system > administration > startup manager

look in the advanced tab,  check off "limit the number of kernels in the boot menu" and choose a number (like 2) for "kernels to keep".

hope that helps.

---

### Post by cdtech on 2009-01-08
If you save older - unused kernel images like that, you'll have a big problem in the long run (with updates). The number of kernel images is proportional to your /boot partition. If you have a working kernel then keep the previous and remove unused through the "Synaptic Package Manager".

Hope this helps ya..........

---

### Post by kansasnoob on 2009-01-08
> **fooman said:**
> there is an app called "startup manager" that will clean that up for you (and can do much more if you like).  it is the repos,  so you can grab it with synaptic...or in a terminal:

```
sudo apt-get install startupmanager
```after it installs,  find it in system > administration > startup manager

look in the advanced tab,  check off "limit the number of kernels in the boot menu" and choose a number (like 2) for "kernels to keep".

hope that helps.

+1!

That's the way to do it unless you're crunched for disc space!

My way = the gui way! I'm a gui guy!

---

### Post by pstefanini on 2009-01-08
Thank you Tim Sharitt, Facetious Falcon and Fooman.  I strated to edit and got Cold Feet.  Then I read Facetious Falcon's comment which made me cancel before saving the file, then I got Fooman's suggestion which seemed the perfect solution since I can manage the process very nicely with a gem of a program.  I'm so impressed with Ubuntu and this forum! 

It worked like a charm! :D  

By way of thank you, you might enjoy the following feed mentioning open source and the future!

[http://downloads.bbc.co.uk/podcasts/radio/worldbiz/worldbiz_20090108-2030a.mp3](http://downloads.bbc.co.uk/podcasts/radio/worldbiz/worldbiz_20090108-2030a.mp3)

Best regards and wishes for the New Year

---

### Post by pstefanini on 2009-01-08
Thank you Kansanoob! ... didn't mean to leave you out, just solved before your response

---

