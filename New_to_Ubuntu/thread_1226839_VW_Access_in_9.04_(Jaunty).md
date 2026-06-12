---
title: "VW Access in 9.04 (Jaunty?)"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by lalimalina on 2009-07-30
I have Verizon Wireless Mobile Broadband, and it only works with VZ Access Manager installed.  The VZ Access Manager software is already in the USB modem I use, which is very convenient and works wonderfully... with Windows.  I have Ubuntu 9.04, which I think is the Jaunty Jackalope.  How can I install the VZ Access Manager in Ubuntu?

Or, alternatively, are there any other suggestions on how I can get my internet to work without the VZ Access Manager?  Any programs designed for Ubuntu or Linux that I can use instead?

I used Ubuntu before I got this type of internet service, and had to re-install Windows on my computer as I needed to be able to access the internet immediately for school...  This is the only thing keeping me from going back to using Linux 100% of the time...

Thanks!

---

### Post by Mark Phelps on 2009-07-30
You only really have two options, and really, only one.

Your first option would be to install Wine and then use that to install VZ Access Manager.  But I checked the CodeWeavers application compatibility DB and that program wasn't listed.  So, it's most likely that it will either not install, or if it does install, it will not work.

Which leads to the other option -- virtualization.  You can use Virtualbox to install MS Windows inside Ubuntu.  But then, you have to install an entire OS just to get internet access, and that's a lot of work for very little reward.

---

### Post by LowSky on 2009-07-30
what kind of card did verizon give you, do you know the model?

if not open a terminal and paste this command, it will give us the info on the card

```
lsusb
```

---

### Post by lalimalina on 2009-07-30
Those two options do sound like more trouble than it's worth...  I hope I can find some other way to make it work!

It's a USB760 Modem...  Thanks!

---

### Post by postalphil on 2009-10-02
Here is what you are looking for [http://ubuntuforums.org/showthread.php?t=1002262]("http://ubuntuforums.org/showthread.php?t=1002262") It got my usb760 with verizon working.

---

### Post by blooddragon34 on 2010-01-05
is it possible dl wine software to a cd/r,from my windows pc.then install in my ubuntu 9.04 pc.

---

