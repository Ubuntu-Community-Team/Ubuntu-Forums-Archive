---
title: "Big mistake! need help to reset refresh rate through Terminal please"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by scotttie on 2009-02-15
Hello everyone,
Help!!! made a big mistake , had a flickering screen and went into system altered refresh rate to 75 Htz now when starting ubuntu goes into the startup screen and after about 3 seconds goes to a black screen, I can get the terminal safe mode started OK but dont know if there is any commands to reset the refresh rate?
any help would be greatly appreciated
thanks Scottie

---

### Post by jimreynold2nd on 2009-02-15
Uhh... what kind of graphic card do you have? you might want to run that card's driver's autoconfig tools to get it back right.
OR you might want to hac... erm... edit the /etc/X11/xorg.conf file, find where the refresh rate is specified and correct it. Remember to backup anything you touch!

---

### Post by scotttie on 2009-02-15
thanks jimreynold2nd,
Could you tell me the full command line to edit the xorg.conf file please (I tried entering what you put in the reply but it cant see it! i think something missinfg off front end maybe?
thanks

---

### Post by Dr Small on 2009-02-15
Try:
```
sudo nano /etc/X11/xorg.conf
```

Or, if you know Vim, you can use it instead of nano

---

### Post by kansasnoob on 2009-02-15
> **scotttie said:**
> Hello everyone,
Help!!! made a big mistake , had a flickering screen and went into system altered refresh rate to 75 Htz now when starting ubuntu goes into the startup screen and after about 3 seconds goes to a black screen, I can get the terminal safe mode started OK but dont know if there is any commands to reset the refresh rate?
any help would be greatly appreciated
thanks Scottie

Since you can get to terminal run:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Also please tell us what version of Ubuntu you're running. Xorg changed a bunch in Intrepid so some of the old tricks don't work anymore.

---

### Post by scotttie on 2009-02-15
Tried editing file but file appears to be empty? nothing showing at all, also tried other command line to reconfigure and it says its overwriting configuration and gives a number then returns to the prompt. 
I am running Ubuntu 8.10 with all updates (disc off computeractive mag, all fine till I altered refresh rate).
thanks

---

### Post by scotttie on 2009-02-15
bump

---

### Post by kansasnoob on 2009-02-15
OK, I think you need to restart and enter the boot menu. Now, if you're dual-booting you should always see the boot menu, if not then right after your machines BIOS prompts (Usually a graphic like Dell/HP/PC1 pass you have 3 seconds to hit ESC on the keyboard which should bring you to a boot screen that includes booting the various kernels available and recovery mode for each kernel along with one to test memory.

I'd choose recovery mode for the newest kernel (the one at the top of the list) and let recovery mode run. When it's done running you'll be presented with a few choices. Choose to reconfigure X or something along those lines. Sorry I can't remember just how it's worded, but I know there's one to repair broken packages, another to reconfigure X (or something like that), or to simply boot.

Look here:

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by mutineer612 on 2009-02-15
> **kansasnoob said:**
> Since you can get to terminal run:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Also please tell us what version of Ubuntu you're running. Xorg changed a bunch in Intrepid so some of the old tricks don't work anymore.


I recently experienced a similar issue with max resolution and refresh rate not being detected after installing U8.10 x64.  Running ```
sudo dpkg-reconfigure xserver-xorg
``` command and follownig the prompts reconfigured xserver and everything is working properly.  With ubuntu 8.10 is the xorg.conf file is no longer used?

---

### Post by sisco311 on 2009-02-15
How did you change the refresh rate?

Can you log in using "failsafe GNOME"?

---

### Post by mikewhatever on 2009-02-15
You didn't specify the refresh rate you wanted, so let's say it is 60.
```
xrandr -r 60
```

Edit: Not really sure it will work in recovery mode, still wouldn't hurt to try.

---

### Post by kansasnoob on 2009-02-15
> **mutineer612 said:**
> I recently experienced a similar issue with max resolution and refresh rate not being detected after installing U8.10 x64.  Running ```
sudo dpkg-reconfigure xserver-xorg
``` command and follownig the prompts reconfigured xserver and everything is working properly.  With ubuntu 8.10 is the xorg.conf file is no longer used?

The only difference between our suggested commands is the "-phigh" which means "priority high".

---

### Post by scotttie on 2009-02-15
Thanks everyone,
Unfortunatly nothing seems to work so I have now reloaded the whole issue seems OK now but I have to reset all the previous changes I had made, but what the heck! it's what its all about (isn't it?)
Thanks All
Scottie

---

