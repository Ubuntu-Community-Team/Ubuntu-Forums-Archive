---
title: "Adding items to the launcher bar"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by Chris62 on 2010-03-09
I have just installed Xubuntu in my EeePC 4G in place of the Xandros installation that was there previously.

I would like to add Thunderbird to the launch bar at the top of the screen but can't see how to do it. I have tried Applications/Network and right-clicking on Thunderbird like one can do in Ubuntu but doing this launches the program. How do I do put the Thunderbird icon on the launch bar?

Also, I have just updated Xubuntu and now when I switch the computer on there is a list of different "Ubuntu, Linux 2.6.31.20" going down to "Ubuntu, linux 2.6.31.14"

I had thought that there would be a file called menu.lst that I could edit to get rid of these other items and just keep the current one but can't find such a list. What is the file called that contains this information?

---

### Post by Sir Jasper on 2010-03-09
Hi,

Try right clicking on a blank area of the panel where you want the item (or between existing icons) click Add New Items then click the top item Launcher then on the Command Line type thunderderbird. Then close and then left click your new panel icon to test.

If that works and you want to change the icon, then right click on the panel icon and click Properties, then when the display box appears left click on that icon then choose another icon by left clicking on that icon picture (more are available via the drop-down list top right). In the top two lines of the display box type your preferred description (or leave either or both blank).

----------
Keep the current Kernel and the second most recent Kernel (just in case). All others can be deleted using the search box in Synaptic Package Manager.

My regards

Do come back if you have any problems.

---

### Post by Elfy on 2010-03-09
> I had thought that there would be a file called menu.lst that I could edit to get rid of these other items and just keep the current one but can't find such a list. What is the file called that contains this information?Seems that you have grub2 then - it is different to use than grub legacy. There is a file in /boot/grub - but no longer should you edit that.

More information here - 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

If you wish to remove old kernels use whatever package manager xubuntu uses, possibly synaptic (long time since I used xubuntu) and search for linux-image - mark the older ones fro complete removal.

---

### Post by Chris62 on 2010-03-10
Thanks Sir Jasper, that worked but I can't change the icon to the Thunderbird icon - it is not on the list of icons that appears when I click the panel icon and choose properties. Also it has gone to the extreme right of the panel and I would like it next to the Firefox icon on the left. Is it possible to move it and also to give it the Thunderbird icon? It isn't really a problem as it is now but I would like to change it if it can be done

---

### Post by Sir Jasper on 2010-03-10
Hi,

Right click on your Thunderbird panel icon and click move, then move it.

I will have a quick look for the Thunderbird icon and add to this post if I can find it.

My regards

Addendum:

If you have ALL ICONS in the drop down list. A very long way down, in alphabetical order, you will likely find thunderbird.

If not, if someone can paste a copy in this thread you could copy and paste it into your Pictures folder and then navigate to click on it there.

Further added re your comment below:
¨They¨ do as ¨they¨ please and live where ¨they¨ want, but I have never heard of one going to France [even for a day trip].

---

### Post by Chris62 on 2010-03-10
Many thanks forestpiskie. The version of grub that was installed was 1.97 beta and I should have mentioned that I also boot the netbook from an SD card that has Mint 8 on it and it is this, not Xubuntu, that has all the different ubuntu linux versions. I think it is a bit "off" to have included a beta version of grub in the iso file which I downloaded and used to make the bootable SD card.

Anyway, I have been able to remove all the old versions of linux-image from my desktop machine thanks to your help

By the way, I thought that piskies lived in Cornwall rather than the New Forest but perhaps they haven't any forests down there.

---

### Post by Sir Jasper on 2010-03-10
Hi Chris62,

I see you are still on line. In case you missed it, I have added to my post above

---

### Post by Chris62 on 2010-03-10
Thanks for your help Sir Jasper, I followed your instructions and have now moved the new launcher to where I want it.

Addendum: I have just seen your addendum and have now installed the icon.  'They' change their names in France. They are 'lutins' and prefer the mountains.

---

