---
title: "Drivers and .run files"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by ubuntienewb on 2011-05-13
as you can probably guess im a first time user of ubuntu (linux in general) i have ubuntu 11.4 and a little while ago the additional drivers thingy (yeah very technical me) told me i was missing a graphics card driver i have a Radeon HD 5670, so i installed, and it said i needed to reboot. after i rebooted the screen stayed blank and a little message popped up on the screen saying unsupported video type, so now i can only run ubuntu in graphical failsafe mode (i think thats what its called) so i went to the website and downloaded the drivers for it, but it comes as a .run file and just like .bin files (havent figured out how to use them yet either) i cant run it... i have spent the last 2 hours feeling like im banging my head against a table so any help would be greatly appreciated!

---

### Post by Jesus_Valdez on 2011-05-13
Go to "System -> Administration -> Additional Drivers" and try to choose different drivers for your graphic card.

---

### Post by 3602 on 2011-05-13
Um... fglrx I see.
Do a
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then reboot. Hopefully you will get a GUI. In the many instances where my dcking around resulted in a no-GUI problem that above command solves it.
Then...
(if the Steps 1 and 2 both return "no such file" or some "cannot find" type of errors proceed to step 3.)
**Step 1.**
```
sudo /usr/share/ati/fglrx-uninstall.sh
```If this returns "no such file or directory" it's fine. Proceed.
**Step 2.**
```
sudo apt-get remove --purge fglrx*
```This will *probably* return a couple of warnings: */usr/share/lib/fglrx* and */usr/share/lib32/fglrx *not empty. You do:
```
sudo rm -rf /usr/share/lib/fglrx
```and
```
sudo rm -rf /usr/share/lib32/fglrx
```Proceed.
**Step 3. COPY THIS DOWN on some papers before doing it!**
Reboot. When in the purple boot screen with flashing dots, press F1 key  to get into the emergency recovery board (white-on-black screen). Do:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```Then 
```
sudo reboot
```You will get a GUI.
**Step 4.**
*cd* into whatever dir you have the .run file.
You might want to
```
sudo apt-get install libqtgui4
```Then
```
sudo sh (your installation file).run --buildpkg  Ubuntu/natty
```Wait. A Synaptic window might pop up if you're doing  this for the first time. Let it go away. 
Later you'll see the xterm returning four packages built.
Now
```
sudo dpkg -i *.deb
```Wait.
**Step 5.**
```
sudo aticonfig --initial -f
```then
```
sudo reboot
```then
```
fglrxinfo
```If the last command returnes "MESA" then report back.
Else enjoy.

---

### Post by ubuntienewb on 2011-05-14
this is probably a stupid question but imma have to ask anyway
the only additional driver is for  a proprietary FGLRX graphics driver.
whats FGLRX and does it encompass the radeon HD 5 series? because i have a feeling that this is the same driver name i installed that made it blow up.
thanks for all the helps.

also i should probably mention im running the pc from a vga port on the back of my sony tv not a normal monitor.

---

### Post by ubuntienewb on 2011-05-14
right small problem now. i cant use the pc at all because it says unsupported signal adjust your pc output.. i even tried removing the graphics card and running the MOBOs inbuilt GC but still same problem.....

*RAGE*!!

honestly there is no work files on there should i just wipe the disk and start over? i have a bootup disk

what the hell... works now and says no propietary drivers installed :S

---

### Post by 3602 on 2011-05-14
Did you properly run the purge command?

Try all this here:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

Purge everything, reboot. See what happens. If you get a command prompt instead of a nice GUI then you still have to do the sudo mv command.

---

### Post by ubuntienewb on 2011-05-14
right i did what the page said and it seemed to work, but i still have the old desktop setup rather than unity, also i need to do the latest drivers for the card

---

### Post by 3602 on 2011-05-14
Oh you get straight to GUI *after purging*? That's good, man. Go to Step 4. If you don't need to regenerate a xorg.conf it probably means that your first installation was incomplete.
Oh and the *-rf* flag suppresses all messages, so you don't get a "success" nor a "failure".

---

### Post by ubuntienewb on 2011-05-14
:D oh goodie i am on the right track now... what does this mean exactly?

**Step 4.**
*cd* into whatever dir you have the .run file.


does this just mean open my DL folder? (where the file is stored atm)

---

### Post by ubuntienewb on 2011-05-14
sudo sh (your installation file).run --buildpkg  Ubuntu/natty
tried it and got

sh:Can't open ati-driver-installer-11-5-x86.x86_64.run


honestly ubuntu has got to have a faster and easier way to find and install the right drivers other than this.. :S

---

### Post by kaldor on 2011-05-14
> **ubuntienewb said:**
> :D oh goodie i am on the right track now... what does this mean exactly?

**Step 4.**
*cd* into whatever dir you have the .run file.


does this just mean open my DL folder? (where the file is stored atm)

"cd" is a command. It means Change Directory. When asked to "cd" into a directory, you use that command to go to the directory you need to work with.

Example...

Your .run file is in /home/user/Downloads. use "cd Downloads" to cd into that directory. A Terminal always opens up in the user's home folder. Also, you can press Tab to autocomplete long directory/file names instead of typing it all out :)

Edit: Yeah, I've seen a surprising number of AMD and NVIDIA issues since 11.04 came out. In 7.10 to 10.10 all I had to do was Enable the driver, wait a few seconds, then reboot. No issues. They don't even show up for me on 11.04 :(

---

### Post by 3602 on 2011-05-14
Hmm... The file should be in Downloads if you got it through Firefox and didn't move it later.
In Terminal, do:
```
cd Downloads
```Now re-run the *sudo sh* command. Tip: Just type "ati" then press Tab button on your keyboard, it will automatically fill in the rest.
The file should be runnable, at least I got no problems when I was installing it... If not, do:
```
sudo chmox a+x (your file).run
```But in your case I think that you weren't in the correct directory. To make sure the file is there,
```
ls
```and you shall see the .run file in green.

EDIT: Nice kaldor! :)

---

### Post by ubuntienewb on 2011-05-14
/cry seemed to work and then said system needs to reboot... did so and after it got past BIOS screen the screen went black and stayed black:'(

---

### Post by ubuntienewb on 2011-05-14
now pc wont work at all :(

honestly if this is how hard its going to be every time there is a new driver out i may be forced to go and get W7.

---

### Post by 3602 on 2011-05-14
O...K That's not good.
Do you at least get a command prompt? Or absolutely nothing at all?

---

