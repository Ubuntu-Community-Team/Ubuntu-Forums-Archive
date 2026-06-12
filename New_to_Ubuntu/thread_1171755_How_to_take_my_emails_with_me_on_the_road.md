---
title: "How to take my emails with me on the road?"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-05-27
My brain, as usual, is fuddled. A little more so right now because one of my daughters is needing me to accompany her abroad for unexpected and risky surgery. I can't afford to stop taking care of business during this period of absence. I don't have a laptop and so can't sync everything to it.

I use X-marks for my bookmarks which will take care of that.

What is the best way for me to take my Thunderbird email files with me and be able to use them wherever I might end up? not necessarily on a Ubuntu powered machine.

---

### Post by DGortze380 on 2009-05-27
> **tahitiwibble said:**
> My brain, as usual, is fuddled. A little more so right now because one of my daughters is needing me to accompany her abroad for unexpected and risky surgery. I can't afford to stop taking care of business during this period of absence. I don't have a laptop and so can't sync everything to it.

I use X-marks for my bookmarks which will take care of that.

What is the best way for me to take my Thunderbird email files with me and be able to use them wherever I might end up? not necessarily on a Ubuntu powered machine.

[http://www.mail2web.com/](http://www.mail2web.com/)

---

### Post by presence1960 on 2009-05-27
copy your profile folder which is in /home/.mozilla-thunderbird to a flash drive or CD. when you get to a machine install Thunderbird. If it is a windows machine copy the Mail subfolder to the existing thunderbird profile. This folder contains all your mail. If it is an Ubuntu machine copy your entire profile back to .mozilla-thunderbird folder in /home

---

### Post by tahitiwibble on 2009-05-27
Thank you very much for that **DGortze380**, a remarkable time-saver and will definitely be useful, I had no idea something like that existed. Nevertheless, I still need to have access to my past mails.

---

### Post by biglog on 2009-05-27
[http://portableapps.com/apps/internet/thunderbird_portable](http://portableapps.com/apps/internet/thunderbird_portable)
Use on a flash drive, copy your folders across

---

### Post by tahitiwibble on 2009-05-27
> **presence1960 said:**
> copy your profile folder which is in /home/.mozilla-thunderbird to a flash drive or CD. when you get to a machine install Thunderbird. If it is a windows machine copy the Mail subfolder to the existing thunderbird profile. This folder contains all your mail. If it is an Ubuntu machine copy your entire profile back to .mozilla-thunderbird folder in /home

Thank you **presence1960**, so my /home/dad/.mozilla-thunderbird/jg40ottu.default/Mail is completely platform independent. i.e. it will work on all OS's providing I can find the identically named folder after having installed Thunderbird?

---

### Post by fballem on 2009-05-27
> **tahitiwibble said:**
> Thank you **presence1960**, so my /home/dad/.mozilla-thunderbird/jg40ottu.default/Mail is completely platform independent. i.e. it will work on all OS's providing I can find the identically named folder after having installed Thunderbird?

The short answer is 'yes'.

On a Windows machine, you may have to locate the Thunderbird data once you have installed Thunderbird. It is found in the Documents and Settings\username\AppData folder (Windows XP) or Users\username\AppData folder (Windows Vista, Windows 7). These are normally hidden folders, so you may need to change the View options for the folder to Show Hidden Files.

Remember on a Linux machine that the .mozilla folder is a hidden folder. When the ~/home folder is displayed, say in Nautilus, ctrl-h will unhide these hidden folders.

Those of us who have converted to Linux from Microsoft Outlook are well aware of the ease of transporting Thunderbird files. To do the conversion, we install Thunderbird on Windows, import the outlook mail, save the Thunderbird files to an external drive. When we install Linux and Thunderbird, we can then copy the external Thunderbird files and we're good to go.

Hope this helps, and hope that you're daughter is okay! Prayers are with you both.

---

### Post by presence1960 on 2009-05-27
> **tahitiwibble said:**
> Thank you **presence1960**, so my /home/dad/.mozilla-thunderbird/jg40ottu.default/Mail is completely platform independent. i.e. it will work on all OS's providing I can find the identically named folder after having installed Thunderbird?

yes i took mine from windows when I came to ubuntu- worked perfectly!

---

### Post by tahitiwibble on 2009-05-27
Thank you all, I'll probably do it **everything** suggested just in case, problem solved  ........... **fballem** thank you very much!

---

### Post by tahitiwibble on 2009-05-27
> **biglog said:**
> [http://portableapps.com/apps/internet/thunderbird_portable](http://portableapps.com/apps/internet/thunderbird_portable)
Use on a flash drive, copy your folders across

Amazing! ..... thank you.

---

### Post by whitethorn on 2009-05-27
I would just suggest a small addition to the thunderbird idea.  If you plan on putting your thunderbird profile on a usb stick, create an encrypted file with Truecrypt and put your profile in there.  You can mount it in linux and windows, and should you lose your usb stick other people won't be able to read your emails or access your data.

---

### Post by NHArticleTen on 2009-05-27
second on the [http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by tahitiwibble on 2010-05-18
I just recently ended up using this "KISSing" method :) [http://kb.mozillazine.org/Synchronizing_mail_on_two_computers](http://kb.mozillazine.org/Synchronizing_mail_on_two_computers)

---

