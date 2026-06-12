---
title: "&quot;printer may not be connected&quot;??"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by klirka on 2010-07-05
hello, 

my printer (hp laserjet 1010) has been working fine for several years, through several (k)ubuntu upgrades. i am using the latest kubuntu. 3 days ago the printer stopped working, in the middle of the day. from whatever application i want to print, it always says the printer "may not be connected".

- i unplugged/replugged the printer (it prints a test page when i hit that button on the printer), both power cable and usb cable. nothing happens, no feedback or notification
- in the printer configuration window i removed and readded the printer (strangely enough, it was recognized. i was offered to add the correct hp lj 1010 printer)
- i changed the driver
- i rebootet the system several times through all this 

check box "defaul printer" is clicked.

unfortunately, no results. any help is much, much appreciated, i very much need my printer! thank you!

---

### Post by Drenriza on 2010-07-05
Have you tryed re-starting / starting your printing application? i had the same problem, where i discovered that my printing application had stopped. A quick start, and it worked again.

```
/etc/init.d/cups restart
```

---

### Post by philinux on 2010-07-05
> **klirka said:**
> hello, 

my printer (hp laserjet 1010) has been working fine for several years, through several (k)ubuntu upgrades. i am using the latest kubuntu. 3 days ago the printer stopped working, in the middle of the day. from whatever application i want to print, it always says the printer "may not be connected".

- i unplugged/replugged the printer (it prints a test page when i hit that button on the printer), both power cable and usb cable. nothing happens, no feedback or notification
- in the printer configuration window i removed and readded the printer (strangely enough, it was recognized. i was offered to add the correct hp lj 1010 printer)
- i changed the driver
- i rebootet the system several times through all this 

check box "defaul printer" is clicked.

unfortunately, no results. any help is much, much appreciated, i very much need my printer! thank you!

Could be the cable or the printer. Try a different cable or connect the printer to another machine. The printer might have died.

---

### Post by klirka on 2010-07-05
@ Drenriza: thx i tried that, rebootet, no result.
@ philinux: as i had said already: the printer works. it prints a fine test page when i hit that button directly on the printer. i tried with a 2nd usb cable, no result.

any other ideas, anyone? please help, thank you!

---

### Post by philinux on 2010-07-05
> **klirka said:**
> @ Drenriza: thx i tried that, rebootet, no result.
@ philinux: as i had said already: the printer works. it prints a fine test page when i hit that button directly on the printer. i tried with a 2nd usb cable, no result.

any other ideas, anyone? please help, thank you!

Printing a test page isn't the same as processing data through the usb cable. Try it on a different machine, even a windows one.

---

### Post by klirka on 2010-07-05
sorry i have no second machine and cannot bring one here easily. but that does not seem to be the problem, anyway. in the mean time i did a query on printer trouble here on the forum, and got at least 2 threads with similar problems (unfortunately no working solution):

[http://ubuntuforums.org/showthread.php?t=1523285](http://ubuntuforums.org/showthread.php?t=1523285)

and

[http://ubuntuforums.org/showthread.php?t=1475535](http://ubuntuforums.org/showthread.php?t=1475535)

any other ideas? thanks for your help!

---

### Post by klirka on 2010-07-05
please, could this be a cups problem?
something with a driver?
any ideas? thank you for your help!

---

### Post by philinux on 2010-07-05
Try removing the printer in sys>admin>printing then reinstalling it.

---

### Post by warfacegod on 2010-07-05
> Try removing the printer in sys>admin>printing then reinstalling it.

While you are there, right click the Printer's icon and check that it's enabled and that it's set as default.

---

### Post by klirka on 2010-07-05
yes, i have removed and reinstalled the printer. nothing. :(

in "System Settings >> Printer Configuration" all check boxes are checked: 
default printer: yes. 
enabled: yes. 
accepting: yes.
sharing TextLabel: yes.

---

### Post by klirka on 2010-07-05
still not solved, pls help, many thanks, all suggestions welcome!

---

### Post by sparty_xubunter on 2010-07-06
Same problem.  This workaround of downgrading libusb-0.1.4 in synaptic worked for me.  See entry #38:

[https://bugs.launchpad.net/hplip/+bug/595650](https://bugs.launchpad.net/hplip/+bug/595650)

(from [http://ubuntuforums.org/showthread.php?t=1516181&highlight=printer+may+-be+connected&page=2](http://ubuntuforums.org/showthread.php?t=1516181&highlight=printer+may+-be+connected&page=2) )

---

### Post by klirka on 2010-07-06
@sparty_xubunter: many thanks for your link! seems several other people have the same trouble. 

now i am using kubuntu (on a amd64, if that matters), and in kpackagekit (the kubuntu package manager) unfortunately i cannot seem to find an option to "force version" nowhere. could a good kubuntu-using soul please help me with this?

if in doubt what all this is about, please follow the link that sparty_xubunter has kindly posted and scroll down to item 38.

thank you very much!

---

### Post by klirka on 2010-07-09
hello, problem still not solved, still waiting for a friendly kubuntu user who could show me how to "force version" in kpackagekit and downgrade libusb-0.1.4 to the version that i need. many thanks if you can help me!

---

### Post by vdopey on 2010-07-11
Hi klirka,

Thank you for starting this thread, I had this exact problem today with the same printer as you.

I am also using kubuntu..

Open up konsole and paste the following:

```
sudo apt-get install libusb-0.1-4=2:0.1.12-14
```

That will do it for you and automatically downgrade the package.. 

I just tested it and it definitely works, I also removed the printer from system settings -> printer configuration 
and shut down the printer turned it back on.. It was auto detected and configured printed a test page and it worked..

Again thanks for raising this and sparty_xubunter for showing the page with fix..

---

### Post by klirka on 2010-07-11
hi again, 

i posted vdopeys line in konsole and now my printer is working again. *thanks, vdopey and sparty_xubunter, for your very kind help!*

i mark this thread as solved.

[a warning to those who read this: kpackagekit just offered to upgrade the downgraded package again. :D --- seems we now cannot automatically "select all updates" and "apply" changes any more, but must select by hand and leave out that old libusb upgrade proposal.]

---

### Post by vdopey on 2010-07-11
Hi klirka,

Yeah I hadn't thought about that, but this is obviously a bug they know about and will probably be fixed within a few days time, so you should only need to have it at this version temporarily, I hope. 

 
[https://bugs.launchpad.net/hplip/+bug/595650](https://bugs.launchpad.net/hplip/+bug/595650) -- In fact checking the bug report, its already been marked critical, it will probably be fixed very soon, again I hope.

---

