---
title: "Cannot get Ubuntu to work on my system"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Michael1122 on 2009-04-17
I have downloaded the Umbuntu software twice and each time I try and put it on my computer it copies all the files, I take the disk out, reboot and it never comes up.

I also cannot get back to my windows for some reason, do I need to try and download again?

---

### Post by VotaVader on 2009-04-18
What is it that you want to do? Do you want to replace Windows with Ubuntu, double boot from hard drive, or boot Ubuntu from a live CD?
Can you explain step by step what you're doing to install, and the responses you're getting from the machine?

---

### Post by Michael1122 on 2009-04-18
I am trying to replace windows on my computer.  I went to the download, downloaded the software onto a CD.  I put the CD in and started going through the process.  It asked me if I wanted to do a partition and I chose that option.  It came back adn said partition would not work go back or continue.  I hit continue and continue again and it downloaded the software on my system.  When it was finished, I rebooted with the CD out and the last thing I see is Checking Battery (OK), that's it then it just stops.

Now I cannot get back to windows so I am guessing that I killed windows somehow in the process.

I downloaded it again on another computer, put the disk in installed it and the same thing happens.  Tried to just run it from the disk and not install and nothing comes up.

I do not know if it did not get all the program needed or if the system just does not work on my computer.  I ordered the Kumbuntu DVD today to see if that wioll work once I get it.

---

### Post by bodhi.zazen on 2009-04-18
What are you doing with the files ?

You need to burn the iso to disk.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Then boot you computer, it should boot to cd. If it does not, is your bios set to boot the CD ?

---

### Post by Michael1122 on 2009-04-18
I booted to CD.  Then I downloaded the CD from the Ubuntu page. After installation, I took the CD out per the instructions, and it rebooted my computer.  That is when it booted to Check battery and that is where I get nothing.

---

### Post by VotaVader on 2009-04-18
But you can't have booted to the CD if you hadn't downloaded the CD... I don't get it.
You should download the ISO image, burn the image on a CD, reboot the computer with the CD inside (making sure it boots to CD, and not the regular OS), then follow the installation instructions. When it's finished, take out the CD and reboot.
Now, if the partitioning failed during the installation, then you have to go back and do this again. Make sure the hard drive partition is formatted during the installation, although I think by default it is.

Also make sure you don't boot into "Live CD", because that will just load the OS on RAM and not install it. You have to chose the installation to hard drive option.

---

### Post by Michael1122 on 2009-04-18
O.K. after I have it on the CD I am at the window that says try it, install Ubuntu, check for defects, test memory, and boot from first hard drive.

I choose Install, correct? and then I go through the 7 ssteps of the installation, correct?  As you can see I am a novice at this, sorry.

---

### Post by VotaVader on 2009-04-18
Yes. That's correct. At some point it will ask you on which partition of the hard drive you want to install. If you just want Ubuntu, you can just erase all the existing partitions, and create a new one (and formatting it). I don't remember so well, but I think if you choose the automatic partitioning, it will do this for you, and just use the whole hard drive for Ubuntu.

---

### Post by Michael1122 on 2009-04-18
I am trying to reload this thing again.  When I get to Prepare disk space it says before dev/sdal1 98% dev/sda5 1%.  I now clicked on guided resize scsI1. 96% Ubuntu and it is trying to resize the partition. 

Does this make sense in what it should be doing.  The first time I loaded it and it came back with a can't resize partition I beleive the Guided - use enter disk was checked and I clicked forward.  That is where I think I erased all of Windows.  But after I finished the 7 steps it ejected my Live CD and then rebooted.  That is where it came to a point and then stopped.

---

### Post by Mulenmar on 2009-04-18
Sounds to me like it's trying to resize the Windows partition instead of removing it.

---

### Post by Michael1122 on 2009-04-18
I just went through the partition and it told me there was nothing to partition.  I think windows is dead, not a bad thing. I am hoping that now when I am done reloading it will reboot properly.  Am I doing anything wrong once I take the CD out of the machine and it reboots.  i just sit there and wait but nothing seems to happen.

---

### Post by VotaVader on 2009-04-18
> **Michael1122 said:**
> I am trying to reload this thing again.  When I get to Prepare disk space it says before dev/sdal1 98% dev/sda5 1%.  I now clicked on guided resize scsI1. 96% Ubuntu and it is trying to resize the partition. 

Does this make sense in what it should be doing.  The first time I loaded it and it came back with a can't resize partition I beleive the Guided - use enter disk was checked and I clicked forward.  That is where I think I erased all of Windows.  But after I finished the 7 steps it ejected my Live CD and then rebooted.  That is where it came to a point and then stopped.

Ok, that should be fine. I guess it did partition in the first install. There must have been another error in the process. The thing is you'll have to have one partition that contains the file system (I think that when you choose a partition, you can select what it's being assigned to. Select /). Then another small partition (not more than 4GB) should be chosen as swap space. So a 98% partition and a 1% partition sounds about right. Just make it format the partitions again when reinstalling because there might have been an error there the first time.

---

### Post by Michael1122 on 2009-04-18
I am now rebooting and I get the Loading App Armor profiles, the GNOME, System tools, etc.  it gets down to checking battery state and it seems to just stop.

Does it take a really long time to boot up the system?

---

### Post by quickk on 2009-04-18
Are you sure that it actually reboots?  

When installing ubuntu, I had to manually turn the computer off and then back on after it told me to remove the cd.  It's supposed to automatically reboot, but in my case it doesn't.

If you just want to install ubuntu and don't care about what's on your disk, here are your steps:

1. Boot from the cd.  You then get the options you described (try it, install Ubuntu, check for defects, test memory, and boot from first hard drive).

2. Choose "install Ubuntu"

3. When it asks about partitioning, just accept the defaults (this should be "use entire disk").  This will DELETE everything on your drive, so make sure that this is what you want.

4. When it says to remove the disk, do so.  If it does not automatically reboot, manually power the computer on and off.

It should then boot into Ubuntu.

---

### Post by quickk on 2009-04-18
Ok, I just saw your reply.  

It's possible that there's some graphical resolution problem that prevents you from seeing anything that's on the screen.

What kind of screen do you have.  I have two 17" lcd screens with 1280x1024 pixels and I always have to change the boot parameters for ubuntu to work.

---

### Post by Michael1122 on 2009-04-18
O.K. now I am to were I logged in and put in my password.  It gave me stuff about absolutely no warrenty and then it saya "to run a command as administrator (user"root"), use "sudo (command) 
See "man sudo_root" for details

michael@michael-desktop: $

Now what do I do?

---

### Post by Michael1122 on 2009-04-18
I have one 17" monitor regular resolution.  I am not sure why after I put my password in I get some weird thing that says michael@michael-desktop: then some weird sign then the dollar sign. after that I get a prompt.  Am I suppose to type something else in?

---

### Post by Michael1122 on 2009-04-18
My mionitor is set at 720 x 400

---

### Post by quickk on 2009-04-18
In my case, this is what I need to do:  

1. Reboot, and at very start when it says press "ESC" from GRUB menu, do so.

2. You then will see a couple of boot options.  You can use your arrow keys to move up and down to select the different ones.  Highlight the regular boot option (not the safe-mode or memory test).  

I'm not at home so I don't remember what they are exactly.  I think it is the second one.  Don't press enter yet. 

3. Press "e" to edit the line (you'll see the various options that are open to you at the bottom of the screen. "e" is for edit, "b" is for boot, etc).

4. There's going to be a long line of stuff that you don't need to understand.  Move the cursor to the very end and add 

vga=795

This will select a resolution of 1280x1024.  Other possibilities are described here: [http://spblinux.de/2.0/grub.htm]("http://spblinux.de/2.0/grub.htm")

For example vga=792 for 1024x768, or vga=ask.


5. Once you added the vga=... press enter, and then press "b" to boot.


Hope this helps.

---

### Post by quickk on 2009-04-18
Hmmm...

After you entered your password, try typing "startx".  What happens?

---

### Post by quickk on 2009-04-18
> **Michael1122 said:**
> My mionitor is set at 720 x 400

Are you sure?  This is very weird.  Usually 17" LCD monitors have a resolution of 1280x1024.

---

### Post by Michael1122 on 2009-04-18
when you are editing does the vga= go in the first line or on the last line or does it matter?

---

### Post by quickk on 2009-04-18
Here's a very good review on how to change the bootup resolution:

[http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters]("http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters")

---

### Post by quickk on 2009-04-18
It should be at the end of all the other options.  It doesn't actually matter, but it's easiest not to make mistakes that way.  


The best way is just press the "end" key on your keyboard which brings you to the end of the line.  Then add vga=795, press enter and then "b" to boot.

Just to be sure, the line that you are editing should look something like: 

kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda5 ro quiet splash

After you add the vga=795 it is:

kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda5 ro quiet splash vga=795

---

### Post by VotaVader on 2009-04-18
Yeah. The thing is it seems your X server (the program that runs the graphical interface of Ubuntu) isn't starting up with the OS for some reason, so you get the Terminal interface (sort of like starting to DOS in the old Windows). I don't know why this could happen (I'm fairly new to Linux). Maybe it's one of the problems the others mentioned, but you should be able to start the GUI with the "sudo X" or "sudo startx" commands, and entering your password.

---

### Post by Michael1122 on 2009-04-18
Wow.  I think I am over my head on this.  I got to the menu1st file but I cannot find anything on that.  I do not know if I got there to late or what.

Will the DVD help me at all get past this?  I get to this field that says michael@michael-desktop but I do not know what to input at that time.  Got any ideas?

---

### Post by Michael1122 on 2009-04-18
The only way that I can get to my password and ID is to go through the recovery menu and then enter at resume.  Does this seem right?

I tried the vga=795 and all it did was make the type really small and then it just stopped again.

I tried the sudo x thing and I got a grey screen that looked like patchwork.

---

### Post by quickk on 2009-04-18
The DVD version will have the same problem.  Usually you don't have to go through this and it just works, but you are lucky I guess ;)

I'm guessing that you did not manage to change the resolution in the grub boot menu.  

If you get to something that says michael@michael-desktop, that means ubuntu is loaded, but the nice graphical desktop that you want has a problem and won't start.  It's like you are stuck in DOS mode.

You can still do lots from here, like edit the menu.lst file.  

First backup your file:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

To edit it, at the command prompt (the michael@michael-desktop line), type:

```
sudo nano /boot/grub/menu.lst
```

nano is a command line text editor.  If that does not work, nano is not installed and you can install it by typing:

```
sudo apt-get install nano
```

The menu.lst file has lots of stuff in it.  Everything with a "#" in front is commented out and does not affect anything.  For example, you could add a line like

```
#This code does nothing
```

and it would not have an effect.

Near the end of the file you should see uncommented lines.  One of them will look like:

```
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda5 ro quiet splash
```

It won't be exactly the same, but it will end with the "splash" option (I think!).

At the end of this line, add the vga=795 option.  Save the file.  You do so by pressing the CONTROL key and the letter "o" at the same time (at the bottom of the nano screen you can see the different options.  ^ = the control key).  It will ask for a file name.  Just press enter to overwrite the current file.  

Once this is saved, reboot your computer.  You can type "sudo reboot" to do so or just press the reset button on your computer.

Once your computer reboots, everything should work properly!

---

### Post by Michael1122 on 2009-04-18
Thanks Voto Vader

I did the sudo startx and it came up.  unbeleivable.  Last question.  Do I have to do this everytime I get on this computer?

---

### Post by quickk on 2009-04-18
problem solved I guess. I'm not sure why you have to type sudo start x...

---

### Post by Michael1122 on 2009-04-18
O.K.  I got it up and running but I cannot get on the internet.  Ahhhh.  Any suggestions.  It told me that I was offline so I put myself on-line and nothing comes up

---

