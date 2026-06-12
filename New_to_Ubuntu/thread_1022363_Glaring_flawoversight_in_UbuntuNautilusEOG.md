---
title: "Glaring flaw/oversight in Ubuntu/Nautilus/EOG?"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by Andy06 on 2008-12-26
[Mods: My first 2 posts, I've started a similar thread in General help as well, please delete if duplicate is not appropriate]

Recently, we have been pushing everyone in our dorm residence to start using linux and since Ubuntu is just about the best distro to get started with, the linux lobby is busy installing Ubuntu on all computers.

Now I start getting feedback on this weird bug.

When you view images in nautilus, and then open one with eye of gnome (or in even with gthumb or gkview), pressing the next button on screen or on the keyboard takes you to the next picture ordered by name irrespective of how you have chosen to order them in your file browser/explorer. Even if you select the default as "order by date modified" and then re-open nautilus, the image viewing programs will still treat the images as if they are all in alphabetical order.

This is a real elementary thing and a total deal breaker for everybody since almost everyone orders their images by "date modified" or some other criteria and everyone uses next buttons for quickly going through all the images. With the current situation, one must view a picture, shut down EOG/Gthumb/GKview and then reopen it again by double clicking on the next picture. This is undesirable behaviour and completely counter to that of XP/Vista/Leopard/Snow Leopard. 

I might add that everything else works perfectly and all other little niggles with drivers and such are being troubleshooted by the Linux gang in college, but this single issue seems to be a deal breaker for potentially dozens of converts:(

There has been a bug report filed over an year ago here:
[https://bugs.launchpad.net/ubuntu/+source/eog/+bug/136740](https://bugs.launchpad.net/ubuntu/+source/eog/+bug/136740)

....although it doesn't seem to have received any attention or replies.

A thread regarding this problem was started around the same time (possibly same user:trudetski) here:
[http://ubuntuforums.org/showthread.php?t=480681](http://ubuntuforums.org/showthread.php?t=480681)

Once again......no replies or resolution. 

trudetski mate,
If you're reading this, how did you end up resolving this?

Helpppp please.

Thank you very much for your time.

---

### Post by pytheas22 on 2008-12-26
Yes, this is sort of a dumb feature to be missing.

An easy work-around, however, is to install gthumb, an alternative program for viewing images.  You can install it using add/remove programs or simply by typing:
```

sudo apt-get install gthumb
```

After it's installed, right-click in Nautilus on the image you want to view and select 'Open With'.  If you don't see 'gthumb Image Viewer' already listed, select 'Open with Other Application' and enter 'gthumb' as the custom command.

In gthumb, you can go to View>Sort Images By> and specify modification date as the means of ordering images.  It will then use that criteria for determining the image that gets displayed when you press the 'Next' button or left-click on the current picture.

If you want to make gthumb the default application for opening images from Nautilus, right-click on an image, select 'Properties', and you can specify the default application under the 'Open With' tab (you may need to do this once for each of the different types of image files on your computer, i.e., once for .jpg's, once for .png's, etc.).


I don't know why Ubuntu doesn't use gthumb, which has more features, by default; I think it used to.

Hope it helps.

---

### Post by spiderbatdad on 2008-12-26
Indeed if you open your pictures folder, for example, and select Edit>>Preferences>>Media. You can select gthumb to open all pictures.

---

### Post by suitedaces on 2009-05-06
I was having same problem and installed gthumb. However now whenever I double click on an image to open it, gthumb will only open that one, where as the old image viewer had the previous and next available. Any way around this other than opeing gthumb first then navigating to the folder?

---

### Post by pytheas22 on 2009-05-08
> I was having same problem and installed gthumb. However now whenever I double click on an image to open it, gthumb will only open that one, where as the old image viewer had the previous and next available. Any way around this other than opeing gthumb first then navigating to the folder?

I don't have this behavior.  When I open an image from within Nautilus using gthumb, the next and previous buttons are available for navigating through other images in that folder.  Are you sure you're opening the file with gthumb, and the images are in a normal, local directory (i.e., they're not shared over the network, and there are no virtual directories or symlinks in the equation)?

I'm on Ubuntu 9.04, using Gnome/Nautilus.

---

