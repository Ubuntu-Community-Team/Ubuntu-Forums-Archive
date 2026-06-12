---
title: "Getting an .inf file"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by toasty_ghosty on 2008-04-02
Hello

I am trying to get my wireless card to work. I am using a WPC11 v3 card. I was trying to use the Linux drivers available, but I cannot get them to work so I thought I would just use ndiswrapper. The issue is, is that all the install packages for Windows are .exe and I cannot get the .inf file I need. How do you extract it from the .exe? Or where do you get just the .inf file? Any help would be very nice.

Thanks.

---

### Post by chili555 on 2008-04-02
Generally, you can use *cabextract*:```
sudo apt-get install cabextract
```Then do:```
cd /folder/containing/exe
cabextract sample.exe
```Two other tools that help with those stubborn .exe's are *unshield* and *unrar.* Also, sometimes, when you cabextract an .exe, you find other files that need to be cabextracted, unshielded or unrared, too. Try them all; they're free.

---

### Post by toasty_ghosty on 2008-04-02
Thank you. But I still am getting this issue...

t@Linux:~/Desktop$ cabextract wpc11v3.0*
wpc11v3.0_wpa_dr.exe: no valid cabinets found

All done, errors in processing 1 file(s)

---

### Post by koenn on 2008-04-02
If you run that exe on a windows machine, you'll probably find the .inf file there. There's usually a vendor or device name in it (you're gonna wish Windows had something like grep), and sometimes you can recognise them by filename.

You can also try 'strings', a program that finds text in binary files. It might get you the content of the inf file, that you can redirect to a text file so you re-create the .inf file rather than extracting it.

---

### Post by toasty_ghosty on 2008-04-02
Thank you. Good idea about finding a Windows machine. Now to just find one...

---

### Post by koenn on 2008-04-02
I had a look at it - it's probably a self-extracting zip archive, in which case you can unpack it with
```
 unzip wpc11v3.0_driver060503_wpa.exe -d /path/to/folder 
```, 
the inf files will be in a subdirectory of "/path/to/folder"

---

### Post by toasty_ghosty on 2008-04-02
Thank you. I now have the .inf files I need.

---

### Post by koenn on 2008-04-02
good luck with the ndiswrapper

---

### Post by chili555 on 2008-04-02
I believe *unzip* does it. Sorry I forgot to mention that handy tool.

---

### Post by iamclueless on 2008-04-09
> **toasty_ghosty said:**
> Thank you. I now have the .inf files I need.

Have you managed to get your WPC11 ver3 working for WPA secured routers?  Do let me know... i imaginei will need to do exactly what you did

---

### Post by chili555 on 2008-04-09
> I was trying to use the Linux drivers available, but I cannot get them to workIs this a Prism II chipset? They should be quite easy to get going. What didn't work for you?

---

### Post by iamclueless on 2008-04-18
> **chili555 said:**
> Is this a Prism II chipset? They should be quite easy to get going. What didn't work for you?

yep the card works when accessing unsecured networks.  no go with WEP at all.  no chance with WPA.. it needs to be flashed before it can use WPA, not about to do that.  

currently using it the card on a Mepis install and it works for the most part (only WEP but not the passphrase, and only one of the codes, and the network cannot be hidden. 

so at this point i know what to do.  a hardware flash of the firmware is required.  and possibly ndiswrapper afterwards

posting this now as something new people can refer to if they have the same issues.

---

### Post by chili555 on 2008-04-18
I never saw a Prism II card I couldn't get to work with WEP. Never. If you want to try again, post back.

[http://ubuntuforums.org/showthread.php?t=172810&highlight=WEP&page=2](http://ubuntuforums.org/showthread.php?t=172810&highlight=WEP&page=2)

---

