---
title: "stuck in command prompt"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by wiredone on 2009-11-07
i ugraded to ubuntu 9.01 all was well.rebooted. now i am left at command prompt.after passwords are entered, i have the $ sign ready for commands as in terminal.how do i restore the graghical on boot up. i played around with some permissions while attempting to mount a second internal hard drive. after giving up i removed it. single drive now has 8.05 sise by side with the 9.01 as dual boot. how do i get into 9.01. usplash error and authority.x came up. any ideas?

---

### Post by ikt on 2009-11-07
if you type,

```
startx
```

does anything happen?

The errors that you get try to document and post here, as they help solve the issue :)

---

### Post by wiredone on 2009-11-07
xauth:error in locking authority file/home/myname/.Xauthority

---

### Post by chazn85 on 2009-11-07
Have you tried loading as root?  what graphics drivers are you using?

---

### Post by corncob on 2009-11-07
If you hit [ctrl][alt][F7] all at once, does anything happen?

---

### Post by wiredone on 2009-11-07
i can log on as root but all of the forum commands that i've read fail , some as user some as root

---

### Post by wiredone on 2009-11-07
nothing..its as if i'm stuck in terminal mode

---

### Post by wiredone on 2009-11-07
i don't know the graghics drivers off hand but durring the boot corrections were made for resolution ..i can switch to root..im stuck in terminal mode..do you know how to go to the graphics mode

---

### Post by LewRockwell on 2009-11-07
intel video?

you do know 9.10 blew that up

.

---

### Post by corncob on 2009-11-08
You do see the grub boot menu at startup?  Just wondering if somehow you could be booting into recovery mode?  For want of much else to say, you could try
```
xinit
```
although I think its the same thing as startx.
At the boot menu, is there another Linux kernel you could select?
There seems to be some rough edges on my upgrade too and I'm considering saving my home folder to a pen drive or something and doing a fresh install.  That way I'd get the ext4 format too.  You could use the live CD to save your home folder.

---

### Post by wiredone on 2009-11-09
i did a fresh install of 9.04 then verified updates for 9.04. i then upgraded to 9.10 but this time i selected over write the existing configurations. it worked perfectly but failed to recognize the mounting the cd rom-rw and kept looking for a floppy. i did the reboot as sugested in ubuntu notes prior to the first reboot of 9.10.i killed floppy in the bios then unplugged and rechecked boot order for cd then hd. the system booted a couple of times sucessfully then crashed again with usplash problem. that happened after sucessfully going on line several times.it seems to alter the bios settings for floppy again after rebooting. i trashed 9.10 and went back to 9.04 - all systems work perfectly again. im not convinced that i can do repairs to 9.10. all of you sharp guys will have to tweek it while this small time key puncher waits awhile for the fixed version. i tried startx xstart and several other commands from the forums without success. 
):P

---

