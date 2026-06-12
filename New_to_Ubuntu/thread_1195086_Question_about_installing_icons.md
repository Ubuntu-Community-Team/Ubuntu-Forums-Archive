---
title: "Question about installing icons?"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by cptrohn on 2009-06-23
Ok... so I got a nice new glossy theme last night that I REALLY like and I am trying to get a new set of icons installed but I guess I am doing something wrong that can't figure out.

I want these icons   [http://www.gnome-look.org/content/show.php/black-white+2+Style?content=72619](http://www.gnome-look.org/content/show.php/black-white+2+Style?content=72619)

And I seem to be having the permissions trouble they are talking about in their instructions... and I can't figure it out on my own and am about to pull my hair out over it.. LOL

PS... I'm really wanting to get this eye candy working because I'm supposed to meet a couple friends.... that use Vista that brag about how "good" it looks and how ubuntu looks too "plain" for them....

---

### Post by michy99 on 2009-06-23
Can you be more specific about the problems you are having? What did you try and what was the result?

---

### Post by billgoldberg on 2009-06-23
Extract the tar file or whatever it came in and put the folder containing the icons in 

/home/yourusername/.icons

Then go to System -> Preferences -> Appearance en choose customize.

Then pick the icon theme.

Check my [customizing ubuntu guide]("http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/") for more info on theming Ubuntu.

---

### Post by cptrohn on 2009-06-23
> **michy99 said:**
> Can you be more specific about the problems you are having? What did you try and what was the result?

I downloaded the file and extracted it to the desktop, I then go to places>computer>usr>share>icons   and then I try to drag and drop the folder into the icons folder I get an error message saying that permission is denied to move them into the Icons folder.

I've never tried to download new icons before and I am having a hard time with this for some reason (so I'm probably missing something simple)

---

### Post by Therion on 2009-06-23
> **cptrohn said:**
> I want these icons   [http://www.gnome-look.org/content/show.php/black-white+2+Style?content=72619](http://www.gnome-look.org/content/show.php/black-white+2+Style?content=72619)
Have you tried simply downloading the icon file (most likely you'll wind up with a .tar.gz), saving it on your Desktop and then opening the Appearance Manager (Theme tab) and dragging and dropping the file onto it?  Do NOT extract the file.  Drag and drop the .tar.gz file you have on your Desktop.  This procedure works for most icon-packs, assuming the author packaged the download in the standard format.

If everything goes correctly you should be prompted if you want to use the newly installed "theme" right away.

---

### Post by cptrohn on 2009-06-23
> **billgoldberg said:**
> Extract the tar file or whatever it came in and put the folder containing the icons in 

/home/yourusername/.icons

Then go to System -> Preferences -> Appearance en choose customize.

Then pick the icon theme.

Yes, but it won't let me put the folder into icons for some reason.

---

### Post by starcraft.man on 2009-06-23
> **cptrohn said:**
> Ok... so I got a nice new glossy theme last night that I REALLY like and I am trying to get a new set of icons installed but I guess I am doing something wrong that can't figure out.

I want these icons   [http://www.gnome-look.org/content/show.php/black-white+2+Style?content=72619](http://www.gnome-look.org/content/show.php/black-white+2+Style?content=72619)

And I seem to be having the permissions trouble they are talking about in their instructions... and I can't figure it out on my own and am about to pull my hair out over it.. LOL

PS... I'm really wanting to get this eye candy working because I'm supposed to meet a couple friends.... that use Vista that brag about how "good" it looks and how ubuntu looks too "plain" for them....

First put the file you downloaded on the Desktop, then extract it _once_ with the right click. This gets you to the black white style folder with instructions. System > Preferences > Appearances. Click install, navigate to the archived tar.gz theme inside the folder you extracted. Push ok, and add. Now it's added to your set of icons, you can mix and match as you like.

For the record, the read me instructions are garbage. I just added the icons to my theme by doing this, they look pretty!

---

### Post by cptrohn on 2009-06-23
> **Therion said:**
> Have you tried simply downloading the icon file (most likely you'll wind up with a .tar.gz), saving it on your Desktop and then opening the Appearance Manager (Theme tab) and dragging and dropping the file onto it?  Do NOT extract the file.  Drag and drop the .tar.gz file you have on your Desktop.  This procedure works for most icon-packs, assuming the author packaged the download in the standard format.

If everything goes correctly you should be prompted if you want to use the newly installed "theme" right away.

No I haven't tried that...I'll give it a shot.

---

### Post by billgoldberg on 2009-06-23
> **cptrohn said:**
> Yes, but it won't let me put the folder into icons for some reason.

Impossible.

Unless you screwed around with permissions.

Then you could just revert them back or use nautilus in root mode to paste the folder there.

Use the command 

```
gksu nautilus
```

to launch nautilus as root.

---

### Post by aeiah on 2009-06-23
> **cptrohn said:**
> Yes, but it won't let me put the folder into icons for some reason.

that's because you're trying to put them in /usr/share/icons/

this is part of the root file structure and you need special permissions to write to it. its certainly possible. you can launch a nautilus filebrowser window that has root permissions by running gksudo nautilus but its much simpler to plop the icon folder into your home directory in the .icons folder. note that folders that start with a dot are hidden normally.

browse to your home directory, hit ctrl+h to unhide your hidden folders, find your .icons directory, and put your unpacked icon folder in there. you can then hit ctrl+h again to hide all those unsightly hidden folders.


ps: icons in /usr/share/icons/ are available to all users (including root), whereas ones in your home directory are only available to you (your username). this shouldnt be an issue for you but if you have a lot of users and want them to have that particular icon set then you should place them in /usr/share/icons. otherwise, always put them in the home/.icons folder

---

### Post by cptrohn on 2009-06-23
> **starcraft.man said:**
> First put the file you downloaded on the Desktop, then extract it _once_ with the right click. This gets you to the black white style folder with instructions. System > Preferences > Appearances. Click install, navigate to the archived tar.gz theme inside the folder you extracted. Push ok, and add. Now it's added to your set of icons, you can mix and match as you like.

For the record, the read me instructions are garbage. I just added the icons to my theme by doing this, they look pretty!

This worked!  Thanks alot to everybody for their help!!

LOL  Let that bum say my ubuntu looks "plain" again...LOL!

---

### Post by billgoldberg on 2009-06-23
> **cptrohn said:**
> This worked!  Thanks alot to everybody for their help!!

LOL  Let that bum say my ubuntu looks "plain" again...LOL!

I gave the correct anwser to your problem a few posts back but you didn't read it correctly.

I said you need to put the files in your  /home/username/.icons folder, yet you still put it in /usr/...

While this time it worked out for you, when you have other questions and you aren't doing what people say you might not be able to solve the problem.

In this case there were multiple ways to install icons, other times there might only be one solution.

Just saying.

---

### Post by cptrohn on 2009-06-24
> **billgoldberg said:**
> I gave the correct anwser to your problem a few posts back but you didn't read it correctly.

I said you need to put the files in your  /home/username/.icons folder, yet you still put it in /usr/...

While this time it worked out for you, when you have other questions and you aren't doing what people say you might not be able to solve the problem.

In this case there were multiple ways to install icons, other times there might only be one solution.

Just saying.

Well excuse me for being human

---

### Post by ~sHyLoCk~ on 2009-06-24
A simple drag and drop of the *.tar.gz file on the Theme Windows [Right click on desktop and click Themes tab!] installs icons for me in Gnome.

---

