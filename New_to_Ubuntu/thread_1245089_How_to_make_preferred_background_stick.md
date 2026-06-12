---
title: "How to make preferred background stick?"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by kenmac2 on 2009-08-20
Hi,
I can change the background to a preferred picture, but it doesn't stay that way.
When I reboot, the new file isn't there anymore, just the originals.
Is there a trick to saving the preferred setup?

kenmac2

SOLVED

---

### Post by Penguin Guy on 2009-08-20
Are you deleting or moving the picture after you've used it as a background?

---

### Post by Cheezespread on 2009-08-20
Two questions :
1. Have you installed Ubuntu or are you mentioning a live CD ? (though you mentioned you are rebooting - Just confirming )
2. Have you moved the wallpaper from its location after you made it your wallpaper ?

---

### Post by kenmac2 on 2009-08-20
This is a standard Ubuntu installation. (dual boot)
The picture file is still in its original folder.
There is no sign of the preferred file in the background list after a reboot.

kenmac2

---

### Post by Cheesemill on 2009-08-20
Is the picture on an NTFS drive by any chance?
 
If so does the drive automatically mount on startup or do you have to click on it in the Places menu first?

---

### Post by kenmac2 on 2009-08-20
Yes, it's an NTFS drive, and it is read OK by Ubuntu.
I located the file OK with the Browse function and it does load/display it OK.
It's just not listed as a background after a reboot.

kenmac2

---

### Post by mimor on 2009-08-20
make sure the disk is auto-mounted in /etc/fstab

---

### Post by Cheezespread on 2009-08-20
Is the drive automounted when you login or mount it on your own ?. As in is there an entry for the same in the /etc/fstab file ?

Else you can always copy the picture to your needed directory inside Ubuntu ; prefferably where you remember like the Documents folder. Try changing the background now. Should work.

---

### Post by kenmac2 on 2009-08-20
It's not listed in the /fstab (only CD-Rom and Floppy listed there).
However, it is listed in the Places menu and when it is clicked on, it offers the Unmount option.
I haven't done any manual mounting of a Drive.
I'll try copying the file into Ubuntu as you suggested.

kenmac2

---

### Post by kenmac2 on 2009-08-20
OK, I copied the file into the Ubuntu Pictures folder and used that, and that has fixed it.
Thanks for you help.

kenmac2

---

### Post by tarps87 on 2009-08-20
Just a quick note, when you click the icon in the places menu it mounts the drive, to auto mount it on boot you will need to add it to fstab

---

### Post by Bartender on 2009-08-20
Wallpaper is stored in a folder named /usr/share/backgrounds.

I think this might be a fun practice session for those folks who have managed to avoid the terminal.  I count myself as one of that group... 

First part of this does NOT involve the terminal.  Go to Places>Computer>Filesystem, then find the usr folder, click on that, find the share folder, click on that, then find the backgrounds folder.  Inside backgrounds folder are some wallpapers you didn't know about.  On my jaunty installation there are about a half dozen pictures that look like they were taken from the International Space Station (?).

If you've found some wallpapers you like, you can certainly keep them in Pictures or some other folder in /home, and that works.  But it would be cooler to keep them in the usr/share/backgrounds folder.

I think the easiest thing to do would be this:

You have a wallpaper you want to save.  Put a copy on the desktop.  Give it a short, simple name with no spaces.  In other words, not "pic 3.png" but "pic3.png".  I used .png as an example.  Wallpaper is probably going to be a .png or .jpg file, I don't think Linux is very fussy about what kind of image file you want to use.

First command in terminal:

```
cd Desktop
``` and hit the Enter key

What you did was told Linux to look at the desktop.

next command:

```
sudo cp pic3.png /usr/share/backgrounds
```

Hit Enter key

You'll enter your password, and then it'll seem like nothing happened.  That's what you want!  

You could either move the file or copy the file.  "cp" is copy command, which might feel safer to someone who's not sure what they're doing.  I don't know about you, but I always get confused about spaces.  The above command has 3 spaces:

sudo [COLOR="Red"]space[/COLOR] cp [COLOR="Red"]space[/COLOR] pic3.png [COLOR="Red"]space[/COLOR] /usr/share/backgrounds

I'm not good with the terminal, so there are probably more elegant ways to do this, but the above works.

Let's say you want to get rid of pic3.png from the "backgrounds" folder.

Back to terminal

```
cd /usr/share/backgrounds
```

Hit Enter key

```
sudo rm pic3.png
```

Enter key again

Enter password at prompt, hit Enter, the deed is done.  If you have the backgrounds folder up in your file browser you can watch the file disappear.  "rm" means "remove".

The above is a perfect example of how Linux doesn't allow just anyone to flail around inside your system.  If you try to remove pic3.jpg with this command:

```
rm pic3.png
``` 

the system will refuse.  You did not log in as "sudo" and enter your password.  

In Windows, anyone can run amok within the file system.  In Linux, you need to provide the proper authorizations just to get rid of a wallpaper file.

Back at the Linux desktop, right-click, click on "Change Desktop Background", click on "Add", then browse to FileSystem, usr, share, background and find pic3.png.  Double-click and you've got your new wallpaper up.

---

