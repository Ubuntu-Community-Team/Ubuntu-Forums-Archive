---
title: "gdebi is nowhere....."
date: 2009-05-15
forum: New to Ubuntu
---

### Post by medicalystoned on 2009-05-15
i installed gdebi from terminal, synaptic shows it as installed, but i don't know how to use it..... any help would be great... i have a bunch of downloads that are .deb that i would like to install...... thank you in advance for the help...... peace

---

### Post by DirtDawg on 2009-05-15
> **medicalystoned said:**
> i installed gdebi from terminal, synaptic shows it as installed, but i don't know how to use it..... any help would be great... i have a bunch of downloads that are .deb that i would like to install...... thank you in advance for the help...... peace

If you have .deb packages, simply double-click to install them. You will be prompted for your password.

---

### Post by TransitMan on 2009-05-15
Just click on the .deb files and gdebi will automatically start the install process for you, after you put in your password.

---

### Post by medicalystoned on 2009-05-15
when i double click another window pops up asking me to choose an application and no choices make sense, when i click choose it opens another window that shows my desktop, a floppy drive,file system, and recently used.
 what now?

---

### Post by TransitMan on 2009-05-15
Did you install gdebi-kde?

---

### Post by DirtDawg on 2009-05-15
> **medicalystoned said:**
> when i double click another window pops up asking me to choose an application and no choices make sense, when i click choose it opens another window that shows my desktop, a floppy drive,file system, and recently used.
 what now?

It sounds like the package you're trying to install may be corrupted. If double-clicking isn't working, try right-clicking the package. The first option should be "open with Gdebi package installer." If it's not, there may be a problem with the package. Make sure the name is correct (with a ".deb" extension."

If it doesn't work, and it's nothing too personal, if you let us know what you're trying to install, it may be easier for us to help. In addition, if you haven't already, remember to check the repositories for packages before trying to install debs. This can be activated in the Applications menu under "Add/Remove..."

EDIT: Sorry, didn't realize you're using Kubuntu. To install programs, go to the K-menu and look for Add/Remove.

---

### Post by DirtDawg on 2009-05-15
> **TransitMan said:**
> Did you install gdebi-kde?

In Ubuntu gdebi is installed by default. Is this not the case with Kubuntu and gdebi-kde? I honestly have no idea.

---

### Post by medicalystoned on 2009-05-15
g-debi kde is installed according to synaptic, iam really just trying to install skype first of all, the others are no biggie, but the wife needs her skype in bed to chat with her buddy........ thanks again for all the help everyone

---

### Post by kpkeerthi on 2009-05-15
> **medicalystoned said:**
> when i double click another window pops up asking me to choose an application

Enter **/usr/bin/gdebi-gtk** for command in that popup window. You can even right click on a deb file, select Properties -> Open With -> Command -> **/usr/bin/gdebi-gtk**

---

### Post by DirtDawg on 2009-05-15
> **medicalystoned said:**
> g-debi kde is installed according to synaptic, iam really just trying to install skype first of all, the others are no biggie, but the wife needs her skype in bed to chat with her buddy........ thanks again for all the help everyone

EDIT: Try kpkeerthi's suggested solution first. If that works, yay!

I always have time to help a fellow Oregonian who appreciates the *ahem* greenery of our fine state.

Anyways, I'll assume that right-clicking did not have the desired effect? If that's the case, let's try installing with a command line. This will hopefully produce an error message that might tell us what's up.

I'll assume your .deb package is on your desktop. This command installs deb packages the old fashioned way. Of course, replace "PACKAGE.deb" with the actual package name (ie skype.deb):
```
sudo dpkg -i ~/Desktop/PACKAGE.deb
```

Assuming something is wrong, you'll get some error messages. Please post them here and we'll see if we can't get to the bottom of this.

---

### Post by medicalystoned on 2009-05-15
ok, i re- installed gdebi kde and all 3 gdebi thins in synaptic

when i try to downlod skype a window pops up asking if i would like to save that file, i click save, a window with a list of .deb files i have saved and 2 .tar.gz files is there, including the skype i want to install, i double click skype and another window pops up, a launch application window, it states that this link needs to be opened with an application, it has a list that contains only skype and then a choose option, that takes me to another window with my desktop, files sytems, etc.
I am so lost........... thank you all again for the help and the patients...

---

### Post by Jazzy_Jeff on 2009-05-15
It is not that you are lost, something is not working right. Are you sure you are downloading the Ubuntu installer for skype?

---

### Post by medicalystoned on 2009-05-15
danny@cannabis:~$ sudo dpkg -i ~/desktop/skype-debian_2.0.0.72-1_i386.deb
[sudo] password for danny:
dpkg: error processing /home/danny/desktop/skype-debian_2.0.0.72-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/danny/desktop/skype-debian_2.0.0.72-1_i386.deb


i hope i posted this correctly...... thanks   hope it helps you help me

---

### Post by Jazzy_Jeff on 2009-05-15
I don't know if this will help or not but have you restarted your computer? From time to time when something doesn't work right I restart and it starts working.

---

### Post by medicalystoned on 2009-05-15
> **Jazzy_Jeff said:**
> It is not that you are lost, something is not working right. Are you sure you are downloading the Ubuntu installer for skype?

not sure of what i am doing now.....i chose skype for ubuntu...it worked before on my other ubuntu machine but i did a re-install and never tried it again.

i totally did re-start...i too have found that to be ths simplest fix sometimes........not so lucky here

---

### Post by Jazzy_Jeff on 2009-05-15
Sorry I couldn't be more help. I have never used Kubuntu so maybe someone else will be able to help.

---

### Post by medicalystoned on 2009-05-15
> **Jazzy_Jeff said:**
> Sorry I couldn't be more help. I have never used Kubuntu so maybe someone else will be able to help.

Thank you so much anyhow for taking the time......this is the kind of stuff that makes me LOVE ubuntu...the community...thanks again---- peace

---

### Post by DirtDawg on 2009-05-15
> **medicalystoned said:**
> ok, i re- installed gdebi kde and all 3 gdebi thins in synaptic



when i try to downlod skype a window pops up asking if i would like to save that file, i click save, a window with a list of .deb files i have saved and 2 .tar.gz files is there, including the skype i want to install, i double click skype and another window pops up, a launch application window, it states that this link needs to be opened with an application, it has a list that contains only skype and then a choose option, that takes me to another window with my desktop, files sytems, etc.
I am so lost........... thank you all again for the help and the patients...

EDIT: Sounds like you have used Ubuntu before, so most of this is probably waaaaaay obvious. Sorry about that. You can never tell how much experience someone has. Try installing it from the command line with the 'dpkg -i PACKAGE.deb' command and post the errors here. That will help lots I think.

EDIT2: HA! You already did. Missed that.

Okay, it's a little tough to figure out what's happening, so forgive me if some of this is obvious.

When you go to the skype website, make sure you go to the Download link and click the Ubuntu option. Firefox will open a seperate window and choose the 'Save File' option. If another window opens upon clicking the 'Save File' option, this window is for choosing where to save the file. If not, then the file has most likely been downloaded onto your desktop.

Okay, so assuming you downloaded the .deb file and it's sitting on your desktop, time to install. Double-click the .deb file. If it does not install, and it sounds like it won't, right-click the package and choose "Open with Other Application." A new window will pop up with a list of options. If gdebi is not on this list, look to the bottom of the window where you will see an option for "use custom command". Click on the little arrow there and enter "/usr/bin/gdebi-gtk" into that box (without quotes). 

Now if that doesn't work, there's something going on with the deb. I downloaded Skype from their website and I didn't get any tar.gz files or anything like that, so I'm not clear what's going on there. Really, if the .deb is good, you should just be able to doubl-click the thing and go.

---

### Post by hysteresis on 2009-05-15
I installed skype using the medibuntu repositories:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by DirtDawg on 2009-05-15
> **medicalystoned said:**
> danny@cannabis:~$ sudo dpkg -i ~/desktop/skype-debian_2.0.0.72-1_i386.deb
[sudo] password for danny:
dpkg: error processing /home/danny/desktop/skype-debian_2.0.0.72-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/danny/desktop/skype-debian_2.0.0.72-1_i386.deb


i hope i posted this correctly...... thanks   hope it helps you help me

Is the package on your desktop? If it's not, move it there and try again with the same command.

EDIT: Actually I think I see the problem, it should be: sudo dpkg -i ~/Desktop/skype-debian_2.0.0.72-1_i386.deb
(Desktop needs a capital 'D')

---

### Post by Jazzy_Jeff on 2009-05-15
Adding the medibuntu repositories might be just what you need.

---

### Post by medicalystoned on 2009-05-15
SOLVED you guys all rock............ I am learning more and more daily....... and I am getting addicted to ubuntu.... THANK YOU ALL..... 

--------------- apt-get install PEACE   (if it was just that easy)

---

### Post by DirtDawg on 2009-05-15
> **Jazzy_Jeff said:**
> Adding the medibuntu repositories might be just what you need.

For Skype that will work, but that won't help next time they need to install a deb package.

---

### Post by medicalystoned on 2009-05-15
> **Jazzy_Jeff said:**
> Adding the medibuntu repositories might be just what you need.

what does mediubuntu have that i don't?


how do i mark this as solved?

---

### Post by DirtDawg on 2009-05-15
> **medicalystoned said:**
> SOLVED you guys all rock............ I am learning more and more daily....... and I am getting addicted to ubuntu.... THANK YOU ALL..... 

--------------- apt-get install PEACE   (if it was just that easy)

Glad to hear it! Will you please consider posting the solution for anyone who may be browsing the forums in the future to solve a similar problem?

---

### Post by DirtDawg on 2009-05-15
> **medicalystoned said:**
> how do i mark this as solved?

Check 'thread tools' in red on the upper-right. I think it's in there.

---

### Post by alexandari on 2009-05-15
baah gdebi NEVER installed a single package of mine without giving me an error since kde 4.1 was out. dpkg -i is the only thing that saves me xD

---

### Post by medicalystoned on 2009-05-15
> **DirtDawg said:**
> EDIT: Sounds like you have used Ubuntu before, so most of this is probably waaaaaay obvious. Sorry about that. You can never tell how much experience someone has..

Okay, so assuming you downloaded the .deb file and it's sitting on your desktop, time to install. Double-click the .deb file. If it does not install, and it sounds like it won't, right-click the package and choose "Open with Other Application." A new window will pop up with a list of options. If gdebi is not on this list, look to the bottom of the window where you will see an option for "use custom command". Click on the little arrow there and enter "/usr/bin/gdebi-gtk" into that box (without quotes). 



first, i have very little ubuntu experience, i mean i use it to browse the web, myspace and e-mail, but since ubuntu  has been in my life i have this constant craving to learn more about it, i try to do as mush from terminal as i can, just to learn

second, this was the solution to my problem.............thank you all again for the help----- peace

---

### Post by DirtDawg on 2009-05-15
> **alexandari said:**
> baah gdebi NEVER installed a single package of mine without giving me an error since kde 4.1 was out. dpkg -i is the only thing that saves me xD

Well that sucks. That has to make it hard for new users to make the transition.

Glad to be of help, medically.

---

