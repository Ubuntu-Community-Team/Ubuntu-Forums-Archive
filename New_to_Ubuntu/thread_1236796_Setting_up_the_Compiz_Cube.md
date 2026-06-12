---
title: "Setting up the Compiz Cube"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by Stevie78 on 2009-08-10
Ive followed all the steps of various tutorials for getting the Compiz cube up, they all tell me the same thing and it still doesnt work.

All I can see is the desktop windows in a line which I can scroll left and right with the arrow keys, holding down Ctrl+Alt.

What am I missing out?

Could someone please list all the options that MUST be enabled for the cube to work at least rudimentarily? Right now all Ive got is 2D.  Thanks...

---

### Post by Schendje on 2009-08-10
Stupid question, but have you tried holding Ctrl+Alt, then holding down your mouse button and moving it to turn the cube?

I'll go have a look at which settings I've got on...

---

### Post by overdrank on 2009-08-10
> **Stevie78 said:**
> Ive followed all the steps of various tutorials for getting the Compiz cube up, they all tell me the same thing and it still doesnt work.

All I can see is the desktop windows in a line which I can scroll left and right with the arrow keys, holding down Ctrl+Alt.

What am I missing out?

Could someone please list all the options that MUST be enabled for the cube to work at least rudimentarily? Right now all Ive got is 2D.  Thanks...

You may look at the FAQ's link in my signature. :)

---

### Post by frt975 on 2009-08-10
Deselect desktop wall and select desktop cube.

---

### Post by MrJoeyUK on 2009-08-10
Once you have compiz enabled, you have to enable desktop cube AND rotate cube, and ensure desktop wall is disabled (which will be by default once desktop cube is enabled).

Then you need to right click either one of your two desktop squares in the bottom corner and click preferences.. there you can edit the amount of sides it has. E.G 4 columns = 4 sides of the cube.

Then, the default key to use it is CTRL + ALT + Left or Right.. or you can hold CTRL + ALT + Mouse Click and wheel around.

---

### Post by Stevie78 on 2009-08-11
I had done all these of course but it doesnt work:

Rotate Cube: already enabled

Ctrl+Alt plus left/right arrow or mouse: As I said theres only a row of desktop windows scrolling left and right - but no cube.
Holding the left mouse button down there moves the active window and everything else (except the Skydome background pic) disappears

Desktop Wall: disabled

Also I changed my desktop size to 4 - 1 - 1 as advised but it still doesnt work.

---

### Post by Stevie78 on 2009-08-11
> **overdrank said:**
> You may look at the FAQ's link in my signature. :)

They are awesome, Ill work my way through them later and get back with a report.

---

### Post by Schendje on 2009-08-11
Don't know if this is much help, but I exported my Compiz profile. Simply unpack it, then import it at CompizConfig Settings -> Preferences (don't forget to export your own first!).

Maybe that will do the trick, as you'd have all the same settings as I do. Good luck.

---

### Post by Stevie78 on 2009-08-11
Ok Ive tried a few things: First, installation according to specs in overdrank's FAQ: Same result and no cube

Schendje Ive substituted my profile settings with yours and it still doesnt work. Its exactly the same problem as before. I see a row of four desktop windows which I can scroll left to right and thats it.
The background is black but thats only cos theres no background pic so no problems there. 

I have no idea what Im missing.

Just for reference, I have an ATI Radeon 2100 graphics card.


There must be some unusal option that blocks me from going from 2d to 3d... any ideas??

---

### Post by Stevie78 on 2009-08-11
I went back to default settings, enabled and changed everything that Im supposed to change and I get the cube effect without zoom, ie I go Ctrl+Alt and left and right arrow only and I see it spinning over to the next desktop window.

No 3d when I go Ctrl+Alt+down arrow though... :(

---

### Post by pizza-is-good on 2009-08-11
Do you have the Compiz-Fusion Icon installed?
 
I enabled the cube through it, with no problems.

---

### Post by Stevie78 on 2009-08-11
Well I cant see a Fusion icon in CompizConfig Settings Manager if you mean that.

The following packages are all installed:

compiz
compiz-core
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-fusion-plugins-unsupported
compiz-gnome
compiz-plugins
compiz-wrapper


Not installed are the kde ones obviously and also compiz-dev and compiz-fusion-bcop arent. The latter one I guess I wouldnt need as I never had Beryl and theres nothing to reconcile.

---

### Post by pizza-is-good on 2009-08-11
In 'add/remove...', search Fusion under 'all available apps', and add Compiz Fusion Icon.
 
That's what I was talking about. Sorry for the confusion.
 
Hopefully this works.

---

### Post by Stevie78 on 2009-08-11
Hmm its getting stranger by the minute. I did indeed not have the Compiz Fusion Icon installed. So Ive done that and then it appeared in Applications > System Tools. However when I click on it, nothing happens - the menu just closes and the cube is still not there.

Also I cant see the icon appear anywhere else...

I must be missing some kind of essential package maybe??

---

### Post by pizza-is-good on 2009-08-12
OK, here are instructions. Hopefully this works.

1. Add the programs shown on image 1.

2. Start the Fusion Icon as shown in image 2.

3. The icon should appear as shown in image 3.

4. Right click on the Fusion-Icon and click on 'settings manager' as shown on image 4.

5. Check the boxes for 'Desktop Cube' and 'Rotate Cube' in the 'Desktop' section as shown on image 5.

6. Enable desktop effects to 'Extra' by right clicking on the desktop >> Change Desktop Background >> Visual Effects >> Extra.

I did all of this on a new install of Jaunty in VBox and it worked flawlessly. If any of the apps to install on step 1 are already installed, I would un-install them and then install them again, but that's just me.

Good luck!

---

### Post by Stevie78 on 2009-08-14
Ok so far so good. I had forgotten to install the Desktop Effects in Add/Remove (which I did).

Then I click on the Compiz Fusion Icon in Applications > System Tools and again nothing happens. The icon also doesnt show up anywhere on the menu bar. I dragged it there manually and clicked on properties and it says:

fusion-icon --no-start

1) whats the command that should be there (if any)
2) Wouldnt it be enough accessing the Compiz settings via System > Preferences > CompizConfig Settings Manager?

---

### Post by psycho reaper on 2009-08-18
Hi there,

im kinda new to ubuntu and linux in general. i run 8.04 on my laptop and have no issues with compiz. My friend however is running 9.04 and i am having a similar issue as the original poster of this thread while trying to set up her cube. please help... nothing in this thread has helped thus far.

---

### Post by Stevie78 on 2009-08-21
Im still stuck and tried out all suggested here plus changing various other settings in CCSM - and with no effect.

I assume Im missing a vital package...but which one? 

Just for info Ive got an AMD Athlon LE-1640 (1 GHz) and an ATI 2100 graphics card. What about your friend's PC?



Maybe the issue will be resolved when I upgrade to 9.10 in a couple of months...

---

### Post by KinKiac on 2009-08-21
> **Stevie78 said:**
> Im still stuck and tried out all suggested here plus changing various other settings in CCSM - and with no effect.

I assume Im missing a vital package...but which one? 

Just for info Ive got an AMD Athlon LE-1640 (1 GHz) and an ATI 2100 graphics card. What about your friend's PC?



Maybe the issue will be resolved when I upgrade to 9.10 in a couple of months...

You said in one of your posts that you managed to get the cube to rotate but it just switched sides without zooming it out first?  If this is correct then you only need to adjust the "zoom" option in rotate cube.  The higher it is, I think, the more it zooms out when you rotate.  You might want to check out the key bindings in rotate cube as well, to make sure they are enabled.  

Other than that, have you made sure your desktop effects are enabled?
What kind of video card do you have?  Does it support GLX and/or openGL?  I was having the same problem when my xorg.conf file got messed up and even though I had the nvidia drivers installed the GLX wasnt working.  Also, what other options do you have enabled?  I found that there are a couple of plugins(extra or experimental I think) that crash my compiz and sets me back to metacity.  

I dont know if any of this helps, but I try.

(whoops, sorry I didnt see your other post with the graphics card on it)
EDIT:  Ok so you have the ATI 2100, 1 question, is this integrated video or and expansion video card?  Ive searched google for it and I get a few hits that say ATI 2100 "integrated".  If so this may be your problem.

---

### Post by cataztrophe on 2009-08-22
wohoo..many thanx for all user that contributed on this thread, nice info!

---

### Post by atngplusultra on 2009-08-22
hopefully the OP got the Compiz Fusion Icon working, because I was having a similar problem, and my solution was this:

right click the icon, go to Compiz Options, and UNmark the checkbox for Indirect Rendering.
Everything is back now, except for my separate desktop images, which i can normally set up in a minute

---

### Post by Stevie78 on 2009-08-22
> **KinKiac said:**
> 
EDIT:  Ok so you have the ATI 2100, 1 question, is this integrated video or and expansion video card?  Ive searched google for it and I get a few hits that say ATI 2100 "integrated".  If so this may be your problem.


Thats what I think as well but I dont know how to fix it. Incidentally I have slow and/or badly running 3D graphics in general (e.g in FlightGear or Torcs - both barely playable)

Ive looked for up-to-date ATI 2100 drivers on the manufacturers website but there arent any.

Is there another location or maybe another driver for a similar ATI card (which one) that may resolve this.



Also, when I talked about the zoom issue I meant that there still is no cube (Ctrl+Alt+Down Arrow). I see a row of the four desktops and can scroll them left and right. Holding down the left mouse button doesnt do anything (unless I enable 3D windows in CCSM, then the desktops disappear and only the selected window is movable).

If I just hold down Ctrl+Alt and then left or right arrow I get a cube-spin effect when moving me to the adjacent desktop left or right.

If anyone could solve the ATI driver/OpenGL/3D display issue that would be great. I think that will get the cube (and other things) working.

---

### Post by Stevie78 on 2009-08-22
> **atngplusultra said:**
> hopefully the OP got the Compiz Fusion Icon working, because I was having a similar problem, and my solution was this:

right click the icon, go to Compiz Options, and UNmark the checkbox for Indirect Rendering.
Everything is back now, except for my separate desktop images, which i can normally set up in a minute


Doesnt work. I cant right-click the icon and get 'Compiz Options'. Is there anywhere in the Compiz Settings Manager where I can turn Indirect Rendering off?

---

### Post by atngplusultra on 2009-08-23
hopefully you found this page:

[http://wiki.compiz-fusion.org/Troubleshooting](http://wiki.compiz-fusion.org/Troubleshooting)

wherein it says:
> If you are using an ATI card, Compiz Fusion requires at least a Radeon 7000 (or M6). From the 7000 to the X1050, you can use AIGLX with the open source ati driver. All X1xxx series cards and the Xpress 200(M) must use the proprietary fglrx driver. Using driver version >= 8.3 (gentoo 8.4.XXX) is recommended as AIGLX is available as of 8.3. If you decide to use older fglrx drivers, you're stuck with Xgl.

I'd follow any official suggestions from that site.

---

### Post by Stevie78 on 2009-08-25
It didnt work.

I think its a graphics card vs Linux driver issue. A driver update for my ATI 2100 with the installation of the Catalyst Control Center plus xorg will only cause the graphics to become corrupted and causes this problem:

[http://ubuntuforums.org/showthread.php?t=1156640](http://ubuntuforums.org/showthread.php?t=1156640)

...which took a while to repair.

I advise anyone with an ATI 2100 not to try and 'upgrade' like I did.

At the moment I cant see any other solution than getting a different (better supported) graphics card.

---

