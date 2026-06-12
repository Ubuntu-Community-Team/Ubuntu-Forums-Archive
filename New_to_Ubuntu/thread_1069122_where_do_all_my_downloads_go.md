---
title: "where do all my downloads go?"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by eimiandra on 2009-02-13
so I just downloaded skype and intsalled all the packages and now I can't find it.  Nor any of my other applications or downloads.  

Where are the applications located (aside from the tool bar)?
and where do all my downloads keep going?

(i just switched from mac osx to ubuntu.  can yu tell?)

---

### Post by egalvan on 2009-02-13
> **eimiandra said:**
> so I just downloaded skype and intsalled all the packages and now I can't find it.  Nor any of my other applications or downloads.  

Where are the applications located (aside from the tool bar)?
and where do all my downloads keep going?

(i just switched from mac osx to ubuntu.  can yu tell?)

Is there a specific reason you downloaded Skype, 
instead of loading it via Synaptic? (Or apt-get?)

(Sorry, I can't help any further, I was going to experiment with this, but the files are over 15Megs, and I don't have that much time right now.)

---

### Post by eimiandra on 2009-02-13
yeah, the same thing happened when i used synaptic.  basically, i'm clever enough to download the packages for the program, but that's as far as i get.

---

### Post by kanikilu on 2009-02-13
If you are using Firefox, you can go to Edit > Preferences and in the Main tab under the Downloads section you can set where files are automatically saved to.

I'm assuming you downloaded the .deb package for Skype, right? If so, once you find where you downloaded it, just double-click on the .deb file to run the installer. After it's installed, I assume a menu item will automatically be created under Applications > Internet, but I'm not positive since I don't use it...

---

### Post by howefield on 2009-02-13
Installing skype from synaptic should put an icon in your Applications > Internet menu, but if as you say, it isn't there all you need to do is create a launcher for it. 

Go to System > Preferences > main menu and add a launcher by selecting the group you want it in and select new item. Fill in the fields with skype as the command and whatever you want in the other two.

You can also launch skype by typing skype into a terminal.

Your downloaded .debs (from the package manager) go into your /var/cache/apt/archives folder.

---

### Post by itendo on 2009-02-13
if youre not using a package manager, are you using a broswer (FF, konqueror) for downloading?

if so, the internal preferences will determine you where the files go. to locate, with FF you'll have the download window, where if you right click on the the icon that DL'ed it will give "open in containing folder" as an option if youre just wanting to know the directory.

---

### Post by ugm6hr on 2009-02-13
> **eimiandra said:**
> so I just downloaded skype and intsalled all the packages and now I can't find it.  Nor any of my other applications or downloads.  

How did you install the packages you downloaded if you can't find them?

I'm confused as to what's going on :confused:

---

### Post by 73ckn797 on 2009-02-13
Doesn't Firefox default downloads to the desktop?

---

### Post by Mark Phelps on 2009-02-13
> **eimiandra said:**
> so I just downloaded skype and intsalled all the packages and now I can't find it.  Nor any of my other applications or downloads.  

Where are the applications located (aside from the tool bar)?
and where do all my downloads keep going?

(i just switched from mac osx to ubuntu.  can yu tell?)

Since you're new to Linux, I would strongly advise you AGAINST downloading stuff directly.  That stuff is often kept in compressed source archives that require LOTS of supporting libraries and packages for you to find and install.  This is something you shouldn't be attempting until you are quite experienced with Linux because it's one of the harder things to do. You may end up installing dozens of packages and making quite a mess of your system in the process.

As to new apps, you can obtain them either of two ways.  Applications --> Add/Remove will provide a list of apps that you can add to your system. Just select the category, select the application, click Apply Changes -- and it's automatically installed.  Synaptic (Administration --> Synaptic Package Manager) works much the same way but uses the actual package names.  You mark the packages you want installed, apply the changes -- and they get installed.

Where they appear is on one of the menus that gets tiled from Applications.  You have to open the menus to find it.  It really depends on which app/package you install because they're all different.

Hey ...and don't feel bad.  We were ALL new to Linux once.

My guess about download location, is probably either on your desktop, or in a folder in your HOME directory (/usr/home/<username>/).  You can find your HOME directory by clicking Places --> Home Folder.

---

