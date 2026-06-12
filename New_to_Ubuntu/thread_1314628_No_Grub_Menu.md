---
title: "No Grub Menu"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by neigun on 2009-11-04
Hi

I've just upgraded to Karmic 64 bit and am experiencing a number of problems related to Grub (or at least I think so!?)- that is most of the time there is no Grub menu available and secondly my PC just boots into 9.10 without giving an option for XP. Some text does appear stating that grub is loading, or words to that effect, but then an Ubuntu symbol appears, prior to the log in screen, with no sign of an actual Grub menu with boot options. 

I did a fresh install, after previously doing an upgrade, so as to have a clean start with Ext 4 and the advice was that the legacy Grub would not recognise Ext 4 so it needed upgrading as well. The two OS's are on separate hard drives rather on a partitioned drive- if that makes any difference.

On occasion I have managed to get the Grub menu up, minus an option for XP, but usually it just boots into 9.10. Then when I reboot it's gone again.

Previously I had 9.04 installed and running as a dual boot with XP (only so I can use my scanner, honest :D ).

Many users seen to be experiencing problems with Grub but nothing I've tried so far is successful:-k

Any thoughts anyone?

---

### Post by ranch hand on 2009-11-04
First off, you are now using grub2.  You should read the link in my sig (1st post) and check the links for in depth info.  These are the guys that know how to get the bugger to sit up and beg.

Your menu is coming up.  It is hidden.  Hitting Esc will not work.  Hold down your shift bar.

It does not sound like your MS is on the menu.  The menu should not be hidden if there is more than one OS.

Run;
```

sudo update-grub

```
That will generally straighten it out.

You can hash the hidden menu stuff in /etc/default/grub.

---

### Post by bodhi.zazen on 2009-11-04
This is the new default behavior for grub2

for information on grub2 see :

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

For your problem, see this section :

[https://help.ubuntu.com/community/Grub2#Boot%20Display%20Behavior](https://help.ubuntu.com/community/Grub2#Boot%20Display%20Behavior)

---

### Post by neigun on 2009-11-05
Thanks Guys

I tried Sudo update-grub ranch hand but Grub is not detecting XP on a separate drive for some reason and is therefore booting straight into 9.10.

The Grub version is shown below if that helps?

neil@neil-desktop:~$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)
neil@neil-desktop:~$ 

Start up manager is installed but does not give the same options as shown here: [https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

For example the "Show bootloader menu" is not available under the Boot options tab. Whilst under the Appearance tab the options for "Bootloader menu colours" and "Bootloader themes" is not present. The Security tab is absent altogether.

The only option would appear to be to edit Grub manually, which I'm a tad nervous about doing.

Neil

---

### Post by ranch hand on 2009-11-05
SUM is not working with grub2 yet.  It will do somethings but you really should wait until the developer gets the one for grub2 done (he is working on it).

As far as booting to a different drive goes, I am not sure what to say.  I have some problems with that myself.

You are trying to boot to MS and I know nothing about that at all, and better yet, have no desire to learn.  Sorry.

There are a lot of MS users on here, I am sure they can help.

Did you check the second link on my Intro post?  There may well be help there.

---

### Post by neigun on 2009-11-08
Thanks for your help Ranch and bodhi.zazen. 

Now I've read more in to it, it does seem to be a problem with Grub2 detecting other OSs, not just MS, on other drives.

The issue with Grub2 is still not resolved and I would like to use my scanner- so any other suggestions would be much appreciated.
:confused:

Part of the problem is the shear quantity of postings on the issue. Are you aware of any that relate to Grub2 detecting other OSs on separate hd, which have come up with a solution?

Neil

PS I wont get my scanner running in Ubuntu as its a Canoscan 3200F and I don't really want to buy another scanner just yet](*,)

---

### Post by wrgb2 on 2009-11-08
I know it's a kludge but can you change you're boot drive to the xp drive in you bios?  It's a pain, but at least you could use your scanner.

---

### Post by neigun on 2009-11-08
I think you are right and it'll have to do for the moment.

---

### Post by neigun on 2009-11-17
Well that didn't work](*,)

---

### Post by kansasnoob on 2009-11-17
Just to clarify, what can you boot right now?

---

### Post by sisco311 on 2009-11-17
Edit the /etc/grub.d/40_custom file:
```
gksu gedit /etc/grub.d/40_custom
```


if windows is on the second hard drive's first partition:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Microsoft Windows XP" {
        set root=(hd1,1)
        devicemap -s hd0 hd1
        chainloader +1
}
```

Note: devicemap might be drivemap.

if it's on the first hard drive's first partition:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Microsoft Windows XP" {
        set root=(hd0,1)
        chainloader +1
}
```

run:
```
sudo update-grub
```
and reboot.

[thread=1195275]The Grub 2 Guide[/thread]
[http://en.gentoo-wiki.com/wiki/Grub2#Windows_entry_for_Grub2_config]("http://en.gentoo-wiki.com/wiki/Grub2#Windows_entry_for_Grub2_config")

---

### Post by neigun on 2009-11-18
):p

---

### Post by neigun on 2009-11-18
-

---

### Post by neigun on 2009-11-18
Thanks Sisco311

your advice did exactly what it said on the tin!

I can now use my scanner

---

