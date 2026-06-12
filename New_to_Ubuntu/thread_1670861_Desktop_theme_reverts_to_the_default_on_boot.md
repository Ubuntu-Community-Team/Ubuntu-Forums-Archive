---
title: "Desktop theme reverts to the default on boot"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-01-19
I'm running 10.10 and noticed this the other day, so it just started.

If I shutdown or restart the computer my desktop icons and panel icons all show up as what I think is the default theme. (It's ugly.)  If I logout then log back in my preferred icons reappear. 

I've checked that the correct icons are selected in the appearances' preferences and they are.  I can try to change the icons during "an ugly session" to another choice but they don't change. The only thing I've found so far to get things back to the way I like them is to logout and log back in.

Has anyone else had this experience?  Does anyone know how I can find out what is going wrong during boot?

---

### Post by carrarin on 2011-01-19
yes, I have been having this same problem. Good to know I'm not crazy. :)

---

### Post by carrarin on 2011-01-19
yes, I have been having this same problem. Good to know I'm not crazy. :)

---

### Post by GrouchyGaijin on 2011-01-19
> **carrarin said:**
> yes, I have been having this same problem. Good to know I'm not crazy. :)

I'm glad that others are having this as well.  Any ideas on how to fix it?

---

### Post by GrouchyGaijin on 2011-01-31
bump

---

### Post by or3x on 2011-01-31
I also have this problem, sometimes when i log in, the theme is win95-gray, but if i open System - Preferences - Appearance, the theme looks as it should again. However nautilus is still weird, so i have to kill the nautilus process and start it again to fix that. It's starting to get a little annoying....

---

### Post by lavinog on 2011-01-31
First make sure you have the latest updates, by forcing a check of updates.

The title says lubuntu.  Lubuntu is still somewhat like a beta version, and may have its share of bugs.

Something like this may need to have a bug filed.
It would be helpful to mention what video card you have, and if you have desktop effects enabled.

---

### Post by lavinog on 2011-01-31
Also can you post a screenshot of the "ugly theme"

---

### Post by GrouchyGaijin on 2011-01-31
> **lavinog said:**
> Also can you post a screenshot of the "ugly theme"
Thank you for the reply.  My mistake, the title should be **_Ubuntu_** not Lbuntu. Is there a way I can correct that mistake?

I've checked the updates and I am up to date.  The next time it boots into the ugly session I'll post a shot.

Another problem update:  At first it was doing this at every boot.  Then I went for 20 or 30 boots without a problem.  Now it seems to be maybe 20% of the time.

---

### Post by GrouchyGaijin on 2011-01-31
Here are two screen shots of the ugly theme.

[IMG]http://jfniendorf.org/Screenshot-Pictures.png[/IMG]

[IMG]http://jfniendorf.org/Screenshot-3.png[/IMG]

The weird thing is that right after boot the panel as well as the menus (like applications) had icons I don't use, but in the 15 minutes or so the machine has been up all of those icons returned to the normal icons that I like.

Folders still have this ugly icon and the windows and any menus within the windows - like the contextual menu if you right click on a folder - seem to have a Win95 look to them although the borders to the windows are correct.

---

### Post by GrouchyGaijin on 2011-01-31
> **or3x said:**
> I also have this problem, sometimes when i log in, the theme is win95-gray, but if i open System - Preferences - Appearance, the theme looks as it should again. However nautilus is still weird, so i have to kill the nautilus process and start it again to fix that. It's starting to get a little annoying....

Exactly - I just killed nautilus and restarted it and everything is the way it should be.

---

### Post by Orbital_sFear on 2011-02-09
Same issue here.  I have to log in and out several times before my theme loads correctly.  Sounds like Nautilus isn't starting correctly.

I dug around and found this link:
[http://ubuntuforums.org/showthread.php?t=1575703&page=15](http://ubuntuforums.org/showthread.php?t=1575703&page=15)

Specifically this post from msandoy:

> I had this problem, and I think I have found a sollution.
Do a : sudo gconf-editor
Go into apps>nautilus>preferences, and scroll all the way down. The next to last item should say theme. edit the item, and remove the word default.
Close gconf-editor, log out and log back in. Now the themes should show up correctly in nautilus again. At least it worked for me, with nVidia GFX and 10.10 64bit.


I just tried it, not sure about the results.  A few people say it worked.  I'd rather put in the theme I want it to load, however I'm going to do as the post says and see how it goes.

Note, I didn't type sudo, and I don't think you should have to.

Hope this helps someone

-Orbital

---

### Post by Orbital_sFear on 2011-02-09
Alright, so my previous post didn't work, don't bother.  But, I found another post that does seem to have worked.

Open synaptic.  search for nautilus, right click, reinstall, apply.

I logged out, then logged back in and everything is good now. I read that they fixed the problem, but old configs may still cause the issue.

-Oribtal

---

### Post by Perfect Storm on 2011-02-10
Try this:

```
sudo nano /etc/xdg/autostart/gnome-settings-daemon.desktop
```

Change **Exec** to

```
Exec= bash -c "sleep 2; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"
```

---

### Post by victor9098 on 2011-03-13
None of the above worked for me. Same problem and it just keeps coming back. Only killing nautilus after every start up fixes it. Only a new issue for me, about 2-3 weeks old, very frustrating

---

### Post by atti84it on 2011-08-22
I had the same problem and solved with:
> I had this problem, and I think I have found a sollution.
 Do a : sudo gconf-editor
 Go into apps>nautilus>preferences, and scroll all the way down. The next to last item should say theme. edit the item, and remove the word default.
 Close gconf-editor, log out and log back in. Now the themes should show up correctly in nautilus again. At least it worked for me, with nVidia GFX and 10.10 64bit.

Anyway it's annoying! Looking for better solitions..

---

### Post by 2CV67 on 2011-08-22
Just seen this thread.

I have the same problem & described it with screenshot here:
[http://ubuntuforums.org/showthread.php?t=1824374](http://ubuntuforums.org/showthread.php?t=1824374)

Interested in all solutions!

---

### Post by amjjawad on 2011-08-28
> **atti84it said:**
> I had the same problem and solved with:


Anyway it's annoying! Looking for better solitions..

What release are you using? Lubuntu 11.04? 10.10? 10.04?

I suggest to use Lubuntu 11.04.

---

