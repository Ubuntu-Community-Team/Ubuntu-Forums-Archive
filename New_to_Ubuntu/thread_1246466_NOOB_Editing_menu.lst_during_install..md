---
title: "NOOB: Editing menu.lst during install."
date: 2009-08-21
forum: New to Ubuntu
---

### Post by gonzoid on 2009-08-21
Installing hardy on a Sunfire 2200 and I have to edit the menu.lst file and change HD0 to SDA but I can't get any editor (that I can understand) to run so that I can edit the menu.lst file and boot up the system.

gedit, ee and aee aren't available. I can't figure out vim plus I was having terminal problems with wrapping off the top of the screen with it.

I found an 'Installation AMD64' thread at Community Ubuntu Documentation and it makes it sound so easy 'Simply open the file in your favorite editor...' Yeah.

Any pointers? I've searched for information on how to do this and am stuck and can't boot the system until I fix it. :confused:

Thanks!!

---

### Post by yabbadabbadont on 2009-08-21
nano is the editor you probably need to use.  It is available in the shell that the installation CD provides during installation.

---

### Post by egalvan on 2009-08-21
> **gonzoid said:**
> Installing hardy on a Sunfire 2200 and I have to edit the menu.lst file and change HD0 to SDA but I can't get any editor (that I can understand) to run so that I can edit the menu.lst file and boot up the system.


Any pointers? I've searched for information on how to do this and am stuck and can't boot the system until I fix it. :confused:

Thanks!!

If Hardy is already installed, then...
Boot from the Hardy LiveCD in a LiveCD session...

then use the terminal to run gedit...

---

### Post by Tclarkie on 2009-08-21
do u need to do it in the install

---

### Post by gonzoid on 2009-08-21
> **yabbadabbadont said:**
> nano is the editor you probably need to use.  It is available in the shell that the installation CD provides during installation.

I must have something wrong because I get an error 'Error opening terminal: bterm'.

---

### Post by gonzoid on 2009-08-21
> **Tclarkie said:**
> do u need to do it in the install

According to the doc that I found, yes.

I am a very newbie newbie. Lots of Windoze and mac experience but not much of anything with Ubuntu/Linux/Unix.

The doc is at [https://help.ubuntu.com/community/Installation/Amd64](https://help.ubuntu.com/community/Installation/Amd64).

If there's a better way that I can do, I'm game...

I would assume that I don't need the full path '/dev/sda' (from the doc above), right?

---

### Post by Tclarkie on 2009-08-21
after you install, go to /boot/grub/menu.lst
edit that

---

### Post by gonzoid on 2009-08-21
> **egalvan said:**
> If Hardy is already installed, then...
Boot from the Hardy LiveCD in a LiveCD session...

then use the terminal to run gedit...

What is a 'live CD'? Sorry to be so dense but I'm new at this...

I did find [http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/) and will try that as I have no problem getting back to where I am right now.

Shouldn't this be easier? But then I guess that everyone would be doing it then.

---

### Post by Tclarkie on 2009-08-22
the cd where you boot off to install

---

### Post by Liolikas on 2009-08-22
He try to install server edition so do not have live cd.


> 
I can't figure out vim plus I was having terminal problems with wrapping off the top of the screen with it.

Then try nano.

vim is not hard it just has insert mode and command mode. Basically you need to press ï (eneter inster mode) write what you want then press esc (back to command mode) when done and write ZZ (z is not Z and ZZ is command: save and exit).

---

### Post by Tclarkie on 2009-08-22
well then just use another distro live cd

---

### Post by gonzoid on 2009-08-23
I've learned a lot. The Sunfire x2200 RAID isn't a true raid system. It's 'fake raid' so I disabled it. That was complicating things a lot.

Live CD is a cool feature.

I am off to install using the instructions at this site: [http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

All this to setup a test server for some web projects but I figured that I would have to jump into Linux at some time. My first experience with Linux (Red Hat) wasn't pretty so it was with a little of fear and trepidation that I crept into Ubuntu and so far, it's been frustrating but not outside of what could potentially happen in a Windows environment after mucking with raid and such. It turns out that the Sunfire X2200 raid only works with windows (and probably Solaris). Interesting...

That doc (Installation AMD64 help.ubuntu.com/community/Installation/Amd64) sure left out a whole lot of stuff. It's hard when documentation skips over really important stuff like that. That was the link to installing Ubuntu on Sunfire that I found. If it could be enlarged to state that the NVidea raid has to be disabled before doing anything else, that might make it more useful.

Thanks all! Onward and upward!

---

### Post by Tclarkie on 2009-08-24
good on ya

---

