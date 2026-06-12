---
title: "What is this and how do I get it"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by mishathegoat on 2009-02-14
Hello everyone,
I've been seeing this kind of terminal mixed with bitmaps etc. I have no clue what it is.. does anyone else know?

---

### Post by cerealtx on 2009-02-14
> **mishathegoat said:**
> Hello everyone,
I've been seeing this kind of terminal mixed with bitmaps etc. I have no clue what it is.. does anyone else know?

im asuming your talking about lunar linux?? google is awesome btw
[http://www.lunar-linux.org/](http://www.lunar-linux.org/)

---

### Post by Captain_tux on 2009-02-14
> **cerealtx said:**
> im asuming your talking about lunar linux?? Google is awesome btw

+1

---

### Post by mishathegoat on 2009-02-14
...Uh... okay. I know what *linux distro* the logo is from. And believe me, Google is my *best* friend. However, this application is not called "Lunar Linux".. Lunar Linux is an *operating system*. This application is a terminal emulator (I'm guessing)... such as gnome-terminal, konsole, or aterm.

Bump.

---

### Post by m_duck on 2009-02-14
It could just be a terminal window with a thin window border on the top and left sides, shadows on the bottom and right hand edges, with the lunar linux logo as part of the desktop wallpaper?

---

### Post by mishathegoat on 2009-02-14
Thanks for the quick response. Good theory, I guess that it is possible.. 

However, if you look here at this other screenshot, you can see that it isn't enclosed in window borders. And the picture on the right is strategically placed.

Any other ideas? I appreciate your help..

---

### Post by niteshifter on 2009-02-15
Hi,

I'm almost certain the first is a tricked-out (via compiz / fusion / beryl) Dark Looks theme. I used to run one similar to it.

---

### Post by MarblePanther on 2009-02-15
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
> It might be vte:
[http://inz.fi/blog/wp-content/uploads/2008/01/vte-black.jpg](http://inz.fi/blog/wp-content/uploads/2008/01/vte-black.jpg)
Closest thing I've found

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
EDIT: nevermind, vte isn't a terminal, hehe   my mistake

---

### Post by mishathegoat on 2009-02-15
I appreciate your guys' quick responses.. But I'm certain that these aren't Compiz/etc themes. I found these screenshots under "Screenshots" in the main page of lunarlinux.org. The only caption they have is "Console".

---

### Post by MarblePanther on 2009-02-15
If I had to guess, I would say they are using the e17 desktop.

It usually has strange/cool themes like that
[http://origin.arstechnica.com/articles/columns/linux/linux-20061018.media/evol.jpg](http://origin.arstechnica.com/articles/columns/linux/linux-20061018.media/evol.jpg)

---

### Post by mishathegoat on 2009-02-15
That could also be possible... I still haven't found anything

I'm tempted to try and post on Lunar Linux's forum.. But its not very active..

---

### Post by epswinde on 2009-02-15
Ok, so I was looking through those photos, and in the description of them they say that their window manager/desktop environment is called FrameBuffer -- i think that they've just hacked their virtual terminals (press ctrl+alt+F1 to get to a virtual terminal.  ctrl+alt+F7 gets back to X)

no idea how it's done though.

[more info]("http://en.wikipedia.org/wiki/Linux_framebuffer")

---

### Post by ibuclaw on 2009-02-15
It just looks like an Xserver with a lightweight window manager ontop to me.

Backtrack do a similar thing. I'm just getting it now to run in a VM.

[EDIT]
I lie :)
Text Mode with Framebuffer it is indeed.

I'll just have a poke round the /etc config  files.

Regards
Iain

---

### Post by Crafty Kisses on 2009-02-15
He might be using Tilda.

---

### Post by mishathegoat on 2009-02-15
I've done some more searching and found "fbcon" (framebuffer console). I think that's what its called... I dunno I may be wrong.

I have a feeling you guys are closer to finding the answer than I am. (Thx again btw)

EDIT: I'm also 99% sure that it *is not* a window on top a desktop. From other screen shots I've seen, I can say this with confidence. None of these "borderless windows" have a min/max/x button. If you look at the lunar-linux website, the screenshots are taken from "Console Mode". That is another reason why I'm sure its not a borderless window.

---

### Post by ibuclaw on 2009-02-16
This is what I've done so far:

Firstly:
Check that you have a framebuffer device in /dev
```
ls -d /dev/fb*
```
If you get an error back saying "**ls: cannot access /dev/fb*: No such file or directory**", and I got that, so I created a udev rule for it.
```
sudo gedit /etc/udev/rules.d/50-fbdev.rules
```
and put this inside:
```
# fb devices
KERNEL=="fb[0-9]*", NAME="fb/%n", SYMLINK+="%k", GROUP="video"
```
Save and Quit.

Next, so that the framebuffer device is initiated on startup, edit the initramfs modules
```
sudo gedit /etc/initramfs-tools/modules
```
and add to the bottom the name of the framebuffer module that suits your graphics card.
Mine is an nvidia, so I used **nvidiafb**, but vesafb is the generic default (I think).
[PHP]
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
nvidiafb
[/PHP]
Now backup your initrd file.
```
sudo cp /boot/initrd.img-$(uname -r) /boot/initrd.img-$(uname -r)-save
```
and update-initramfs
```
sudo update-initramfs -k all -u
```
Next, edit the grub menu.lst
```
sudo gedit /boot/grub/menu.lst
```
find the **kernel** line of the Ubuntu boot stanza:
```

title           Ubuntu 8.10, kernel 2.6.27-11-generic
root            (hd1,0)
**kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=04b3b3b7-ce39-46b0-872f-36eef8e4ef59 ro quiet splash**
initrd          /boot/initrd.img-2.6.27-11-generic
quiet

```
And add "**vga=**" to the end of it
```
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=04b3b3b7-ce39-46b0-872f-36eef8e4ef59 ro quiet splash **vba=31B**
```
I used 31B, but you can choose to use whatever fits your monitor fine.

*NOTE*
You can set it to **vga=ask** and you will be asked what type of resolution you want on startup instead, so you can see all options, and choose the one that best fits.

After making these changes, I ran update-grub
```
sudo update-grub
```
Now reboot, and you should now have a framebuffer device in /dev
This is what mine looks like
[PHP]
$ ls -d /dev/fb*
/dev/fb  /dev/fb0
[/PHP]
Now, to give it a test, install a framebuffer application
```
sudo apt-get install fbi
```
then switch to a VT (ie: Ctrl+Alt+F1) and login.
Now run this to see a picture of the Ubuntu wallpaper in your console.
```
fbi /usr/share/backgrounds/warty-final-ubuntu.png
```
If your console screen resolution is < 1024x768 and you have < 16 colours set on the console (as you chose in the vga= option), then it may not the prettiest of things to look at.

For setting up the console so it has a picture background, I will have to have a play about to see if I can get something setup.

After having a few looks around, this application seems to be a step in the right direction
```
sudo apt-get install fbset
```
But I will post more, if I can setup any of the VTs to have a background image.

Happy hacking!

[UPDATE]
Look at what I've found:
```
cat /etc/modprobe.d/blacklist-framebuffer
```
intriguing ...
> 
# Framebuffer drivers are generally buggy and poorly-supported, and cause
# suspend failures, kernel panics and general mayhem.  For this reason we
# never load them automatically.



Regards
Iain

---

### Post by ibuclaw on 2009-02-17
OK, I've given up on trying to see if I can use framebuffer to get anything working.

What I have instead found is this little trick.

```
sudo gedit /etc/X11/Xwrapper.config
```
and change the line that says "**allowed_users=console** to this
```
allowed_users=anybody
```
I Installed **feh** to control my background and **terminator** for my console emulator (though you can use any terminal you like).
```
sudo apt-get install feh terminator
```
and finally create an .xinitrc file in your home directory
```
gedit ${HOME}/.xinitrc
```
This is what my config file looks like.
```

feh --bg-scale /home/iain/Pictures/ubuntu.tattoo_1280x1024.jpg &
terminator -b --geometry=1280x800+0+0

```
Once that is done, press Alt+F2 or open a terminal and run this
```
startx -- :1 vt12
```
and a new minimalist Xsession will be created for you.

you can change what number xserver it is on, and you can change which virtual terminal you want it to reside on.
In the example, I chose Xscreen 1 (**:1**) and vt12.

[EDIT]
Attached to this post is a picture of what I've setup.


Anyways, enjoy.

Regards
Iain

---

### Post by mishathegoat on 2009-02-18
Very cool that's exactly what I was looking for I appreciate all the work you put into this

[B][EDIT - 3 Years Later]

Finally found out exactly what it was. It is "fbcondecor"/"fbsplash"[/B]

---

