---
title: "How do I make grub menu look cool? Lucid Lynx LTS"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by deckerry on 2011-04-30
I have been trying to figure out how to make my GRUB menu pretty for like at least 4 hours and I can't figure it out. Can somebody help?:confused:

---

### Post by drs305 on 2011-04-30
[COLOR="DarkRed"]Edit Added: See Post #24 for the solution for the Grub 1.98 version that is still in Lucid. The following will only work with the Grub 1.98 version in Maverick or later.[/COLOR]

Grub 2 themes are unfortunately still a work in progress; but you can still add a background image without too much difficulty.

Open /etc/default/grub as root:
```
gksu gedit /etc/default/grub
```

Add this line:
> GRUB_BACKGROUND="/mountpoint/image"
Example: GRUB_BACKGROUND="/home/myusername/Desktop/cool_image.png"

Save the file, then "sudo udpate-grub".

The image can be a .png, .tga, or 8-bit .jpg or .jpeg

You can also download some sample images with:
```
sudo apt-get install grub2-splashimages
```
These background images will be located in */usr/share/images/grub*

You can also change the font colors. I just finished writing a new guide for Grub 1.99. Although you can't just drop the image in /boot/grub like 1.99 allows, you can use the rest of the information to tweak your settings:
[http://ubuntuforums.org/showthread.php?t=1718521]("http://ubuntuforums.org/showthread.php?t=1718521")

If you want some advanced themes or much better theming, search these forums for BURG, a grub replacement.

---

### Post by deckerry on 2011-04-30
I edited default/grub and it looks like this ```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rootdelay=80"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

#GRUB_BACKGROUND="/usr/share/images/grub/Plasma-lamp.tga
```

Then I saved and closed that file and used this: 
```
sudo update-grub
```

Here's the output
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda3
done

```

I rebooted and got the same old ugly plain black and white GRUB menu.

---

### Post by Hedgehog1 on 2011-04-30
One of the weirdnesses with grub and background images is that some just don't work.  I did this with the next version of grub (the one that shipped with 10.10), and found that I had to make a smaller image (640x480) before I got the picture to show.

Of course, then I couldn't read the menu, but that was because I made a poor artist selection of the image.  Paisley backgrounds just do not work on grub menus.  **Trust me on this...**


***The Hedge***

:KS

---

### Post by deckerry on 2011-04-30
I tried a different image, which I made sure was 640x480. It was png. It didn't work either. Are my codes wrong or something?

Is the # sign required? Are the parenthesis required? Am I missing something? Am I editing the wrong text file?

---

### Post by deckerry on 2011-04-30
-deleted-

---

### Post by JOHNNYG713 on 2011-04-30
Grub customizer ! [https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

---

### Post by Kal Sho on 2011-04-30
Take the "#" out. Having a # at the beginning of the line makes it a comment.

edit: Also, the image has to be 14 colors (or is it 16 max? either way 14 will work).

---

### Post by deckerry on 2011-05-01
I tried it without the # sign. Didn't work.

---

### Post by Kal Sho on 2011-05-01
See my edit above, and make sure you close your quotes.

---

### Post by deckerry on 2011-05-01
Here's what I changed it to:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rootdelay=80"
GRUB_CMDLINE_LINUX=""
GRUB_BACKGROUND="/home/downloads/grub1.png"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

The image is 640x480 and indexed to 14 colors.

Still, no luck.

---

### Post by drs305 on 2011-05-01
A couple of things:

Is the image actually in /home/downloads ? Is this a folder you made, outside your own /home folder. Your default folder would be /home/username and the default Downloads folder for you would be /home/username/Downloads.

Save the file and update-grub if you make any changes.

You can see if update-grub found the image in the terminal returns when you run update-grub. If it soesn't generate a "Found image" message you don't have the correct path. 

If you do get the message saying it found the image, and it still doesn't display, then it is probably an image problem.

As mentioned, Grub Customizer can also help. I have a guide for it. See "Customizer" in my signature line.

---

### Post by Kal Sho on 2011-05-01
> **deckerry said:**
> 
GRUB_BACKGROUND="/home/downloads/grub1.png"


Just because I'm running out of ideas: Are you sure that path is correct? Case matters also.

---

### Post by pastalavista on 2011-05-01
Where you have [GRUB_BACKGROUND="/home/downloads/grub1.png"] probably should be [GRUB_BACKGROUND="/home/<your user name>/Downloads/grub1.png"]

---

### Post by Rasa1111 on 2011-05-01
yeah if the image is in your 'default' downloads folder, you have to use a Big D, a small d won't work.

---

### Post by deckerry on 2011-05-01
From the beginning here it is.
First
```

ryan@ryan-laptop:~$ gksu gedit /etc/default/grub

```

Second
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rootdelay=80"
GRUB_CMDLINE_LINUX=""
GRUB_BACKGROUND="/home/ryan/Downloads/grub1.png"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Third
```

ryan@ryan-laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda3
done
ryan@ryan-laptop:~$ 

```

I have also attached a screenshot to show which directory the image is in.

After all this, still no luck.

---

### Post by deckerry on 2011-05-01
I feel like I'm beating a dead horse by trying the "edit the grub text file" method. I think I'll try the "customizer" unless anybody has any other ideas.

---

### Post by drs305 on 2011-05-01
> **deckerry said:**
> I feel like I'm beating a dead horse by trying the "edit the grub text file" method. I think I'll try the "customizer" unless anybody has any other ideas.

The command still isn't finding the image, but I was about to recommend Grub Customizer when I read your post.

---

### Post by deckerry on 2011-05-01
I installed the customizer. It doesn't look the same - probably 'cause i've messed with my themes and stuff. But, more importantly, I tried to change the appearance and rebooted and ...

nothing. :(

Sometimes, I truly feel like computers hate me.

---

### Post by Kal Sho on 2011-05-01
I'd suggest trying a different image.

[This one]("http://i339.photobucket.com/albums/n454/betorscreens/grub-splash.jpg") is the one I use.

If it works, you know where the problem is.

---

### Post by deckerry on 2011-05-01
That's a beautiful picture. I converted it to a 14 color png and used the grub customizer to apply it under the appearance tab. Then I used "sudo update-grub", rebooted, and still nothing.

---

### Post by Kal Sho on 2011-05-01
OK. Now try it without converting it. It works as-is just fine for me.

---

### Post by deckerry on 2011-05-01
IT WORKS IT WORKS IT WORKS
I DON'T KNOW WHY, BUT IT WORKS!!!!!!

Thank you
drs305 and Kal Sho!!

You guys rock!!!!!!

Thanks everybody else too!

---

### Post by drs305 on 2011-05-02
> **deckerry said:**
> IT WORKS IT WORKS IT WORKS

I know you already solved this using Grub Customizer but I feel I need to correct things for archival reasons.

I was keying on Grub 1.98, but not Lucid. There are two versions of Grub 1.98, the one in Lucid and the one in Maverick. The GRUB_BACKGROUND= setting in /etc/default/grub works in the Grub 1.98 version in Maverick but not in Lucid's. 

In Lucid, the background image is controlled by the WALLPAPER= line in /etc/grub.d/05_debian_theme. So that is the line you would edit/modify with the path and image filename. The current line is:
>   WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"

Since you are using Grub Customizer I would stick with it. Should you ever uninstall it and return to the normal Grub files, this is how you would get your background image in Lucid.

---

