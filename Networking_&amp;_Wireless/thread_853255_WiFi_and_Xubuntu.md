---
title: "WiFi and Xubuntu?"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by racie on 2008-07-08
I'm completely new to Ubuntu, so please try to explain this to me step by step.  I have recently installed Xubuntu on a computer with WiFi, but I don't know how to configure it so the internet works.  What do I do?

---

### Post by racie on 2008-07-08
Okay, I just found out my wireless card is Atheros, which is NOT on the list of supported wireless cards for Ubuntu.  I haven't tried a direct connection with a wire.  I'm using a different computer to type this.  So if I can't download anything that could help onto Xubuntu, what in the world do I do???

---

### Post by snowpine on 2008-07-08
Hi Racie, first of all, don't panic! To get help on the forums, you'll need to find out exactly which model number wireless card you have. Then, use the search feature and it's likely you'll find someone else with excatly the same problem. I learned the hard way that even different versions of the same card from the same manufacturer can have different chip sets. :(

Do you have a disk with Windows drivers for your wireless card? If so, you can use a program called ndiswrapper to load the Windows driver. If not, I'd recommend connecting your computer via wired ethernet for the time being, if possible, so that you can download whatever software and drivers you need. 

Let us know what you've got, we'll try to help!

---

### Post by dodle on 2008-07-08
Go to your start menu > Accessories > Terminal.  Type in the following code, then enter your password.  

```
sudo apt-get install ndisgtk
```The application should then appear under: Start Menu > System > Windows Wireless Drivers, or just type "ndisgtk" (no quotes) in the terminal.

Like snowpine said, use that to install your Windows' driver and your wireless card should work in Linux.

If you can't find the .inf file your driver, try going to your laptop's manufacturer's website.  Or find the make and model of your wireless card and download the driver from it's website.

---

### Post by snowpine on 2008-07-08
Good suggestion by Dodle; ndisgtk is a graphical interface for ndiswrapper (which you run from the terminal). If you are unfamiliar with the command line interface, ndisgtk may be easier for you. They accomplish the same thing.

---

### Post by racie on 2008-07-08
Unfourtunately I do not know the exact model of my wireless card and I do not have a CD for it because it came with the computer.  I do have good news, though.  I found a chord to connect my laptop so I was able to download ndiswrapper.  Oh, and does this mean anything:
```
Ethernet Controller: Atheros Communications Inc. AR242x 802.llabg Wireless PCI Express Adapter (rev 01)
```?

*edit* oh, and I don't know how do use ndiswrapper, so um... yeah.

---

### Post by snowpine on 2008-07-08
Try 'ndisgtk' like Dodle suggested, it is an easier interface for ndiswrapper. But you are going to need that Windows driver; hopefully you can download it from the manufacturer's website. 

Try doing a search for Atheros AR242x and I'm sure you'll find lots of information. :)

---

### Post by dodle on 2008-07-08
> **dodle said:**
> Go to your start menu > Accessories > Terminal.  Type in the following code, then enter your password.  

```
sudo apt-get install ndisgtk
```The application should then appear under: Start Menu > System > Windows Wireless Drivers, or just type "ndisgtk" (no quotes) in the terminal.

Like snowpine said, use that to install your Windows' driver and your wireless card should work in Linux.

If you can't find the .inf file your driver, try going to your laptop's manufacturer's website.  Or find the make and model of your wireless card and download the driver from it's website.

:)

---

### Post by racie on 2008-07-08
I typed that, and all it said was that I was up-to-date.  Maybe I really did download ndisgtk instead of ndiswrapper.  I don't understand where my .inf file would be, though.

> **snowpine said:**
> Try 'ndisgtk' like Dodle suggested, it is an easier interface for ndiswrapper. But you are going to need that Windows driver; hopefully you can download it from the manufacturer's website. 

Try doing a search for Atheros AR242x and I'm sure you'll find lots of information. :)

Ummm... what do I need to download?  My laptop is a Compaq Presario F756NR Notebook PC.

---

### Post by racie on 2008-07-08
UPTDATE!!  I found the correct inf file for my driver after searching through my Windows system files, but when I pressed intall, it said "invalid driver."  What is wrong with my computer?  This is getting kind of frustrating.

---

### Post by dodle on 2008-07-08
Try downloading a newer driver.

What brand is your laptop?

---

### Post by racie on 2008-07-08
My laptop is a Compaq Presario Notebook.  Is that what you mean?  Oh, and what driver would you suggest?

---

### Post by dodle on 2008-07-08
What is the model number of your laptop?

(sorry, that's what I meant to ask before)

---

### Post by racie on 2008-07-08
Ummm... there's a sticker still on it and it says "Compaq Presario F756NR Notebook PC."

---

### Post by dodle on 2008-07-08
Well, I couldn't find a driver at HP's website, but I found this: [http://ubuntuforums.org/showthread.php?t=766169]("http://ubuntuforums.org/showthread.php?t=766169")
Looks like others are dealing with this same issue for that particular wireless card.

---

### Post by dodle on 2008-07-08
Also, just found the driver here:  [http://www.atheros.cz/download/drivers/ar5xxx/xp32-5.3.0.56-whql.zip]("http://www.atheros.cz/download/drivers/ar5xxx/xp32-5.3.0.56-whql.zip")
So you can try that one out too.

They sure make you run around a lot to find a driver for that thing:).

---

### Post by racie on 2008-07-08
> **dodle said:**
> Well, I couldn't find a driver at HP's website, but I found this: [http://ubuntuforums.org/showthread.php?t=766169]("http://ubuntuforums.org/showthread.php?t=766169")
Looks like others are dealing with this same issue for that particular wireless card.

I can't do whatever he did because I do not have the menu "System > [COLOR="Red"]Adminstration > Hardware drivers[/COLOR]".  I found a possible solution here: [http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233&release_id=576121](http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233&release_id=576121), but I don't really understand what to do.  Anyone have a clue?

*edit*  Thanks for the zip file, Dodle.  I'm going to see if it will work without getting to the disable menu because I don't know how to get to it.

---

### Post by dodle on 2008-07-08
> - disable both restricted drivers in System > Adminstration > Hardware driversI'm not sure why he said that.  I never had to disable any drivers for mine.  If you need to know how to do it, I think I can help.  I'll just need to log out of Windows and into Xubuntu.

---

### Post by racie on 2008-07-08
Hmm... well, the driver installed correctly, but the internet connection still doesn't work with the WiFi.  Do I need to set it up?  I don't know how anyway lol.

---

### Post by dodle on 2008-07-08
To see what formol was talking about:  In the terminal you can type:```
gksu jockey-gtk
```But I don't think that is going to help you out.  I don't see any restricted drivers to disable in mine.

To see how your wireless network is configured you can type:```
network-admin
```You'll probably have to click on the box in the lower-right that says unlock.  You'll probably see 3 different connections:  Wireless, Wired, and Point to Point connection.

---

### Post by dodle on 2008-07-08
It might be that you just need to restart your system for the driver to start working.

---

### Post by racie on 2008-07-08
> **dodle said:**
> To see what formol was talking about:  In the terminal you can type:```
gksu jockey-gtk
```But I don't think that is going to help you out.  I don't see any restricted drivers to disable in mine.

To see how your wireless network is configured you can type:```
network-admin
```You'll probably have to click on the box in the lower-right that says unlock.  You'll probably see 3 different connections:  Wireless, Wired, and Point to Point connection.


There are only two different internet connections:  wired and point to point.  Ugh.  Going to restart now and see if anything else pops up.

---

### Post by racie on 2008-07-09
[COLOR="Red"]**!!!!UPDATE AND NEW PROBLEM!!!!**[/COLOR]

I restarted the computer and it still doesn't show a wireless option after everything and I have a new problem!!  UGH!  After I restarted, a problem arose with minimizing.  I am unable to minimize any of the windows and the show desktop button doesn't work!!  Does anyone have any solutions to these?!  Xubuntu is giving me a really hard time.  I'm afraid I might give up soon. :(

---

### Post by racie on 2008-07-09
NEW NEW UPDATE!!  I installed Ubuntu and now I need to know how to install ndiswrapper because the code for ndisgtk doesn't work.  How do I work the type of file that's on this site? [http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.53.tar.gz&42437836](http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.53.tar.gz&42437836)  I don't understand how to install the file in this extension.

---

### Post by dodle on 2008-07-10
> **racie said:**
> NEW NEW UPDATE!!  I installed Ubuntu and now I need to know how to install ndiswrapper because the code for ndisgtk doesn't work.  How do I work the type of file that's on this site? [http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.53.tar.gz&42437836](http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.53.tar.gz&42437836)  I don't understand how to install the file in this extension.

That's a source file and needs to be compiled.  You should be able to get ndiswrapper working by going to a terminal and typing:```
sudo apt-get install ndisgtk
```> 
There are only two different internet connections: wired and point to point. Ugh. Going to restart now and see if anything else pops up.I've had the same problem, but usually installing ndisgtk and the windows' driver solved that for me.  As far as the windows not minimizing, I'm not sure, I'll have to look around.

---

### Post by racie on 2008-07-10
thanks.  =)

---

### Post by dodle on 2008-07-10
It looks like this person is having the same issue: [http://ubuntuforums.org/showthread.php?t=853037]("http://ubuntuforums.org/showthread.php?t=853037")Keep an eye on this thread in case they come up with an answer.

---

### Post by racie on 2008-07-10
Oh good, so my problem isn't unique.  Right now I'm reinstalling Ubuntu.  lol

---

