---
title: "no wireless ubuntu 8.10 dell d600"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by hollowtd on 2009-03-27
I had some trouble on my dell d600 ubuntu ibex getting wireless to work when I first installed it. I think I had the record for most pages posted. Anyway, is there anyway to get it working again. It just stopped (after I used a mobile broadbnd device for a weekend). I'm not sure which wireless stuff I used because I installed b43-fwcutter and then the ndisgtk, ndiswrapper and the ndiswrapper utils. 

Is there a way to know which one is working my computer? Also, is there anyway to get it working again? Not sure what happened. 

Note: I can download files to a usb stick and then put them on the computer. I can't connect wirelessly or with an ethernet cable for now. 

Cheers as always

---

### Post by hollowtd on 2009-03-27
had no idea what I was doing but typed this
Step 5: Configure The Windows driver With NDISwrapper
Now install the Windows driver
In a terminal type:
sudo ndiswrapper -i bcmwl5.inf

* bcmwl5.inf is for my chipset, if you are using another driver you will have to use a different .inf file.

Then:
sudo ndiswrapper -l (that is a lowercase L)

You should see a message that says driver present, hardware detected.

Now finish installing the driver
In a terminal type:
sudo ndiswrapper -m 

and it started working. Not sure if that or if it helped that I pushed f2 + fn or not? Great got it going.

---

### Post by stalkingwolf on 2009-03-27
try using the recovery mode and fix broken packages.

Hit escape when grub starts then select recovery mode.

---

### Post by hollowtd on 2009-03-27
great thanks for that

---

### Post by stalkingwolf on 2009-04-05
did that work?

---

