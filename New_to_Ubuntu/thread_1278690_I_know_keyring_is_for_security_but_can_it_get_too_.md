---
title: "I know keyring is for security but can it get too annoying?"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by mjp29 on 2009-09-29
I know that Ubuntu, unlike Windows, is built for security.  After all, Unix itself was designed (back in the 1960's I believe) for security.

However, it appears to me that the keyring on both my Ubuntu computers ask for a password a little too often.

I would prefer that the keyring or operating system only ask for a keyring password when I am doing something like installing software.  However, my keyring seems to pop up on boot from time to time (I chose to not require an administrative password upon booting) and the keyring often pops up (asking for a password) when I open programs like Evolution email (and other programs and so forth).

I never had MS Windows at home.  I used Mac OS X (my old G4 Cube PowerPC is getting way too slow and dated now and I like Ubuntu).  But I do like how the Mac os X only seems to ask for an administrative password for things like installing software.  I understand some Vista users complain that their computers are constantly bugging them for a password.

Is there a way to not use a keyring or only make keyring or Ubuntu operating system ask for a password when doing something of critical security sensitive (like installing new software and such).

---

### Post by lindsay7 on 2009-09-29
Click on Applications/Password and then click on the passwords tab. Right click on password and choose change password, put in your old password and do not enter anything new, then just save and back out of this menu.

See this for more,

[http://ubuntuforums.org/showthread.php?t=1141508](http://ubuntuforums.org/showthread.php?t=1141508)

---

### Post by mjp29 on 2009-09-29
> **lindsay7 said:**
> Click on Applications/Password and then click on the passwords tab. Right click on password and choose change password, put in your old password and do not enter anything new, then just save and back out of this menu.

See this for more,

[http://ubuntuforums.org/showthread.php?t=1141508](http://ubuntuforums.org/showthread.php?t=1141508)

Thanks, for future readers one should probably click on Applications/Accessories/Passwords and Encryption keys

right?

My only question (problem) with having no password to be asked is this -> If I do the method you suggest will Ubuntu thus never ask for a password even when new software is installed - ? - I suspect so.

So, if true, I would suggest that somehow Ubuntu be coded so that atleast one could use a password (keyring, administration password, whatever) when atleast choosing to install new software (like on Mac os X) - not that Mac os X should be used as any standard (but Mac X being much much better than MS os systems if you know what I mean! lol).

But I thank you so much for your reply and I indeed did what you suggested - as I just think keyring has been bugging me to death.  Shucks, I have Ubuntu on my 4 year old daughters computer and it is asking her for passwords when she is trying to play an online preschool Dora game - haha

---

### Post by lindsay7 on 2009-09-29
The change I gave you is for the keyring only.  You still will need to enter your password for everything else just as before.

---

### Post by random turnip on 2009-09-30
The password is there for a reason.
I'm windows one of the biggest security problems is that when installing something you've downloaded it will just say "is it safe to continue" or something like that, and 99% of people just click ok without even looking or thinking about it after using Windows for a while.  At least with a password you actually have to think "hang on, am i meant to be installing something?...".

Anyway, the chances of it actually making a difference and something happening to your computer are really really slim.  Just makes it easier for one of your freinds who wants to play around with Ubuntu to change something they don't understand, i think that's half the point behind it.

---

### Post by theozzlives on 2009-09-30
The only time I get asked for a "keyring" password is when I boot without logon and my wireless kicks in.

---

### Post by Peter09 on 2009-09-30
If you are getting asked for a password to access your wifi make sure the shared box is ticked in the network manager applet configuration for the interface.

---

### Post by mjp29 on 2009-09-30
if i click this shared box for my wifi, that won't be sharing my wifi with the neighbors will it  (the wifi is password protected for just my use)

---

### Post by mjp29 on 2009-09-30
> **lindsay7 said:**
> The change I gave you is for the keyring only.  You still will need to enter your password for everything else just as before.

great!  thanks!

---

### Post by Peter09 on 2009-09-30
If you click the shared box it means that all users on the computer can use the connection - nothing to do with your neighbour. This means that network manager does not need to ask for your password to validate you.

---

### Post by mjp29 on 2009-10-12
> **random turnip said:**
> The password is there for a reason.
I'm windows one of the biggest security problems is that when installing something you've downloaded it will just say "is it safe to continue" or something like that, and 99% of people just click ok without even looking or thinking about it after using Windows for a while.  At least with a password you actually have to think "hang on, am i meant to be installing something?...".

Anyway, the chances of it actually making a difference and something happening to your computer are really really slim.  Just makes it easier for one of your freinds who wants to play around with Ubuntu to change something they don't understand, i think that's half the point behind it.

For myself, I'm satisfied with disabling the keyring (by not having any password in it) where it no longer bugs me.  The other poster is right in that disabling the keyring password then one *still* has to enter a password when installing new items.

---

