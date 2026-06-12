---
title: "Changing from one computer to another"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by Chris Edgell on 2010-02-03
So, thanks to you, I burned that LiveCD AND installed it on Machine #3.

I liked the idea of having a slate "wiped clean" and since this machine has a bigger Hard Drive, I thought I'd see if I can use this as my primary machine as I solve any problems-as someone had suggested that I use the test machine until I get IT how I like it and then go ahead and choose which I wanted to be primary and which tester.

I hooked my flat-screen up to this box and also hooked up the Ethernet.

When I tried to boot up, it wouldn't, I got a message "No Sync", so I went into the BIOS and made sure it said: First Boot: CDROM.

Now THIS that you're looking at is booted from the CDROM, it offered me the option of install, but it is already installed, it just didn't boot from there.



I did see how this machine and new OS has no history -- I went through some changes getting to my mail and to set a new password to get on this forum.  

Any odd advise?  Shall I change the First Boot to HD?  I wonder if I shut down if all this that I HAVE DONE will be lost because I booted from the LiveCD.

I think I'll just wait and see if I hear some response from any of you about these questions, but you're probably sick of me for one 12 hour period...it was sorta' like giving birth in the back of a cab...you'd probably like to be on your way for awhile.

---

### Post by audiomick on 2010-02-03
Hi Chris.
There are a few things there.
Firstly, you can leave the BIOS setting to boot from the CD first. I makes the boot a bit slower, but that is all. The way it works is that the machine looks for an OS at the first entry in it's list, if it doesn't find one it goes on to the next entry, and then the next, until it finds an OS it can boot. If you let it look at the CD drive first, it will "waste" a few seconds looking there before it goes on to the hard drive to look. The advantage for you is that you don't have to go into BIOS and change that every time you want to boot something from a CD. I would suggest leaving it for now. When you get to a point where you are completely happy with the set up and don't look like having to use the live CD any time in the near future, you could change it to "HD first" to speed up your boot a bit.

The "no sync" message indicates that the flat screen isn't seeing a signal from the laptop.
When you boot into the live CD, does the flat screen work? When you boot the laptop without the flat screen, does it boot ok to it's own monitor? What model is the graphics card? Post the output of
```
lspci
```
if you don't know.

When you say the OS has no history, do you mean the history in Firefox? That will be gone after a reboot. Generally speaking, anything you might have changed somewhere not on the computer, e.g. a password in the Forum, which is saved on the forum server, will be remembered. Anything that the computer remembers will not be retained in a live CD session after reboot.

---

### Post by pirateghost on 2010-02-03
take the cd out and boot it up

---

### Post by Chris Edgell on 2010-02-03
Yup, I removed the CD and this time it booted to the OS I just installed this morning.  And it's a good thing too, because as was stated: all I did while booting from the CD was lost.  So now I'm very much on the right track.

Thanks!

---

