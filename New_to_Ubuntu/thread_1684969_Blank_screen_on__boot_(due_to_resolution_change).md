---
title: "Blank screen on  boot (due to resolution change?)"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by allmightymoo on 2011-02-09
**[COLOR=Red]I Realize this is long but i need help and thought i'd be specific! Thanks![/COLOR]**
[B]
[/B]
**My Computer:**

[LIST]
[*]HP Pavilion Entertainment PC (dv5 i      believe)        
[*]Dual booting Win7 x64 (upgrade from win vista x64) and      Ubuntu 10.04 
[*]Graphics Card: ATI Radeon HD 3200
[*]RAM: 4GB        
[/LIST]
  ** My problem:**
    After selecting Ubuntu from the GRUB menu, I see the little blinking white cursor (or underscore) in the top left area of my screen that i usually see when Ubuntu is booting. Then some small amount of text flashes at the top of the screen (too fast to read) **then the screen goes blank, as in  no text or anything is on the screen, the screen is still on though.** It seems to stay that way indefinitely although i have never waited for more than 5 minutes. **So** **Ubuntu does not boot at all, screen stays blank.**

[B]What I did:
[/B]The reason this is happening is because i did this:
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)
  (Its basically a tutorial on how to improve the resolution of the boot screen logo thing)

I believe that the problem is that i changed the res of my boot screen to 1280x1024 (as indicated in step 3 of the tutorial) but I’m thinking that my computer screen is not that resolution (Win7 says recommended res is 1280x800) and maybe as a result the boot screen does not load.  (this is just a guess from my limited knowledge of ubuntu)
   
  **My question:**
  What do you think? 
  Is there a way to change the resolution back?
              (Win7 says my recommended screen res is 1280x800) 
  Or can I just undo everything I did? 
              (Like “restore” my system to an earlier point w/o completely reinstalling)
   
  Basically how can I fix this problem?!?!?!?!? (w/o reinstalling)
   
  **Note:**
  I’m somewhat knowledgeable w/  computers and ubuntu but I’m no expert so if you could be specific in your answer I would really appreciate it! :p


Thanks in advance!!!

---

### Post by robsoles on 2011-02-12
Boot from LiveCD, check under places for your installed file-system and select it out of places to mount it.

Open terminal and type```
gksudo nautilus
```Now you have a 'rooted' file-browser, please be careful with it.

Using the file-browser that opened navigate to /media/<insert-uuid-or-similar-here>/etc/default and right click 'grub', choose open with gedit and change the line corresponding with the following to match the following:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap"
```close everything and reboot. (Note but: I have taken the line given in the article you linked to and changed it to the apparent recommended for your display...)

Any good?

---

### Post by allmightymoo on 2011-02-15
Did everything you said...no change

Thanks anyway...any other ideas?

somebody said i should try this >> [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by robsoles on 2011-02-15
Sorry, forgot to mention: ```
sudo update-grub
```is required to make the changes to that file go into effect.


If it still won't boot after that then consider resetting the file to vanilla, here is a sample from my system - don't completely copy this file over your own, may not be super. Just reset the line (or any others) that you've touched to match this copy's simile```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Update grub and reboot again - if that fails it will probably be best to follow the advice at the link you have provided, otherwise if it works then consider trying stuff with the "#GRUB_GFXMODE=640x480" line, just remove the '#' and that makes the line active, try it at 640x480 first and if that works it's worth trying 1280x800 at that point.

Any good now?

---

