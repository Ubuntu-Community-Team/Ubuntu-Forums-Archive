---
title: "Upgraded to 10.10 and Now No GUI"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by BigJohnL on 2010-10-28
I run two dual-boot ubuntu machines with XP.  Upgraded both to 10.10 and accepted all prompts for replacement, etc.  One machine seems just fine; the other (an old Dell 8100) now gives only a command-line interface when booted to ubuntu.

Is there a fix, or do I have to download 10.10 and reinstall?

Thanks in advance for the help!

---

### Post by cariboo on 2010-10-28
You have to remove the previous  graphics driver and /etc/X11/xorg.conf file, as the older  graphics driver doesn't work with the new version of Xorg, in maverick.

You'll have to let us know what graphics chipset the Dell system uses, in order for us to give you more specific instructions.

---

### Post by seventhsamurai on 2010-10-28
[deleted]

---

### Post by BigJohnL on 2010-10-28
Win Device Manager sez it is an nVidia GeForceMX 2

---

### Post by mcoleman44 on 2010-10-28
When you get to grub choose recovery mode. Drop to a root shell and type this:
```
sudo rm /etc/X11/xorg.conf
```
then type:
```
startx
```
 see if this helps

---

### Post by mcoleman44 on 2010-10-28
Ohh and once you get into the gui
check hardware drivers to see if youre driver is listed. Remove it and see if there is another driver listed that you can update

---

### Post by BigJohnL on 2010-10-28
Where would the old driver be found, and what might the filename look like?

Where would one get the replacement driver?  nVidia?  

BTW, I'm considered something of a power user in XP, but Linux seems to have a steep learning curve ...

---

### Post by mcoleman44 on 2010-10-28
After you get into the GUI in low graphics mode. Go to system < Administration < hardware drivers
I'm guessing there will be an updated driver listed there that you can activate.

---

### Post by BigJohnL on 2010-10-28
How do I get into the GUI from the command line?

Sorry to be so dumb!

---

### Post by BigJohnL on 2010-10-28
OK, i got the the low-res GUI.  Now I'll see if I can follow the remaining instructions.

---

### Post by mcoleman44 on 2010-10-28
When u first start up you will see options under grub, choose recovery mode. You will then see a list of options. Choose failsafex.

---

### Post by BigJohnL on 2010-10-28
Had the GUI, now don't.  Grub doen't recognize sudo or rm.

Thinking about just giving up on 10.10: doesn't seem to be a driver out there for my old nvidia card.

---

### Post by BigJohnL on 2010-10-28
Now can't get into GUI at all.  xinit sez "fatal server error", "Giving UJp"

Should I just give up too, and reinstall 10.10 from scratch?  Will it come with a driver that will work with this hardware?

Thanks for your patience!

---

### Post by mcoleman44 on 2010-10-28
Did you try choosing failsafex in the recovery mode menu?

---

### Post by beew on 2010-10-28
> **BigJohnL said:**
> Now can't get into GUI at all.  xinit sez "fatal server error", "Giving UJp"

Should I just give up too, and reinstall 10.10 from scratch?  Will it come with a driver that will work with this hardware?

Thanks for your patience!

What graphic card do you have?

---

