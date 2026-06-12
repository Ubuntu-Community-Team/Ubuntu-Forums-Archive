---
title: "OEM Install - removing elements &amp; changing theme"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by fatality_uk on 2010-08-26
Hi all.

So I am wanting to start selling Ubuntu PC's to the masses in the UK but have a wee problem. I have tried using the OEM install function, which works for the most part.
The problem is that once the ```
sudo oem-config-prepare
``` is sent to the newly configured system, after logging in as a new user, all the config I did in the OEM section is lost. All the apps I installed are still there, but for instance the theme changes back to the default and the bottom panel, which I removed is back.

I am pretty sure that shouldn't happen, but wanted to check if there is a work around for this.

Thanks

---

### Post by Mrandersonjr on 2010-08-26
Are you making the new user before or after you issue the command?

---

### Post by Paqman on 2010-08-26
What are you actually doing when you're setting it up though? Do you modify /etc/skel?

---

### Post by fatality_uk on 2010-08-27
> **Paqman said:**
> What are you actually doing when you're setting it up though? Do you modify /etc/skel?

Errr nope :)

I am following instructions from here:
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
which says boot into OEM mode, makes changes, i.e. install packages, drivers etc and then run ```
sudo oem-config-prepare
``` which I did, but as I say, the main things is the theme and bottom panel don't sty as I had it in OEM mode.

I am probably being dense, but that's usual for me!!

---

### Post by fatality_uk on 2010-08-28
Has anyone had experience with OEM installs? I can't seem to find any tutorials for 10.04.

---

### Post by mcduck on 2010-08-28
> **fatality_uk said:**
> Errr nope :)

I am following instructions from here:
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
which says boot into OEM mode, makes changes, i.e. install packages, drivers etc and then run ```
sudo oem-config-prepare
``` which I did, but as I say, the main things is the theme and bottom panel don't sty as I had it in OEM mode.

I am probably being dense, but that's usual for me!!

The user you use during the OEM installer is deleted afterwards, and a new user is created when the new owner of the computer starts it first time.

Anything you put in /etc/skel will be copied to any new created user's home directory, and as all user's setting, for both the desktop and all the programs, are stored in hidden config files in user's home directory you just have to make the settings you want and then copy the relevant setting files into /etc/skel.

The same mechanism applies to users created on a installed machine, and also the guest session. So if you want to practice configuring the new user accounts you can do it easily on an already-installed Ubuntu system by creating a new user account, configuring it as you like it, and then copying all the setting files form that account to /etc/skel. Then start a guest session to see if all the settings you made are there or if you missed some config file or directory.

Note that you don't have to copy everything from the user directory to /etc/skel, only the stuff you actually want to change from the default settings. And you usually don't want to copy the files form user account that is actually in use, as you might, for example, want to copy some settings for Empathy messenger but not any actual messaging accounts.

---

### Post by fatality_uk on 2010-08-28
Thanks all. Will give /etc/skel a go.

---

### Post by fatality_uk on 2010-11-04
Quick update. I did a copy using the method /etc/skel/ and that worked really well. Thanks for the help guys.

---

