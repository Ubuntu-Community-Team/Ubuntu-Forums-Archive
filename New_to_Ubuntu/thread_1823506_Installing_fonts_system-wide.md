---
title: "Installing fonts system-wide"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by Jetro on 2011-08-12
Hiya,

Trying to install a couple of fonts in Ubuntu 10.04. I've done this according to the [Fonts section]("https://wiki.ubuntu.com/") on Ubuntu Wiki.

What I first did was placing them in ~/.fonts, but then they aren't available in Opera (or Synaptic etc.) I guess what I want is to install them system-wide.

I have done it according to ["Manually"]("https://wiki.ubuntu.com/Fonts#Manually"). I copied the fonts folders over to truetype. I just noticed now that when I open this truetype folder normally (with no rights), the folders appear, but they say they're empty, that the folders content cannot be read. So I wonder what that's about. Do I have to move every file individually? Have also done the [FONT="Courier New"]sudo fc-cache -f -v[/FONT], and rebooting.

So, yes, how do I actually make fonts available system-wide? :(

**Edit:** Oops, I actually figured out how (though, not as much as just stumbling upon it). I individually changed the rights of each font folder to be "accessible" to other users. Solved it. :)

---

### Post by ajgreeny on 2011-08-12
For future reference, all the fonts you will use in Ubuntu are stored in two places.

1.  /usr/share/fonts
2.  ~/.fonts

I recommend you install them in the #1 location as if you install them to your /home directory they will not be accessible from another account on the computer.

First make a folder to hold your custom fonts.
```
sudo mkdir /usr/share/fonts/truetype/customttf 
``` (customttf is an example.)

Next open a terminal in the folder where you have a bunch of custom fonts and type the following:```
sudo cp ./*.ttf /usr/share/fonts/truetype/customttf
```  This will copy the truetype fonts to that folder.

Now that we have the fonts in the proper folder we need to install them system-wide in Ubuntu with ```
sudo fc-cache -f -v
``` which will install the fonts so that all your applications like OpenOffice and all users can use them.

I hope this helps.

---

### Post by Jetro on 2011-08-12
Thanks. :)

I think that, specifically the second command, ought to be in the Wiki guide. Or maybe I just missed something.

---

