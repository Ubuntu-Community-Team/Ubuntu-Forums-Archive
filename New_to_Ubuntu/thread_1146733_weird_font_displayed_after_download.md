---
title: "weird font displayed after download"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by Arrorn on 2009-05-02
I installed some dependencies (cairo-dock thinking it was cairo) for the new TiLP and when i restarted my laptop everything is now displayed empty boxes...

The computer itself is still intact so i can look at files and stuff but everything i type or is written is empty boxes... since my root command prompt in the recovery mode still displayed in English... i first uninstalled the dependencies hoping that would fix it... no such luck

I looked online a bit and found someone had a similar issue with ubuntu 6 so i tried one of his suggestions and edited xorg.conf so it leads to the proper font paths... he had suggested that the font directories were screwed up, so on another computer that i also have ubuntu 9.04 installed on i checked his suggest new font paths and they looked ok... so i copied the edited xorg.conf file onto my screwed up laptop, i copied the original xorg.conf to my desktop, and now when i boot it up it and it gets to the login screen it still displays a font consisting of empty boxes and now gives me an unintelligible error message...

is there any way i can revert my computer back to before i installed the dependencies.

The computer that is screwed up is a toshiba laptop dual booting vista and ubuntu 9.04... i have another 2003 dell desktop with ubuntu 9.04 and a 2004 compaq laptop also with ubuntu 9.04 and then i have a home built computer running vista...

---

### Post by 123456789123456789123456 on 2009-05-02
you can try this, but I don't know how it will work.  You need to make a backup of the current system, screwed up as it is.  After that, attempt to use synaptic, to perminitly remove the dependencies, and the packages that you recently added to the computer.  After that, restart, in recovery mode, make sure that the font and language is set correctly, and restart the computer manually.

If that does not fix the problem, attempt perminatly removing all recent files, all that have been added to the system, after the date the OS was created, so any packages that were added to the system after the relase date of 9.04, remove, then install them.

that should hopefully fix the problem, unless something in the core system was corrupted.

---

### Post by Arrorn on 2009-05-02
yeah i'm making a back up of the entire home folder... then i'm going to back up the package.selections and i'm just going to reinstall ubuntu on the laptop.... i cant read anything so i will have no idea what buttons to press in synaptic to do what you suggested... and i already removed the dependencies that i had installed be for this... the root is still in english...

---

### Post by Didius Falco on 2009-05-02
After you back up, but before you reinstall, try this:

If you can still boot up and use the Terminal from a normal boot, do so and type

```
sudo apt-get purge cairo-dock 
sudo apt-get purge cairo-dock-plugins

```That will remove the packages and all their configuration files.

If you can't boot up normally, boot into Recovery mode to the Command line and issue the same commands.

Then reboot.

I hope this helps

On Edit: You may be prompted by synaptic to run ```
sudo apt-get autoremove
``` after you've issued the above commands. If so, do that before rebooting.

---

