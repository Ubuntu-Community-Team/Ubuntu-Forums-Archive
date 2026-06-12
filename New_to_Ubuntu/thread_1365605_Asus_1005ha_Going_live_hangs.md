---
title: "Asus 1005ha Going live hangs"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by rottentree on 2009-12-27
So I have recently got an Asus 1005ha(the faster one n280...) and I have been fiddling around with it trying to find the best linux for my taste I successfully installed crunchbang linux then later eeebuntu but I didn't like them(one of my main reasons was that they couldn't detect my wired connection whereas Windows XP recognised it with no fuss, no wifi at home I just wanted to set it up the way I like it)

So I continued my testing with Ubuntu 9.10 NBR and Xubuntu 9.10(downloaded them and put them up on a pendrive with unetbootin) now the weird thing is that:
 Ubuntu got stuck at a black screen with the mouse active(but showing the thinking/loading animation) so I waited then waited... after that I got bored with it and pressed the Shutdown button on my laptop which Ubuntu recognised and tried to quit but came up with a bunch of errors and I ended up with a console like interface(you know all text, blinking _ ) which didn't respond to anything so I had to take out my battery to 'shutdown'(does that hurt my netbook ? :S )
 Xubuntu did a similar performance but instead of thinking forever it got stuck in an infinite loop constantly loading in the same things(switches to console like interface)  then back to the black screen then loading in the exact same things it did before.

So what the hell is going on corrupted downloads? :S
My pendrive has suddenly decided it's time for revenge?
Or is it something else?
:(

---

### Post by rottentree on 2009-12-28
shameless bump :P

---

### Post by Kobalt on 2009-12-28
I don't understand : is it something happening from a Live USB environment or from your install (which you did from an USB key) ? 
How did you create your bootable USB stick ?

---

### Post by rottentree on 2009-12-28
Oh damn it I thought I was clear.

The problem happens from the Live USB environment after the loading bar(or in the case of 9.10 the flashing icon) disappears it only loads up a black screen and can't get past it.

I tried it out with Xubuntu 9.04 and that works so the problem seems to be with 9.10 but shouldn't the live environment detect a wired connection because it doesn't seem to :-|

---

### Post by milosz.galazka on 2009-12-28
Couple days ago I installed ubuntu on 1005ha without any problems.
I can check out booting from usb after I return home.

Although Moblin live cd didn't worked well (probably wifi as I remember) but after installation wifi was regonized and started working.

---

### Post by Kobalt on 2009-12-28
> **rottentree said:**
> Oh damn it I thought I was clear.

The problem happens from the Live USB environment after the loading bar(or in the case of 9.10 the flashing icon) disappears it only loads up a black screen and can't get past it.

I tried it out with Xubuntu 9.04 and that works so the problem seems to be with 9.10 but shouldn't the live environment detect a wired connection because it doesn't seem to :-|

How did you create your Live USB ?

---

### Post by rottentree on 2009-12-28
> **Kobalt said:**
> How did you create your Live USB ?

Oh sorry I forgot to answer with the Unetbootin program.

---

### Post by Kobalt on 2009-12-28
OK.
Did you try this : at the very first Ubuntu boot prompt, press F4 and chose to boot in "safe graphics mode" ?

---

### Post by rottentree on 2009-12-28
> **Kobalt said:**
> OK.
Did you try this : at the very first Ubuntu boot prompt, press F4 and chose to boot in "safe graphics mode" ?

There is no Ubuntu boot prompt (or I don't know how to get it) after the Unetbootin menu it immediately starts the live environment.

---

### Post by RipleyAM on 2009-12-28
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)
This is what i used to install Ubuntu on my 1005ha.  It worked flawlessly for me.  This also gives you a boot prompt.

edit: If you end up liking NBR and you want to remove the netbook interface here's a link to do that.
[http://ubuntuforums.org/showthread.php?t=1308792](http://ubuntuforums.org/showthread.php?t=1308792)
the tutorial is in the 6th post.

---

### Post by wobin77 on 2009-12-28
Make sure your pendrive is formatted as FAT32 and not NTFS. This was my problem why it wouldn't run or run and hangs.

---

### Post by rottentree on 2009-12-28
I can't even format it to NTFS I'm on XP and the only option it gives me is FAT32 but I will keep that in mind for the future :)


> **RipleyAM said:**
> [http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)
This is what i used to install Ubuntu on my 1005ha.  It worked flawlessly for me.  This also gives you a boot prompt.

edit: If you end up liking NBR and you want to remove the netbook interface here's a link to do that.
[http://ubuntuforums.org/showthread.php?t=1308792](http://ubuntuforums.org/showthread.php?t=1308792)
the tutorial is in the 6th post.

I'm going to try it out! Will report how it goes.

I got the boot prompt but there was no option to set it to 'safe mode' also pressing F4 didn't do anything so I tried to load up the live environment and it got stuck the same way it did with Unetbootin. I chose the standard 1Gb option with the [COLOR=#0066FF]USB-Installer-for-Ubuntu.exe[/COLOR]

---

### Post by rottentree on 2009-12-29
bumpdate

And I forgot to mention after it gets stuck and I press the shutdown button on my laptop it tries to unload things and comes up with a bunch of "SQUASHFS errors" complaining about: "error reading block [insert numbers and letters here]"(I don't know if I remember it 100% accurate but something similar)

---

### Post by Kobalt on 2009-12-29
> **rottentree said:**
> I chose the standard 1Gb option with the [COLOR=#0066FF]USB-Installer-for-Ubuntu.exe[/COLOR]

What exactly do you mean by this ? 
I've used Unetbootin with previous releases of Ubuntu, and the current stable one, on the very same computer you have. And I never had any trouble. 
I just downloaded the regular Ubuntu Desktop 32-bit ISO and pointed Unetbootin to this ISO, and my USB stick.

By the way : formating the drive to Fat32 is fine in order to create a bootable USB stick, no need to format in NTFS.

---

### Post by rottentree on 2009-12-29
> **Kobalt said:**
> What exactly do you mean by this ?

[RipleyAM]("http://ubuntuforums.org/member.php?u=984187") suggested that I should try out this [http://www.pendrivelinux.com/create-...sb-in-windows/]("http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/") because it worked for him so I did but it didn't work for me also it should have gave me a boot prompt where I could have loaded it up into safe mode (which you suggested)  the boot prompt was there but not the option to load into safe mode.

> **Kobalt said:**
> 
By the way : formating the drive to Fat32 is fine in order to create a bootable USB stick, no need to format in NTFS.

I didn't format it to NTFS and I don't want I just noted that I'm going to keep that in mind that formatting to NTFS can lead to problems :)

---

### Post by Kobalt on 2009-12-29
Do you ever get this boot screen ? 


[IMG]https://help.ubuntu.com/community/BootOptions?action=AttachFile&do=get&target=mainboot.png[/IMG]

---

### Post by rottentree on 2009-12-29
No with Unetbootin I don't get that screen.

With the method [RipleyAM]("http://ubuntuforums.org/member.php?u=984187") suggested I do get a similar screen but not exactly that (some of the menu options are not there or are a bit different the F<key> are not there and it's not chopped off because it won't react when I press them)

---

### Post by rottentree on 2009-12-30
[http://forum.eeeuser.com/viewtopic.php?pid=658619](http://forum.eeeuser.com/viewtopic.php?pid=658619)
According to the last post in that topic I'm not the only one with this problem.

---

