---
title: "Desktop icon can't be changed"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by CinemaScope on 2010-04-06
I added a second HDD to my system which is **Ubuntu 9.10 **(32-bit) and it seems to be working well. For the second drive I used **GParted** to delete the old partitions and create a single partition (primary partition in ext4 format). Used **Psydm** to permanently mount the drive, and in a terminal used "sudo chown john /media sdb1" to allow me to write to the drive.

My problem is, I can't change the default desktop icons to folders on the second drive. Desktop icons for the main drive can be changed as normal, but for the second drive, when I use the usual method to choose a different icon image (using **properties**) the chosen icon image is not accepted and the original default grey folder icon remains. I have tried choosing icons from **pixmaps**, **icons**, and my own collection of icons in a folder in **Documents** but still no good. I copied across my own folder of icons to the second drive -- in case it needed to be on the same drive as the item it is a shortcut to -- but still same result. 

Another thing noticed: when I move the position of the desktop icons (for items on the second drive) to the place I want them, on next reboot they are back to the default position of top-left (icons for items on the main drive remain fixed in their positions as usual).

Not a big problem but annoying I can't use my collection of icons! Any suggestions greatly accepted, thanks.

---

### Post by CinemaScope on 2010-04-11
Anyone have any ideas about this problem? Have you got two drives on your machine and can change the icons without problem! What am I doing wrong?
Thanks.

---

### Post by durand on 2010-04-11
It seems to work here. What happens exactly, does it selet the drive and then change after a reboot or does it just not let you set the image? Because I just tried it with a removable drive and I can only set it's icon if I manually type in the name of the image file, otherwise, it doesn't work right :S

---

### Post by CinemaScope on 2010-04-11
Thanks for replying. I have created some desktop shortcuts to folders in a second, permanently mounted HDD. The shortcuts work, but I have been unable to personalise the shortcut icons (change them from the default icon image). The only way I know how to do this is through **Properties**: on the **Basic** tab click on the current icon image and then use the file browser to navigate to a folder with icons (small png images) and click on the one you want to use. Normally this is confirmed by the new icon image taking the place of the old one in the **Properties** dialogue, and then on quitting that dialogue, you see the icon now has the chosen new icon image.

This works fine with shortcuts to folders on my main drive, but for some reason not for shortcuts to my second drive.

"I can only set it's icon if I manually type in the name of the image file" -- can you explain how I can do that? As far as I can see, changing an icon image using **Properties** does not allow you to type in an image name.
Thanks.

---

### Post by durand on 2010-04-11
It's pretty simple, just click on the icon next to the current location. Here's what it looks like here:
[IMG]http://img217.imageshack.us/img217/5229/screenshotselectcustomi.png[/IMG]

---

### Post by CinemaScope on 2010-04-11
Thanks for posting that screenshot, I wish I knew how it relates to my problem! Is "durand" a shortcut icon on your desktop and "thefence" the image you want as it's icon? I'm pretty sure it isn't because the desktop is seen at the same hierarchy level which therefore means we can't be referencing an icon on the desktop? From the main menu I invoked a window like your's but I don't know what to do next. What is the relationship between a desktop shortcut icon and this window?

Can you talk me through it step by step? For example, if I have a desktop shortcut called "media files", don't I need to be at the desktop level to link an image file to it as an icon? I'm totally lost here I'm afraid.

---

### Post by durand on 2010-04-11
Uhm, your image file can be anywhere you like. All I did there was:
- Right click on the icon I wanted to change the appearance of.
- Click on Properties
- Click on the current icon button
- Now I see the window in the screenshot above
- Press the pencil button (as in the screenshot above, might be different for you)
- Go to the location of the image you want to use for the icon
- Then type the first part of the image's name in the location text box, and let autocomplete do the rest.
- Then just press Open and that image should set as the icon.

Hope that helped!

---

### Post by CinemaScope on 2010-04-11
Thanks very much -- I was able to follow that fully. Unfortunately, it still doesn't work -- the original default icon remains. Must be some other problem I have.

Thanks once again for your quick reply.

---

### Post by durand on 2010-04-11
Hmmm. How are you creating your shortcuts? I'm just dragging the drive icon from Computer to the desktop while holding down Ctrl and Shift. That creates a symlink. I can't see any reason why it isn't working for you.

---

### Post by CinemaScope on 2010-04-11
I created my folder shortcuts by right-button clicking the folder, choosing **Make link**, which appears in the same window as the folder, then dragging the link to the desktop. These shortcut links work, I just can't change the icon image for shortcuts to the second drive (changing shortcut icon images to the main drive are successful). I tried the method you mentioned above to create a link and the problem of changing the default icon image remains.

---

### Post by durand on 2010-04-12
That is really strange. You should post a bug about this at launchpad.net. Sorry I couldn't be of more help..

---

### Post by CinemaScope on 2010-04-12
Thanks for your help; great forum support. In this instance the problem has not been solved. I will upgrade to the latest Ubuntu next month, so perhaps maybe that will solve it? I'm going to be building a new computer and will try the 64-bit version for the first time and see what happens. Once again, thanks for your help.

---

### Post by durand on 2010-04-12
Hmm, you know, that could be the reason why it's working for me and not you. I'm running lucid, you're on karmic, I guess?

---

### Post by CinemaScope on 2010-04-13
Yes, I'm using Ubuntu 9.10 (32-bit version).

---

