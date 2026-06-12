---
title: "Can i change from gnome to KDE"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by krdan4th on 2009-02-11
I have installed on my system Ubuntu 8.10 and I was wondering if there is any way I could change the desktop enviornment from gnome to KDE 4 with out having to delete Ubuntu to install Kubuntu.

---

### Post by TWO on 2009-02-11
> **krdan4th said:**
> I have installed on my system Ubuntu 8.10 and I was wondering if there is any way I could change the desktop enviornment from gnome to KDE 4 with out having to delete Ubuntu to install Kubuntu.

Yes. Simply open up the **Terminal **and type in

```
sudo apt-get install kubuntu-desktop
```Press Y to confirm then let it run.

Restart, and then once you get back to the log in screen select KDE for the session type.

Kubuntu will now be installed next to Ubuntu, and you'll simply need to pick a different session type at the login screen. Bare in mind though that you'll see a mixture of KDE and GNOME apps in your menus, making them slightly clogged looking.


Hope you enjoy KDE 4. :)

---

### Post by Kobalt on 2009-02-11
Yes, you can have both desktop environments in parallel, just install the kubuntu-desktop package from Synaptic. 
After this, from the login screen you'll be able to chose in which DE you want to log in.

---

### Post by KaiHeimann on 2009-02-11
There are a number of ways that you can do that, but the best way by far in my opinion is to use adept to install the parts of KDE4 that you want. You can find instructions on how to do that [here]("https://help.ubuntu.com/community/InstallingKDE")

Hope that helps. :)

---

### Post by PalacePainter on 2009-02-11
Are there any conflicts with having both gnome and kde in same system?

Are there any problems caused when you run a cleaner in such a system?

---

### Post by Kobalt on 2009-02-11
There are no problems having both Gnome and KDE.
What do you mean by cleaner ?

---

### Post by PalacePainter on 2009-02-11
Software that removes junk from hd.

---

### Post by TWO on 2009-02-11
> **PalacePainter said:**
> Software that removes junk from hd.
 
Define "junk."

Most you can do is remove *residual config *and *partial packages.*

Look at the following how-to page:

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

I'd only really bother with the aforementioned bits of "junk" in that how-to, unless you want to go all out.

I personally only ever run:

```
sudo apt-get autoremove
``````
sudo apt-get autoclean
```in the Terminal.

---

### Post by Kobalt on 2009-02-11
I highly recommend that you only use commands or softwares that you fully understand before trying to "clean" your system. 
Ubuntu is pretty tidy, there shouldn't be much action needed from your side in order to keep it clean.

---

### Post by PalacePainter on 2009-02-11
I tried those cleaners, and I suspect they removed items that left the OS damaged?  

Do they damage Ubuntu?

---

### Post by PalacePainter on 2009-02-11
Does Ubuntu Linux collect duplicates and triplicates scattered all over the hd like Windows did?  I.E.: "Junk".

What junk does a Ubuntu reboot clean out? if any.  Or does Ubuntu just not get junked up with junk?

Does Ubuntu RAM need cleaning like Windows RAM does, by an occasional reboot, or with a software like how "Cacheman Memory Restore" works in Windows?

---

