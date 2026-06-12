---
title: "Please Help- Lost wireless network"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by Locutus_of_Borg on 2007-09-29
Hello, I am on kubuntu 7.04 kernel 2.6.20-15-generic.

Last night I got tired of Kmix messing with my keyboard volume controls, so I opened Add/Remove un-checked the Kmix box, and clicked apply changes.  It began to delete a lot more than Kmix, so I closed the window.  I'm now missing GNOME among other things, but more importantly, I no longer seem to have a wireless device.

iwconfig says:
lo -------  no wireless extensions

eth0 ------ no wireless extensions

eth1 ------ basically says everything is off or missing


Is there any way to restore this apart from re-installing and erasing everything I've added since my initial install?

I have made no backups. :\ 


:confused: :(

---

### Post by MobiusNZ on 2007-09-29
Plug into a wired network and check out /var/log/dpkg.log.

That should give you an idea on what to re-install. Look for lines that don't have "status" as the first word after the date. Those pretty much correspond to apt commands that you can do the reverse. Most packages leave their configuration when you uninstall them, unless you explicitly tell it to remove config.

---

### Post by Locutus_of_Borg on 2007-09-29
i dont know when i will have the chance to get to a wired network, im sitting at a coffee shop since we only have dial-up at home, i was hoping there was someway to add the network manager device from my install disk maybe?

---

### Post by MobiusNZ on 2007-09-29
Actually, you'll probably find that the sources are still cached on your disk, so you may not even need the disk.

---

### Post by Locutus_of_Borg on 2007-09-29
i thought they might, but i don't know how i would go about re-installing them.  I've only been using linux for about a month or two. It's intel proset wireless, if that helps in anything you or anyone else can suggest.

thank you very much

---

### Post by MobiusNZ on 2007-09-29
Open up your terminal and type ```
cat /var/log/dpkg.log | grep remove
```
That will show you all the stuff you've removed from your system. Find the likely ones based on the date stamp, and then type ```
sudo aptitude install [package names separated by spaces]
```

---

### Post by Locutus_of_Borg on 2007-09-29
thanks a lot.

and this will work without an internet connection?

---

### Post by MobiusNZ on 2007-09-29
Should do, if you're only reinstalling stuff. You may possibly need your install cd though.

---

### Post by Locutus_of_Borg on 2007-09-29
okay, i am much relieved now. 

thank you for helping

you get gold star! :KS

---

### Post by Locutus_of_Borg on 2007-09-29
It still tries to connect to the internet, and eventually times out.  I will try it with the disk inserted when I get home, I guess.

:(

---

### Post by MobiusNZ on 2007-09-30
If it still tries to connect to the net with the disk in, you may need to to edit your sources to only fetch from the cd.

To do that, open up a terminal and follow these steps.
First, backup your sources file:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```
Next, edit the sources file, using your preferred editor, eg:
```
sudo nano /etc/apt/sources.list
```
In this file, # means ignore line, or comment. Comment all the lines that have http in them by putting a # at the start of that line.
At the top of the file there should be the reference to the cdrom install location, probably commented out. Uncomment it. If its not there, you'll need to add one. Mine looks like 
```
deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
```
Yours will possibly be different - check the first line of your cdrom's README.diskdefine

Save the file then run (with your cd in)
```
sudo aptitude update
```

Then try reinstalling the rest of your stuff.

Hope that helps

---

### Post by Locutus_of_Borg on 2007-10-01
thanks, but i ended up just re-installing

all of my personal files were copied onto my windows partition, and i was able to get all additional applications re-downloaded and installed in a matter of a few hours

---

