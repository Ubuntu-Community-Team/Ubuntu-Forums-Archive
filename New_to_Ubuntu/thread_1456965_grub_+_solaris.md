---
title: "grub + solaris"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by anewguy on 2010-04-17
I have an extra disk I was thinking about installing solaris to just to try - I intend to stick with Ubuntu and with Windows as well.

I've read most of the stuff on how grub2 works and I think I know what I would need to do if I had to do it manually, but my question is:

If I install Solaris to a seperate disk (it uses an older version of grub) will it mess up the grub2 stuff on the mbr of my main disk?  If not, when I do boot back into ubuntu on my main disk if I run update-grub will grub2 pickup the solaris installation on the other disk and create an entry on the boot menu for it?

Thanks in advance!

Dave ;)

---

### Post by zvacet on 2010-04-18
> If I install Solaris to a seperate disk (it uses an older version of grub) will it mess up the grub2

I think not if you don´t install Solaris grub on MBR.To add Solaris to the grub2 you will have to add entry or reinstall grub2.In both cases you will have to run

```
sudo update-grub
```

---

### Post by oldfred on 2010-04-18
Grub2 is very good at finding other systems but my understanding is Solaris is a totally different system. If you make sure Solaris installs its grub to the MBR of the separate drive and sudo update-grub does not find it you can add a chainboot entry to 40_custom to link to the MBR to the other drive. It may be better to chainboot anyway as any changes to  Solaris will automatically be reflected in its boot menu.

menuentry "Chainload Other System on sdb" {
set root=(hd1)
chainloader +1
}

---

### Post by -humanaut- on 2010-04-18
Solaris and Ubuntu don't get along to well with Grub try googling it theres ways to install them side by side but it's tricky (trust me I lost an entire solaris system and they were on two separate harddisks)

---

### Post by anewguy on 2010-04-18
Based on what everyone is saying (and *THANKS* everyone!), what I'm going to do is remove the cables from my main harddrive so I can't accidently hose it, and just have the 2nd drive only running when I install Solaris.  Then I can try the chainload to see how that works.

Just another quick question if you don't mind:  my 2nd drive is currently the slave on my IDE channel with my main disk being master.  I have a DVD/RW on the 2nd IDE adapter.  I know that an IDE channel is only as fast as its slowest device, and since my main disk is ata 133 but the 2nd disk is only ata 100, I would prefer not to slow down my main disk.  So, I want to move it to the 2nd IDE adapter.  Just 1 little problem - the bays where my DVD/RW is requires a slide adapter on one side since the case only open on 1 side.  Unfortunately, the slide adapter isn't common like most of them, and as much as I've tried in the past I can't locate one.  The cage is completely riveted to the case, whereas the hard drive cage is at least removable.  My IDE cable won't reach from hard drive bay up to any of the bays my DVD/RW could be located in.  So, do they make a cable now that my old timer's hat doesn't know about that has a larger distance between the first and second ports on the cable?

Thanks for all your help!

Dave ;)

---

