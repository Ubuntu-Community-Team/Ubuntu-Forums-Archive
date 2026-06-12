---
title: "iTunes"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by Jynxx on 2009-01-08
Is there a version of iTunes for Ubuntu? If so, where would I go to get it?

Thanks!

---

### Post by Zack McCool on 2009-01-08
No, there is not.  There are other apps that can read and write to an iPod, but they will not work with the iTunes store.

I use Amarok with my iPod 30GB G5.

---

### Post by lovelyvik293 on 2009-01-08
No there is no itunes for the linux is avaliable.Try using the Rhythmbox.

---

### Post by Darkade on 2009-01-08
No iTunes is not supported for linux.

If you want to sync your iPhone There are other apps that can do it, my favorite is gtkpod. 

If you want to hear music you can use Rhythmbox, which is similar and pretty stable and simple. Songbird is also similar to iTunes and you can get it [here]("http://getsongbird.com/") it has lots of features. You can also install Amarok, I really don't like it but a lot of people seem to love it

---

### Post by rururudy on 2009-01-08
You can get it to run -- with limited functionality -- using 'wine'.  Wine is a Windows Emulator.

I don't really recommend you use it under wine, but one day it may work better.  I can't sync to my iPod, but I can use it to play music.

Me personally?  I use 'mpd' to play the music and 'Sonata' as the frontend.  I like mpd because I can logout and the music still plays.

---

### Post by Jynxx on 2009-01-08
So will the Ipod sync with one of these other programs and will it allow me to load and unload music from it?

---

### Post by lovelyvik293 on 2009-01-08
Yes all of them can sync with the ipod.But i have some problem with the ipod classic.

---

### Post by Darkade on 2009-01-08
> **Jynxx said:**
> So will the Ipod sync with one of these other programs and will it allow me to load and unload music from it?
Whit Amarok, and Rhythmbox you can sync. I don't know about Amarok sync but rhythmbox sync is buggy. That's the reason I use gtkpod (which is just an app to sync) It's super fast and really efficient.

---

### Post by scorp123 on 2009-01-08
> **Jynxx said:**
> Is there a version of iTunes for Ubuntu?  If you absolutely must use iTunes e.g. in order to update the firmware of your iPhone ... you could use VirtualBox (make sure you use the "PUEL" edition; not the "OSE" edition: that one does not have USB support!) and install Windows XP into a virtual machine, and then use iTunes inside of it. When you connect your iPhone to your Ubuntu machine via the USB cable, a message may pop-up about a "New camera discovered ..." ... just click on "Ignore", then assign the iPhone to the virtual Windows XP (via the "USB Device" menu on VirtualBox). There is one phase during the firmware update where an iPhone will switch into a maintenance mode, therefore changing it's USB device ID. You will notice because the update process inside the virtual Windows XP appears to hang. Simply assign the iPhone again to the virtual machine and it will continue and work OK. I have updated a few iPhones like that and it works.

How to get Sun xVM VirtualBox 2.10 via repository (Synaptic / "apt-get"):
[http://ubuntuforums.org/showpost.php?p=6332363&postcount=16](http://ubuntuforums.org/showpost.php?p=6332363&postcount=16)

---

### Post by Jynxx on 2009-01-08
Awesome. I have the nano and love my music so its nice to hear that they will sync with the beast. lol

---

### Post by lovelyvik293 on 2009-01-08
+1 to gtkpod.

---

### Post by Jynxx on 2009-01-08
Can I get gtkpod from the repository in add/delete software?

---

### Post by Darkade on 2009-01-08
> **Jynxx said:**
> Awesome. I have the nano and love my music so its nice to hear that they will sync with the beast. lol
A nano would totally work, my girlfriend has one and it completely works

> Can I get gtkpod from the repository in add/delete software?
Yes there it is :D

---

### Post by scorp123 on 2009-01-08
> **Jynxx said:**
> Can I get gtkpod from the repository in add/delete software? You could easily check that yourself, you know? :D  And you can also do it real quick via terminal ... so for the sake of completeness - the right command to use here would be "**apt-cache search NameOfProgramHere**" ... so if we do it for "**gtkpod**" we get this:
```
> apt-cache search gtkpod
gpixpod - Organize photos on your iPod, freely!
gtkpod - manage songs and playlists on an Apple iPod
gtkpod-aac - manage songs and playlists on an Apple iPod
```
The left column represents the names of the packages that you'd need to get. So either type in those names into "Synaptic" or feed them to "sudo apt-get install ... ", e.g.:
```
sudo apt-get install gtkpod
``` ... This will pull the program and all its dependencies from the repositories and install it for you.

---

### Post by Vantrax on 2009-01-08
Mozilla also recently launched songbird which is supposed to have the functionality of iTunes but connected to the Amazon store instead.

Might be worth a check.

---

### Post by Jynxx on 2009-01-08
True, sorry. Not at home where I could check that. I'm at work on the windows box.  :D

---

### Post by evilkastel on 2009-01-08
I prefer Banshee (updated, the one in the repos works badly) over everything. worth a try, i'll say.

---

