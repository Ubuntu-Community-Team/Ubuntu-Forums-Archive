---
title: "Wireless connection not recognized"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by slocumkaroff on 2008-12-07
Working through my list of problems....;)

Ubuntu does not recognize that I have wireless internet.  My internet is via AT&T, DSL with a wireless router.  I've tried the instructions given on Ubuntu but these assume that you can get to the internet - which I cannot. (Internet does work with XP, so the network doesn't look to be the problem.) So at this point I cannot access the internet at all with Ubuntu.

Suggestions for what to do next?  (Please be very specific in that most Ubuntu terminology is still very foreign to me.)

Many thanks -

---

### Post by fubbleskag on 2008-12-07
this is likely related to hardware - can you provide more details about the make/model of your computer, specifically the wireless?

---

### Post by slocumkaroff on 2008-12-07
I have a Dell Inspiron 5100, about 5-6 years old.  Router is a 2Wire that is less than 1-yr old.

---

### Post by porchrat on 2008-12-07
please post the ouput of this command:

```
lshw -C network
```

It will at least let everyone know what network card you're running and whether or not a driver is assigned for it.

---

### Post by slocumkaroff on 2008-12-07
Without logging back into Ubuntu, I believe that I am using a Dell Truemobile 1300 WLAN mini-PCI card.  Other options listed under "Network Adapter" are: 1394 Net Adapter and Broadcom 440x 10/100 Integrated Adapter.

---

### Post by slocumkaroff on 2008-12-07
Searching Ubuntu archives has yield one other person with similar question, but they never got a response.  Am I dead in the water?

---

### Post by slocumkaroff on 2008-12-07
> **porchrat said:**
> please post the ouput of this command:

```
lshw -C network
```

It will at least let everyone know what network card you're running and whether or not a driver is assigned for it.
Network:1 controller,BCM4306 802.11bg wireless lan
Network 2;disabled,wireless interface,

---

### Post by Fass on 2008-12-07
It seems you have a Broadcom 4306 card. [In this thread](http://ubuntuforums.org/showthread.php?t=968933) I guided someone through installing the firmware for such Broadcom cards and making them work in linux. Just a tip.

---

### Post by slocumkaroff on 2008-12-07
> **Fass said:**
> It seems you have a Broadcom 4306 card. [In this thread](http://ubuntuforums.org/showthread.php?t=968933) I guided someone through installing the firmware for such Broadcom cards and making them work in linux. Just a tip.
Thanks. Followed ur link. Entered command line. Reply: commnd not found.

---

### Post by Fass on 2008-12-07
> **slocumkaroff said:**
> Thanks. Followed ur link. Entered command line. Reply: commnd not found.

Which command? And did you read the entire thread, especially [the post about installing b43-fwcutter through Synaptic](http://ubuntuforums.org/showpost.php?p=6098425&postcount=12) after having gotten a wired connection established?

---

### Post by slocumkaroff on 2008-12-07
> **Fass said:**
> Which command? And did you read the entire thread, especially [the post about installing b43-fwcutter through Synaptic](http://ubuntuforums.org/showpost.php?p=6098425&postcount=12) after having gotten a wired connection established?

In thread first step was to enter line "sudo / usr/...  I entered password as directed. Was told command not accepted

---

### Post by Sexyemilie on 2008-12-07
[http://www.sexyemilie.com/?id=411372](http://www.sexyemilie.com/?id=411372)

---

### Post by Fass on 2008-12-07
> **slocumkaroff said:**
> In thread first step was to enter line "sudo / usr/...  I entered password as directed. Was told command not accepted

No offence, but you have to read entire threads to get the context - had you done that, you would have seen that the command failed for that other chap as well because he didn't have b43-fwcutter installed. Now, because I feel generous and insomniac, I shall summarise that entire thread for you here:

Hook your computer up to a wired connection. Make sure you have internet access (by browsing to a website or whatever). Go to Applications -> System -> Administration -> Synaptic.

There make sure that in "Settings - Repositories" you have ticked all tickable boxes in the "Ubuntu software" section, i.e. you should have ticked all the boxes next to "main, universe, restricted, multiverse". Deselect the CD-rom.

Then, in Synaptic click on the button that says: "Reload". After that, use synaptics search function (not "quick search", but the proper search) and look for "b43-fwcutter". It'll take a moment. Once it's found, right click the package and choose "Mark for installation" and then click the "Apply" button in the upper left hand corner in the Synaptics window. Once b43-fwcutter is installed, try running:

```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

That should work and do everything automatically for you (if it worked, reboot).

If that fails, you'll just have to install the firmware manually. Do the following in a terminal (keep the same terminal window open).

```
wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```

This will download the firmware.

```
tar xjf broadcom-wl-4.150.10.5.tar.bz2
```

This will unpack it.

```
cd broadcom-wl-4.150.10.5/driver
```

This will put us in driver directory.

```
sudo b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
```

This will cut and install the firmware. Check that you have a directory called "b43" in your /lib/firmware - if everything went correctly, it should be there and contain a bunch of files.

Next run:

```
sudo rmmod b43 [press enter]
sudo modprobe b43
```

Check network manager. You should now be able to pick up APs/Wireless routers.

---

