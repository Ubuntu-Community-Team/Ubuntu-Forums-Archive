---
title: "Accidentally removed critical packages"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by JcZndeR on 2010-03-09
Hi,

I am running Karmic Ubuntu, and for some reason my language packages/ibus weren't working.. it said it was missing something
So in trying to fix things, I removed python-apt intending to reinstall it overlooking that it would remove other really important things as well
Now, my graphical interface (gdm?) does not get past the login screen and I have no internet, as well as a lot of other packages...
I have a 9.10 disk, so I believe i can install packages off of that?
My main problem is that I need to restore graphics and internet so i can fix everything else..
I believe I need to install ubuntu-desktop? If someone could walk me through how to install that in karmic offline from the command line, I would be very appreciative
I, obviously, would really dislike reinstalling, but if I have to..
haha, this has been really stupid :redface:

thank you

---

### Post by fivex on 2010-03-09
Log into a failsafe terminal
Now you need to add your cd as a respiratory. The command is(I believe, I might be wrong)
sudo apt-cdrom add

Now insert your ubuntu cd and type
sudo apt-get install ubuntu-desktop
That *should* work.

---

### Post by JcZndeR on 2010-03-09
I tried it, unfortunately that package was not found.
Does the CD not include ubuntu-desktop?
or should I install another package
or perhaps im not mounting the disk correctly..
seems right to me

---

### Post by fivex on 2010-03-09
> **JcZndeR said:**
> I tried it, unfortunately that package was not found.
Does the CD not include ubuntu-desktop?
or should I install another package
or perhaps im not mounting the disk correctly..
seems right to me
Oh, sorry, run this command first:
sudo apt-get update
That should fix it. If it doesn't, try
sudo aptitude update

---

### Post by JcZndeR on 2010-03-10
hm, I had done that already, it complains about not being about to connect to a lot of http addresses
oddly, I already commented those links out of my sources.list

---

### Post by JcZndeR on 2010-03-13
yay! okay, so i could not get any packages installed offline
ubuntu doesnt seem to be happy without internet =/
so i hooked up an ethernet cable and found instructions on how to connect to the internet via command line, really easy
and installed ubuntu-desktop there
logged in, and everythign started up fine xD
its been quite an ordeal, :P woot!
thanks fivex for helping me ^_^

---

