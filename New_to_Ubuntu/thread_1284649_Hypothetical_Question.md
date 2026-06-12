---
title: "Hypothetical Question"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by samh785 on 2009-10-06
So, say I was getting a new computer and I wanted to use ubuntu on it. How would I go about easily making it set up just like the computer I was currently using? How would I make it install all the packages that were in use on my current computer?

---

### Post by pythonscript on 2009-10-06
Didn't see your signature at first that says you're running Ubuntu. You could pull a list of all the packages on your system and just install them again from the repos. dpkg-repack is a nice utility to generate packages for software already installed on your system (if you don't want to waste the bandwidth re-downloading all the packages). Also, depending on the program, you can copy the config files from your current system over to your new one. 

If the hardware on your current system is virtually identical to that on your new one, you could just image your entire hard drive from your old computer and install that image onto your new one, then update all the software, left over modules, etc, accordingly.

---

### Post by Diabolis on 2009-10-06
1.- Make a list of the apps you have installed
2.- Copy the configuration files located in your home folder. Those are invisible, because their name start with a dot, and you can see them by pressing **<Ctrl> + H**.
3.- Install the list of packages in the new computer
4.- Paste the configuration files in the new home folder

> run the following command:

    dpkg --get-selections > apps.txt


This will store a list of every application that is currently installed to a file called apps.txt. If you are wanting to re-install your OS, then make sure that you save this file to a USB stick!

Once you are ready to install all your applications again:

    dpkg --set-selections < apps.txt
    dselect update
    apt-get dselect-upgrade show



Now after a lot of downloading and installing, you will once have all of your applications installed again.

[http://jamsubuntu.blogspot.com/2009/03/save-list-of-installed-applications.html](http://jamsubuntu.blogspot.com/2009/03/save-list-of-installed-applications.html)

---

### Post by Temposs on 2009-10-06
More precisely:

Backup your home directory to external storage. Specifically, backup any files and directories that start with a period(.). Copy it to the home directory on your new computer. Install all the apps you had before. All your apps should have the same configuration and options enabled because all of the application configuration files in Linux are held in the home directory in the files and directories that start with a period.

Then, install all the apps you had before using the usual method in Ubuntu with Add/Remove or Synaptic Package Manager.

---

### Post by CatKiller on 2009-10-06
> **pythonscript said:**
> If the hardware on your current system is virtually identical to that on your new one

This caveat is largely redundant. For the most part, the hardware is irrelevant since modules are loaded as they are needed. Proprietary (graphics, mostly, but potentially wireless networking too) drivers (since they can't be included in the kernel) would be a problem and might need to be re-configured, and switching from 32-bit to 64-bit would probably be simplest with a re-install.

Other than that, switching the hard drive to a substantially different computer probably won't cause any problems at all.

For sanity, a new install with the old Home directory and re-install of the previous packages might be best anyway, but Linux is pretty portable.

---

### Post by pythonscript on 2009-10-06
> **CatKiller said:**
> This caveat is largely redundant. For the most part, the hardware is irrelevant since modules are loaded as they are needed. 

Thanks for the reminder. Coming from Arch this is something that actually requires worrying about. I do love that about ubuntu!

---

### Post by oldos2er on 2009-10-06
Open Synaptic, File, Save Markings, save the file to a safe location that won't be overwritten. After installing Ubuntu on the new computer, open Synaptic, File, Read Markings, point it the file you saved earlier. Done.

---

### Post by MelDJ on 2009-10-07
> **samh785 said:**
> So, say I was getting a new computer and I wanted to use ubuntu on it. How would I go about easily making it set up just like the computer I was currently using? How would I make it install all the packages that were in use on my current computer?

maybe make a live cd with remastersys and install it on the new computer?

---

