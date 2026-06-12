---
title: "upgraded from 9.04 to 9.10 and performance is slow"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by jim.v on 2010-05-23
I've been using Ubuntu since January on a dell vostro v13 (no windows dual boot) and its been a good experience.  any issues that came up I was able to resolve by searching thru the forums.  this one has me stuck though......

9.04 was working great and I stupidly decided to upgrade to 9.10.  Since then, the computer is terribly slow - closing a window will take seconds (and the cpu usage will climb to 100%), firefox will take forever to load up a simple web page.  previously, I could have couple applications open and the computer was still fairly snappy.  Now it is unusable.

Anyone have any advice?  any way to go back to 9.04?  ANy help would be appreciated

jim

---

### Post by Sef on 2010-05-23
> Anyone have any advice?  any way to go back to 9.04?  ANy help would be  appreciated

Only way to go back would be to reinstall 9.04.  Another option would be to upgrade to 10.04.  I would do a clean install since you are having problems with 9.10.

---

### Post by Kafubie on 2010-05-23
Yes,  A fresh install would do wonders for your machine.
Just back up your media on a USB flashdrive.

---

### Post by sylvester_0 on 2010-05-23
While I concur that an upgrade to $(latest) is in order, I'd try turning off visual effects (System -> Preferences -> Appearance -> Visual Effects) and see where that gets you.

---

### Post by jim.v on 2010-05-23
switching off visual effects helps a little, but the machine is still unusable.  how would I go about reinstalling 9.04?  or, how would I do a fresh install of 10.04 (iirc thats the latest)?

I'm not afraid of the terminal window, but I need "newb" friendly directions :)

one other thing, some other thread mentioned that the graphics card might have been disabled in the upgrade so that the cpu is now  responsible for refreshing the screen and thus the slowdown.  how could I check that?

thanks

jim

---

### Post by sylvester_0 on 2010-05-23
Do you have an ATI graphics card? ATI is known for EOL their products in short order.

Your best best is to install a fresh copy of 10.04. Download the latest live ISO from ubuntu.com (I'd use a .torrent) and burn it to a CD at the slowest speed. If you'd rather use a USB stick (at least 1GB), install UNetbootin (sudo apt-get install unetbootin), run it (sudo unetbootin) and choose to write the ISO you downloaded to your USB stick.

After that's done when you reboot choose to boot to your boot medium (USB or CD). I think you'll be able to figure it out from there.

---

### Post by skarme on 2010-05-23
How to upgrade to 10.04?
Make a live CD. Here's the link.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
Install a fresh copy; things would work fine.

---

### Post by jim.v on 2010-05-23
honestly, the fresh install route looks complicated to me, plus I lose all my settings/favorites/etc - I haven't done anything like that before and I want to exhaust other possibilities before going down that road.

so, how do I check if my graphics card (Mobile Intel Graphics Media Accelerator 4500MHD) is actually working?

jim



> **sylvester_0 said:**
> Do you have an ATI graphics card? ATI is known for EOL their products in short order.

Your best best is to install a fresh copy of 10.04. Download the latest live ISO from ubuntu.com (I'd use a .torrent) and burn it to a CD at the slowest speed. If you'd rather use a USB stick (at least 1GB), install UNetbootin (sudo apt-get install unetbootin), run it (sudo unetbootin) and choose to write the ISO you downloaded to your USB stick.

After that's done when you reboot choose to boot to your boot medium (USB or CD). I think you'll be able to figure it out from there.

---

### Post by mbzn on 2010-05-23
How long since your upgrade? I use my /home with clean install when i get a new ubuntu and on first boot after install the computer is usually useless for some time (leave it on for 15min then reboot and repeat) and after about the 4 or 5th reboot the speed is great. i guess it has to do with the importing of settings...

Or you might have had an unlucky upgrade(Hope this is not the case). Give it a hour or to and if the problem don't go away try a clean install of 10.04(That will surely solve it)

---

### Post by sylvester_0 on 2010-05-23
I believe there's only one intel driver available and there aren't really and settings that you can change. It's either going to work or not work at all.

You could try moving your current xorg.conf and restarting your GUI if you think that's the problem...

```
sudo mv /etc/X11/xorg.conf{,.old}
sudo service gdm restart
```

Edit: Why don't you just upgrade to 10.04, it won't hurt anything

```
sudo do-release-upgrade
```

---

### Post by jim.v on 2010-05-23
upgraded on saturday afternoon, hasn't worked properly since that time.  at least a half dozen reboots since than


> **mbzn said:**
> .......I use my /home with clean install.......

I'm sorry, I don't know what that means

jim

---

### Post by mbzn on 2010-05-23
Don't worry, in that case i was wrong anyway. (i meant that i use my old /home partition with a clean install).

---

### Post by jim.v on 2010-05-23
```
sudo mv /etc/X11/xorg.conf{,.old}
sudo service gdm restart
```tried this and it made no difference

```
sudo do-release-upgrade
```trying the upgrade now, will take a couple hours to download and install.  I'll let every know if that helps......

thanks

jim

---

### Post by jim.v on 2010-05-23
so I upgraded to 10.04 as recommended and things have gotten worse, now my track pad  doesn't work.  

I don't know if the other problems have been resolved since I can't do anything without the trackpad.

now what?

jim



> **jim.v said:**
> ```
sudo mv /etc/X11/xorg.conf{,.old}
sudo service gdm restart
```tried this and it made no difference

```
sudo do-release-upgrade
```trying the upgrade now, will take a couple hours to download and install.  I'll let every know if that helps......

thanks

jim

---

### Post by jim.v on 2010-05-23
the trackpad *and* keyboard are not working - since neither will knock the machine out screensaver mode.

what could have happened during the upgrade to do that?

is there any hope of returning this computer to a useful state?

jim

---

### Post by alphacrucis2 on 2010-05-24
> **jim.v said:**
> the trackpad *and* keyboard are not working - since neither will knock the machine out screensaver mode.

what could have happened during the upgrade to do that?

is there any hope of returning this computer to a useful state?

jim

Try creating a new user account and then login as the new user. Does it still run slow as the new user? 

Also try the following command from the terminal:

```
top
```

That will show what processes are chewing up resources.

---

### Post by jim.v on 2010-05-24
right now I'm stuck because the trackpad and keyboard are not functioning.  how do I get around this issue?

anyone?

jim


> **alphacrucis2 said:**
> Try creating a new user account and then login as the new user. Does it still run slow as the new user? 

Also try the following command from the terminal:

```
top
```That will show what processes are chewing up resources.

---

### Post by sylvester_0 on 2010-05-24
Do you have a USB mouse/keyboard that you could hookup to try to get it working again? If you do, I'd recommend doing that then pressing Ctrl-Alt-F1, logging in with your username and password, then running the first set of commands that I gave to you earlier (moving your xorg.conf.)

Also, it looks like the touchpad in your machine has issues: [http://en.community.dell.com/support-forums/software-os/f/3525/t/19324786.aspx](http://en.community.dell.com/support-forums/software-os/f/3525/t/19324786.aspx)

---

### Post by jim.v on 2010-05-24
> **sylvester_0 said:**
> Do you have a USB mouse/keyboard that you could hookup to try to get it working again? If you do, I'd recommend doing that then pressing Ctrl-Alt-F1, logging in with your username and password, then running the first set of commands that I gave to you earlier (moving your xorg.conf.)

Also, it looks like the touchpad in your machine has issues: [http://en.community.dell.com/support-forums/software-os/f/3525/t/19324786.aspx](http://en.community.dell.com/support-forums/software-os/f/3525/t/19324786.aspx)

I will bring my work keyboard/mouse home tonight and try those steps

jim

---

