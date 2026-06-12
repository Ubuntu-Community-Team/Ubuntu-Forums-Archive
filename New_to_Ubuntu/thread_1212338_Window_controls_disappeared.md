---
title: "Window controls disappeared"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by typos1 on 2009-07-13
I ve lost all my minimise/maximise/change window size/close window controls at the top right of all windows(except tabs in firefox). Have I accidently done something? Cant work out what and spent ages tryin to get them back.

---

### Post by tarps87 on 2009-07-14
1) Have you still got the tile bar?
2) Are you using compiz?
3) Are you using emerald?

---

### Post by typos1 on 2009-07-14
Yeh still got the title bar just have to use the bar at the bottom of the screen to minimise close etc-What are compiz and emerald?!

---

### Post by tarps87 on 2009-07-14
They are window managers, if they are installed they will appear under System -> Preferences
If you can not find them in there try going in the appearance settings and changing the theme

---

### Post by typos1 on 2009-07-14
Changed theme but not made any difference. 2 days ago I changed visual effects from normal to extra and back again and it happened after that.

Now it wont let me perform adminastaive tasks-I ve got a software update to install and when I hit install the screen goes greyed out with a blank box in the middle-normaly I d have to type my password in the box, but it just hangs with greyed out screen. The only way to get out of it is to press esc. Tried to go into the list of installed apps, but wont let me cos need pasword.

Still, Im  getting used to having loads of bugs:

cant empty deleted emails folder all of a sudden,
got no sound for movies,
cant install flash player,
cant watch iplayer,
amsn plugins wont install,
amsn cant find cam (but ubuntu can)
and now it wont let me do admin tasks

Much as I hate to say it, at the moment it seems windows has way fewer bugs

---

### Post by tarps87 on 2009-07-14
It seems like it maybe related to compiz, when you enable visual effects this enable compiz.
Try
```
metacity --replace
```
if this does not work try
```
compiz --replace
```

Note: If at any point you can not open a terminal press alt+ctrl+F1 and login "sudo reboot" will restart the computer

for flash, movies and probably iplayer
```
sudo apt-get install ubuntu-restricted-extras
```

Id don't know about amsn as I don't use it.

For admin tasks, at the moment sudo *command*

Have you installed any other drivers?
[coed]sudo /usr/bin/jockey-gtk
[/code]
If so try disabling it.

---

### Post by typos1 on 2009-07-16
When I open a terminal its the same as when the update manager asks for my password-blank screen. I got round this with update manager by typing my password and hitting enter even though I couldnt see anything and it worked-the updates were installed. So I did the same with the terminal and after I hit enter I could see the terminal window and got all my window controls back! Then I tried to close the terminal and it said there was a programme still running. I closed it anyway and the termianl went blank again and after that the whole top bar of the each window disappeared not just the controls. The whole desktop froze. Re-booted and tried compiz-replace. No changes but get same prob when try to close terminal.

Using "clear looks" from appearance setting and the on/of controls have disappeared-only way to turn pc off is to use on/off button on tower.

---

### Post by tarps87 on 2009-07-16
> **typos1 said:**
> When I open a terminal its the same as when the update manager asks for my password-blank screen. I got round this with update manager by typing my password and hitting enter even though I couldnt see anything and it worked-the updates were installed. So I did the same with the terminal and after I hit enter I could see the terminal window and got all my window controls back! Then I tried to close the terminal and it said there was a programme still running. I closed it anyway and the termianl went blank again and after that the whole top bar of the each window disappeared not just the controls. The whole desktop froze. Re-booted and tried compiz-replace. No changes but get same prob when try to close terminal.

Using "clear looks" from appearance setting and the on/of controls have disappeared-only way to turn pc off is to use on/off button on tower.

What do you mean when you open the terminal it asks for you password?
Before or after you try to run a command with sudo?
If you are using sudo in the terminal you should see the prompt
password:
then when you type you will see nothing, this is the way it has been designed.

Did the buttons appear when the terminal did or when you typed a command?

---

### Post by ~sHyLoCk~ on 2009-07-16
What happens when you type ```
metacity --replace&
```

---

### Post by typos1 on 2009-07-17
> **tarps87 said:**
> What do you mean when you open the terminal it asks for you password?
Before or after you try to run a command with sudo?
If you are using sudo in the terminal you should see the prompt
password:
then when you type you will see nothing, this is the way it has been designed.

Did the buttons appear when the terminal did or when you typed a command?

Sorry, the terminal is blank (get a white empty box) as well (and so are the info boxes if I unplug the internet or connect my pda) and I ve done loads of sudo stuff in it in the past  when it asks for password-it doesnt ask for password with these commands, but as the terminal was blank I couldnt see what was in it, I just remembered having to type it in a lot when using a terminal. Typed in "metacity --replace&" as shylock says and that has sorted it, but only if I keep the terminal open. If I close it it is minimised NOT closed, you cant do anything else in it and all the windows controls disapear again.

---

### Post by ~sHyLoCk~ on 2009-07-17
> **typos1 said:**
> Typed in "metacity --replace&" as shylock says and that has sorted it, but only if I keep the terminal open. If I close it it is minimised NOT closed, you cant do anything else in it and all the windows controls disapear again.
Do this:
Goto Startup applications[somewhere in system->preferences] and add a new entry ```
metacity --replace&

```
reboot and see if things get sorted!

---

### Post by typos1 on 2009-07-18
Makes no difference

---

### Post by jrothwell97 on 2009-07-18
OK, try this.

Reboot. If everything is still very borderless, open up a terminal and run ```
metacity --replace
```

Metacity is what we call the *window decorator* (Emerald is another one, although it's not installed by default) and it's responsible for handling the window border, title bar, controls, etc.

It has to be said though, what's happenning is very odd. This all happened after you enabled and disabled visual effects?

---

### Post by ~sHyLoCk~ on 2009-07-18
> **typos1 said:**
> Makes no difference

Save this as auto.sh

```
#!/bin/bash
metacity --replace&
```

Then put it anywhere you prefer. Open terminal and cd to that directory.

```
cd /path/to/script
sudo chmod +x auto.sh

```

Goto System->Preferences->Startup Applications and add a new entry :
name: whatever you like
add the path to the script. Reboot

```
sudo shutdown -r now
```

Btw, metcaity shouldn't need this fix since it's the default WM for Gnome, I think you messed up your system somehwere.

---

### Post by typos1 on 2009-07-18
My system is messed up anyway, its so buggy!

I didnt do anything other than change to the highest visual effects setting and back again

Where do I type 
#!/bin/bash
metacity --replace&in a terminal?

---

### Post by 4Orbs on 2009-07-18
Have you tried turning off the visual effects, then turning them back on to normal?

---

### Post by Shpongle on 2009-07-18
it sounds like you enabled compiz but without window decorations, ok i posted a screenshot of where to enter the code ,go to system-> preferences -> startup applications and copy what i have in the screen &  replace compiz with metacity and save it and log out and back in

---

### Post by ~sHyLoCk~ on 2009-07-18
> **typos1 said:**
> My system is messed up anyway, its so buggy!

I didnt do anything other than change to the highest visual effects setting and back again

Where do I type 
#!/bin/bash
metacity --replace&in a terminal?

Type that in a text file and save it and then follow the rest using terminal.

---

### Post by typos1 on 2009-07-19
I ve tried putting compiz and metacity in sartup progs, neither makes any difference. I put visual effects to none and that brings the window controls back. It was on normal before with window controls, just going to extra and back to normal caused the prob. The strange thing is that before normal would have window controls but now normal doesnt and neither does extra. weird. But then unfortunately ubuntu seems to have lots of strange little bugs so far. I ve changed to clearlooks for appearence and this has no on/off button. Is this unique to clearlooks or another bug?

---

### Post by typos1 on 2009-07-19
Just checked, for some reason clearlooks doesnt have on/off button

---

### Post by wojox on 2009-07-19
No on or off button?
Do you see a little green man running?

---

### Post by 4Orbs on 2009-07-19
You say that turning off the effects brings back the window controls. I had the same problem. In my case the problem was caused by changing screen resolution using the nVidia Settings Mgr. I suggest setting your screen resolution back (as root, using nvidia settings mgr) to "Auto" or "Default", then try turning the effects back on. If doing this brings back the window controls while the effects are on, then you'll need to edit the xorg.conf file in order to assign your preferred screen resolution (rather than use the nVidia Settings Mgr).

---

### Post by typos1 on 2009-07-19
Yes saw the green man Wojox, was that the on/off control?

Everytime I boot up I have to manually change visual effects to "none" to get window controls. Already had loads of problems with the res-I only get 2 very very low resolution in default and it would always go back when I booted up. Had to put something in startup apps. Do you mean NvDIA X sever settimgs? Got no settings manager

---

### Post by 4Orbs on 2009-07-19
If you have the nVidia restricted driver activated, then you should use the nVidia xserver settings mgr to change screen resolution (as root). After selecting your preferred resolution you need to click the button on the bottom to save your settings to xorg.conf file (at /etc/X11/xorg.conf). This assigns your preferred resolution as default for all user accounts and also makes the login screen display your chosen resolution. But if doing this makes the window controls disappear when you activate the effects, then you need to change your resolution by manually editing the xorg.conf rather than by using the nVidia xserver settings mgr.

To open the nVidia xserver settings mgr as root, enter this into a terminal:
```
gksudo nvidia-settings
```
Then make the changes and save as described above, then reboot. Doing it this way will make the changes stick through repeated reboots.

---

