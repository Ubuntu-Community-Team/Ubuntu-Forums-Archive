---
title: "Boot problem command line"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by Bruv on 2011-06-23
I have a very old PC that I am playing about with, it had XP Professional on it, long story, but I had put Linux Unity (I think) on it, and was testing it to destruction, and it has destructed.

Now I have tried to load the OS again to sort things out, but when I put the CD in to re load the OS, I have to login and end up with a command line window. The only command that works for me is 'halt' to shutdown. I think I have deleted whatever opens the OS. I know that the PC is on its last legs, but I don't believe it's a mechanical problem, just my lack of knowledge. I understand from this point I could download the bits I am missing........not the correct terms I know, but can anyone help me out here ?

---

### Post by skatinjj on 2011-06-23
Are you trying to load unity linux or ubuntu?

---

### Post by Bruv on 2011-06-23
I thought Ubuntu was Linux, but no I thought I was loading Ubuntu light.

Where I went wrong I think is lack of research, I think it is like buying a Bare Bones system, you need to know what extras to add and what you must NEVER take away, I think I have uninstalled something that was majorly important.

I shall try and Nuke the drive tomorrow and start again

---

### Post by chkneater on 2011-06-23
sounds like your grub menu is gone.  If you could run a LiveCD or remove the HD to a usable computer just do " sudo apt-get install grub "  (or grub2 I'm unsure about Unity)

---

### Post by Bruv on 2011-06-24
I have come to the conclusion the HD is shot to pieces.
It will only randomly boot to a boot CD and will not boot at all to a live CD.

I think I shall confine this PC to the scrap heap, unless we have some new ideas out there.

---

### Post by chkneater on 2011-07-25
Two things:

1) If your Hardrive is shot, your LiveCD will still work

2) If LiveCD only "randomly" boots that suggests your LiveCD is effed.

When you download LiveCD ISO's make sure to run the checksum and make sure they're correct, otherwise you end up with barely working CDs.

If you want to be extra safe just order the free LiveCD through the mail and you can upgrade with whatever you want.  Good luck and hope you didn't throw out that HD yet.

---

### Post by Miljet on 2011-07-26
Sounds to me like your CD drive is shot - not the hard drive. Try your live CD in another computer. If it works there, you likely need a new CD drive.

---

### Post by chkneater on 2011-08-12
I'm with Miljet, liveCDs don't work intermittent unless the drive or the CD is bad. Try the LiveCd in another computer, then try a working CD drive in your Comp.  Process of elimination!!  Then again if it's an Imac or something...

---

