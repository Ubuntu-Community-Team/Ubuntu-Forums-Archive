---
title: "Unity Help!"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by seojunkim on 2011-08-30
Operating System: Ubuntu 11.04 
                             ATI Radeon Xpress 1250
                             Intel Celeron 530m
                             15.1 inch display



Hi, I am a beginner who just escaped from the grasps of Microsoft. My Video card, according to "/usr/lib/nux/unity_support_test -p" can run Unity Perfectly. I am using an opensource driver. 

Results:
OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RS600
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

However, the screen cracks up when I use unity. I can't find the reason behind it. Please help me. Thank You (screenshot added in the desktop)

---

### Post by Frogs Hair on 2011-08-30
You may want to consider using the recommended ATI proprietary  driver if one is available in additional drivers .

---

### Post by Sef on 2011-08-30
> However, the screen cracks up when I use unity.

What do you mean by crack up?

---

### Post by 3rdalbum on 2011-08-30
> **Sef said:**
> What do you mean by crack up?

I imagine they're referring to the horizontal lines in the screenshot.

> You may want to consider using the recommended ATI proprietary driver if one is available in additional drivers .

The graphics card is no longer supported by ATI, so the only driver they can use is the one they're already using. Which isn't perfect, hence the lines.

If the horizontal lines are bothering you, you could try the non-3D version of Unity; it's in the "unity-2d" package that you can install through Ubuntu Software Center. You can change to Unity 2D at the login screen once you've installed it. It's almost identical to the 3D version, but it's just a little less flashy.

---

### Post by MiasXix on 2011-08-30
Also a new linux user, I got Unity 2D to see how it looked and functioned compared to 3D, and then I realized I couldn't get back to 3D, which I'd kind of like to do.  I checked the little box under the login, and found every possible GUI that isn't 3D.
You have any ideas?

---

### Post by snip3r8 on 2011-08-30
> **MiasXix said:**
> Also a new linux user

Well then I beleive a welcome is in order.
Welcome to the forum, ubuntu and linux.

Now to your problem.
Is the box you are checking to select unity at the login screen or in the settings for the login screen?
Also remember that unity 3d is just called unity ,unity 2d is the one that specifies that its 2d,if the problem persists you could just try and remove unity from the package manager or software center.

---

### Post by marin123 on 2011-08-30
tell me, are those cracks there everytime you bring out the dash? and are they in the same place everytime?

do you have ccsm installed? you could untick a few boxes and see if there's any improvement...

---

### Post by seojunkim on 2011-08-30
> **marin123 said:**
> tell me, are those cracks there everytime you bring out the dash? and are they in the same place everytime?

do you have ccsm installed? you could untick a few boxes and see if there's any improvement...

Yes, the lines are always there in the same spot with frequent color changes. I have ccsm installed, but I have no idea which one is creating the problem.

---

### Post by beew on 2011-08-30
Try to update your driver with this ppa. 

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

If you use open source drivers for either ATI or Nvidia graphic cards upgrading with xorg-edgers would do magic. The packages in the official repos were outdated even when Ubuntu was released. I had installed Ubuntu on a hp netbook and the graphic teared up exactly like yours, after updating with xorg-edgers it is now smooth as butter, same with another laptop with a Nvidia card.

---

### Post by seojunkim on 2011-08-31
> **beew said:**
> Try to update your driver with this ppa. 

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

If you use open source drivers for either ATI or Nvidia graphic cards upgrading with xorg-edgers would do magic. The packages in the official repos were outdated even when Ubuntu was released. I had installed Ubuntu on a hp netbook and the graphic teared up exactly like yours, after updating with xorg-edgers it is now smooth as butter, same with another laptop with a Nvidia card.

I did install it, but nothing changed. Im wondering if i actually did it correctly. Do you know how to check if the drivers are installed?

---

### Post by beew on 2011-08-31
> **seojunkim said:**
> I did install it, but nothing changed. Im wondering if i actually did it correctly. Do you know how to check if the drivers are installed?

Maybe you need to wait for updates? It is updated very rapidly, I get  a bunch of updates every few days.

To check if the xorg-edger packages are installed, open Synaptic, click on "origin" on the left panel and scroll to  find the entry for xorg-edgers (if it is not there it means it is not activated), if you find it then check what are installed.

---

### Post by marin123 on 2011-08-31
Try this:
open Compiz Config, then OpenGL and untick Sync to VBlank and see if the lines are still there.
If that doesn't work, scroll down to Image Loading section and untick Png.
I think that Unity shades are png files and if you disable that you may get rid of that lines. I'm not sure about this, it would be best if someone could back me up or tell me I'm wrong.

---

### Post by hreichgott on 2011-08-31
I second what Marin123 said. Also you can try just turning off all the compiz effects. I do that myself, because they conflict with too many things, and even when working properly they're kind of distracting.

Another option for drivers is the proprietary driver from ATI/AMD. go to amd.com and look for the "Find a Driver" dialog in the top right corner. Make sure you get the Linux version. You'll probably end up with some form of the Catalyst driver which is at least for Radeon cards, might be a better fit for yours. The driver installer is a .run file and can be downloaded to the desktop and run by double-clicking.

But before you go changing the graphics driver, make sure you do your research about how to boot into safe mode, how to boot into a text-only shell, and how to go back to your previous graphics driver when you've only got a text-only shell. Just in case a graphics driver happens not to give you any graphics at all.

---

### Post by beew on 2011-09-01
> **hreichgott said:**
> I second what Marin123 said. Also you can try just turning off all the compiz effects. I do that myself, because they conflict with too many things, and even when working properly they're kind of distracting.


How do you turn off Compiz in Unity?? Besides, why should OP? A beautiful and inviting desktop may be a "distraction" for you but it may be important to others.

Turning of Sync to Vblank in  Unity causes a lot more tearing on my Nvidia machine, maybe it would work differently with ATI.

---

### Post by 3rdalbum on 2011-09-01
I have no experience with using a PPA to update graphics drivers, so I'll just answer your other question.

Unity 3D is just called "Ubuntu" on the login screen. At the login screen, click on your username and then use the popup menu at the bottom of the screen to choose "Ubuntu", if you want to get back to the usual Unity 3D interface.

---

### Post by seojunkim on 2011-09-02
> **marin123 said:**
> Try this:
open Compiz Config, then OpenGL and untick Sync to VBlank and see if the lines are still there.
If that doesn't work, scroll down to Image Loading section and untick Png.
I think that Unity shades are png files and if you disable that you may get rid of that lines. I'm not sure about this, it would be best if someone could back me up or tell me I'm wrong.
Thankyou! That Actually removed the lines under the taskbar! However, the lines at the how do i call it the "Start Menu" didn't disappear yet. Could anyone shed some light on that? :)

---

### Post by marin123 on 2011-09-02
It seems you have opacity problem. I think it's because you have older graphic card, and open-source driver isn't that spectacular.
Panel's shadow is a PNG format picture and disabling Png in Compiz got rid of the shadow and the problems that it is causing.
Next thing you can do is expand the dash to fit your whole screen (in the bottom right corner click on the enlarge icon), and that might solve your problem.
And one more thing (if the above doesn't help). Go to Compiz Config -> Unity and set Dash Blur (in the Experimental tab) to No Blur.

---

### Post by seojunkim on 2011-09-03
> **marin123 said:**
> It seems you have opacity problem. I think it's because you have older graphic card, and open-source driver isn't that spectacular.
Panel's shadow is a PNG format picture and disabling Png in Compiz got rid of the shadow and the problems that it is causing.
Next thing you can do is expand the dash to fit your whole screen (in the bottom right corner click on the enlarge icon), and that might solve your problem.
And one more thing (if the above doesn't help). Go to Compiz Config -> Unity and set Dash Blur (in the Experimental tab) to No Blur.


The Dash blur was disabled already. Is there any workarounds to set my dash to automatically fit my whole screen so i don't have to expand it every time?
Thank you all for helping

---

### Post by marin123 on 2011-09-03
So it does help? Stretching the dash?

Install dconf-editor (sudo apt-get install dconf-editor), open it, go to Desktop -> Unity, and set Form-factor to Netbook.

---

### Post by seojunkim on 2011-09-03
Thanks to all of you, I now have a decent looking unity desktop. I don't know how to express this gratitude, but i really want to say that I appreciate what you guys have done for me. Thank you so much! God bless. :)

---

### Post by waynefoutz on 2011-09-03
I don't know how you pulled it off. I have a laptop with that same video card, I could not get Unity 3d working on it at all. Apparently it could not handle the new Compiz, because I couldn't get any acceleration to work either with the classic Gnome interface on 11.04 to work either. The only way I could get Unity to work on it was to log in with no compiz and use Unity 2d.  I ended up buying a new laptop, putting KDE  on the old one, which ran perfectly, and passing it down to my daughter.

---

