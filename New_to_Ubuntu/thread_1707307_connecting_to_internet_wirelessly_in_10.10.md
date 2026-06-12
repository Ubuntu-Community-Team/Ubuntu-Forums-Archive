---
title: "connecting to internet wirelessly in 10.10"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by melanie.todd01@gmail.com on 2011-03-15
I really need help.  It has taken me half an hour to figure out how to even ask a question.  I really don't have a clue but have somehow managed to instal 10.10 on a mini dell laptop.  Can connect to internet via ethernet cable but can't connect wirelessly.  Have followed all the threads, but I can't even figure out where "system" is so I can look for "administration" and then "drivers".  My screen only shows the ubuntu icon in top left corner.  Nothing else.  I don't think it has loaded properly.  Please advise if ubuntu is too difficult for someone of such basic abilities and I will go and buy windows os tomorrow.  Many thanks in anticipation.

---

### Post by or3x on 2011-03-15
You can add a new menu:
Rightclick on the top panel -> Add to panel -> Menu Bar
Then, if it shows up, System -> Administration -> Additional Drivers to see if there are any available drivers.

---

### Post by melanie.todd01@gmail.com on 2011-03-15
> **or3x said:**
> You can add a new menu:
Rightclick on the top panel -> Add to panel -> Menu Bar
Then, if it shows up, System -> Administration -> Additional Drivers to see if there are any available drivers.

I'm sorry, but I'm not sure how to reply properly, so i hope this works.  
Thanks for your prompt reply.  Nothing happens when I right click on the top panel.  One of the icons on the top right hand side says "one or more disks are failing".  Not sure if that helps.  I should add that when I bought the laptop second hand just a couple of weeks ago it had ubuntu 8.04 on it and it was fine, but I was having trouble opening powerpoint presentations and also couldn't use my iphone as a tethering device.  Any thoughts?

---

### Post by coffeecat on 2011-03-15
> **melanie.todd01@gmail.com said:**
> I don't think it has loaded properly.

If it's only showing an Ubuntu logo top left then something is not right. Which version of 10.10 did you try to install? If it was the desktop version, it should look like the screenshots in this link:

[http://www.unixmen.com/linux-distributions/4-ubuntu/1150-ubuntu-1010-maverick-meerkat-screenshots-and-video-tour](http://www.unixmen.com/linux-distributions/4-ubuntu/1150-ubuntu-1010-maverick-meerkat-screenshots-and-video-tour)

If the netbook version, as in this link:

[http://www.ubuntu.com/netbook](http://www.ubuntu.com/netbook)

How did you install? With a live USB pendrive? You can run that without installing to see how well it works on your hardware. Did you try that before installing?

---

### Post by or3x on 2011-03-15
It seems like there's a hardware problem  with the harddrive. I'm not sure what you should do, sorry. I think you should do a backup of your files though, if it should brake or something.

---

### Post by melanie.todd01@gmail.com on 2011-03-15
I downloaded the netbook version.  It looks exactly like the 2nd link you provided which makes me hopeful (the Unity Interface). The Mobile Geek was here earlier and started off the download onto the USB stick.  I didn't do a trial because I've only had the netbook a couple of weeks and things weren't working for me with 8.04 and I didn't understand how to trial, so I figured just go for it.  Anyway, could you possibly tell me how to find "system, admin etc" in the Unity Interface?  Then maybe I can connect wirelessly and then deal with my next problem which is I can't figure out how to open any files off my external harddrive which I've tried connecting!!!

---

### Post by melanie.todd01@gmail.com on 2011-03-15
> **or3x said:**
> It seems like there's a hardware problem  with the harddrive. I'm not sure what you should do, sorry. I think you should do a backup of your files though, if it should brake or something.
Thank you for your help.  I realise ubuntu is way beyond my capabilities and will just buy windows os and microsoft office because I have no idea what I'm doing.  I hate having to subscribe to MS, but for amateurs like me, there appears to be no option.  Thanks again.

---

### Post by coffeecat on 2011-03-15
You don't need the admin menu. To connect wirelessly, you click on the network manager icon which is in the panel towards the top right. It's usually to the left of the sound icon. Try clicking on that. If your system is seeing your wireless network then it's simply a matter of clicking on it and entering your wireless WPA/WEP passkey when prompted. 

However, Dell often uses Broadcom wireless chips which can be a pain for licensing reasons. If network manager is not seeing your network, then have a look at this link. Sorry it's so daunting:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

The icon in the dock with the setsquare and scissors should take you to all applications.

I have to say that I agree with or3X that the "one or more disks are failing" message you got is ominous.

By the way, you've used your email address as your username. This is not really a good idea and you may want to change this. If so, you can ask here:

[http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

---

