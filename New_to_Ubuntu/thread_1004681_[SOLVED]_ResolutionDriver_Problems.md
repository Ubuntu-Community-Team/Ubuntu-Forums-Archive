---
title: "[SOLVED] Resolution/Driver Problems"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Kyaizen on 2008-12-07
...

---

### Post by Thilo Kuhlman on 2008-12-07
Same here. My resolution is small and I cannot manage to accomplish much. My Hardy Heron also says "No proprietary drivers found". To find your specs though, go to terminal and type in "lspci". I cannot find, however, where to install video drivers, and it is making me want to shoot a unicorn.

---

### Post by residualbit on 2008-12-07
First, what type of video card do you have?

Also, make sure you have the proprietary and restricted sources turned on.

System>Admin>Software Sources

Enable the "Proprietary Drivers for Devices (restricted)
and
"Software retstricted by copyright or legal issues"

Then run the update manager again.

---

### Post by dracayr on 2008-12-07
System&#8594;preferences&#8594;Screen resolution

or, for certain cards you might have to install proprietary drivers. which graphics cards do you have

sudo lshw outputs your system specs

dracayr

---

### Post by mapes12 on 2008-12-07
Machine spec. Terminal ```
sudo lshw
```
Screen res. Terminal ```
gksudo displayconfig-gtk
```
when the GUI pops up select your hardware and required screen res.
> "No proprietary drivers found" This doesn't mean your card is not supported. It just means that some of the drivers that are not "free" are either not required or not installed. To determine further help please post the output to my first command above.

Mark

EDIT - after changing your screen res you end up with a HUGE login screen then post back and I'll post details of how to correct it.

---

### Post by Kyaizen on 2008-12-07
...

---

### Post by mapes12 on 2008-12-07
OK You need to download the packages. Go to the following 2 links. At the bottom of each page is a link to allow the package to be downloaded. Make sure that, for guidance-backends you select the correct architecture for your computer. For displayconfig-gtk there is only one possible download for all architectures. You will have to select a mirror near to you before each download will begin.

[http://packages.ubuntu.com/hardy/admin/displayconfig-gtk](http://packages.ubuntu.com/hardy/admin/displayconfig-gtk)

[http://packages.ubuntu.com/hardy/guidance-backends](http://packages.ubuntu.com/hardy/guidance-backends)

Once downloaded, click on the guidance-backends first, and you should be presented with the option 'Open with GDebi' or something similar. This program installs the package on your system. It will ask for your password.

Do the same for the displayconfig-gtk package.

Once they are both successfully installed (< 30 seconds ) open a terminal and type:

```
gksudo displayconfig-gtk
```

---

### Post by Kyaizen on 2008-12-07
...

---

### Post by mapes12 on 2008-12-07
> What model and screen do I choose?  If they are not available from the drop down list then this fix may not be able to help your configuration.

Are you running version 8.10? (many screen res issues reported lately). Therefore, unless you have a compelling reason to run 8.10 then 8.04 should work Ok until the screen res issues in 8.10 are sorted out by the devs.

---

### Post by Kyaizen on 2008-12-07
...

---

### Post by Kyaizen on 2008-12-09
...

---

### Post by Kyaizen on 2008-12-09
...

---

### Post by Tatty on 2008-12-09
SIS GFX cards produce lots of problems.  At least they always have for me.

The displayconfig-gtk application fixed an SIS resolution issue i was having in Hardy not long ago, but due to the new Xorg in Intrepid the displayconfig-gtk application no longer works and is not in the repos.

You may want to try manually editing your xorg.conf file to set the desired screen resolutions. [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by Kyaizen on 2008-12-09
...

---

### Post by Tatty on 2008-12-09
> **Kyaizen said:**
> I'm not good at coding...

Its not coding,  Its just telling xorg what screen resolutions you want, as long as you back up the file first (that tutorial shows you how) then you cant break anything.

Its the "modeline" bit which may solve your problem. Give it a go, you will learn a lot about how ubuntu works (though bear in mind that tutorial is 3 years old now).

---

### Post by Kyaizen on 2008-12-09
...

---

### Post by Tatty on 2008-12-09
> **Kyaizen said:**
> So you think it will work on the newest version of ubuntu?

I am not sure to be honest.  Im not up to date with how the latest xorg functions, I know it has undergone a lot of changes in the last year or so.

But i dont see why it wouldnt work, linux users would be distraught if there wasnt a text-based way of doing something ;)

**EDIT:** i just found this post on a similar issue.  [http://ubuntuforums.org/showthread.php?t=978303](http://ubuntuforums.org/showthread.php?t=978303)  So it sounds like you can still edit xorg.conf like before.

---

### Post by Kyaizen on 2008-12-09
...

---

### Post by Tatty on 2008-12-09
> **Kyaizen said:**
> Haha thanks for the help, but I've read of the tutorial and I still don't think I can do it..

Ok, its been a long time since I last manually edited an xorg.conf file but I will try to talk you through it.  What resolution should you be getting?

Also, could you post the output of ```
cat /etc/X11/xorg.conf
```

---

### Post by Kyaizen on 2008-12-09
...

---

### Post by Kyaizen on 2008-12-09
....

---

### Post by Kyaizen on 2008-12-09
...

---

### Post by Kyaizen on 2008-12-10
...

---

### Post by Kyaizen on 2008-12-13
...

---

### Post by Kyaizen on 2008-12-13
...

---

