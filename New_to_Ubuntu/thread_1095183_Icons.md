---
title: "Icons"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-03-13
Okay, so I posted this yesterday, but not paying attention, I had messed up the title. So I will try again.....

I have been running LinuxMint. Whenever I try to download and use an Icon package, the folders just look grey. It does not seem to matter where I get them from, or which package. 99% of the time, they don't change to the new theme.

Anyone heard of this happening before or know anything that could be broke?

Thanks

---

### Post by martrn on 2009-03-13
You may have a 'broken' or write protected  'index.theme'   file.

```
find ~/ -iname index.theme
```

Gnome should look at your home directory for a ./icon folder and search for index.theme file, and read from there onwards.

KDE's "index.theme" files are handled differently to Gnomes.

---

### Post by stchman on 2009-03-13
> **AndyP79 said:**
> Okay, so I posted this yesterday, but not paying attention, I had messed up the title. So I will try again.....

I have been running LinuxMint. Whenever I try to download and use an Icon package, the folders just look grey. It does not seem to matter where I get them from, or which package. 99% of the time, they don't change to the new theme.

Anyone heard of this happening before or know anything that could be broke?

Thanks

When you download an icon set it usually comes in .tar.gz form.  Are you saying that you cannot unpack the icons.  You open up the Appearance manager and drag the icon archive into it.

Does this answer your question?

---

### Post by gandaran on 2009-03-13
> **AndyP79 said:**
> Okay, so I posted this yesterday, but not paying attention, I had messed up the title. So I will try again.....

I have been running LinuxMint. Whenever I try to download and use an Icon package, the folders just look grey. It does not seem to matter where I get them from, or which package. 99% of the time, they don't change to the new theme.

Anyone heard of this happening before or know anything that could be broke?

Thanks
do you mean when you run a root nautilus window the icons are gray?
for icons to work for both root and all users they have to be installed in /usr/share/icons, icons installed in /home/user/.icons only work for that user.

---

### Post by AndyP79 on 2009-03-13
Thanks for the responses.

I am using gnome, just to clarify.

I download a tar.gz then I drag it to the icons in the apperance application. I gt the grey folders in everything, nautilus and on the desktop.

---

### Post by gandaran on 2009-03-14
in the appearance manager go to themes tab » personalize » icons tab »  choose the icon you installed, you still get grey icons then?

---

### Post by AndyP79 on 2009-03-14
Yes, this is where I was trying to explain where I am, when I change the icon theme, they are still grey

---

