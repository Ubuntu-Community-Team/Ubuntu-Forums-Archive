---
title: "Help needed to customize XFCE"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by rvgsd on 2009-07-12
Hi all..! XFCE is cool..but I am having some problems and would be glad if someone can answer:

1) I downloaded some xfce mouse themes and extracted them into the **/usr/share/icons/ **folder, where they are contained in the **cursors** sub folder. I can see them now in the mouse settings, and i can also select them. But when I hover over a title bar or the panel, or similar it changes back to the default pointer, if i move it back in open area then it goes back to the themed pointer. How I can prevent this?

2) Is there any way to stop highlighting folders when I hover over them in thunar, or on desktop?

3) Is there any way to disable shadows under mouse pointers and similar?

Thanks for help!

---

### Post by rvgsd on 2009-07-13
Bump.!

---

### Post by kerry_s on 2009-07-13
1. logout and back in

2. i don't think so

3. use a theme without shadows, there images so the shadows are in the image/pic.

---

### Post by rvgsd on 2009-07-13
I already tried restarting the system! that does not work! any more ideas?

---

### Post by kerry_s on 2009-07-13
> **rvgsd said:**
> I already tried restarting the system! that does not work! any more ideas?

point me to the theme let me check it out, it could be defective or just broken. might even be you just got a bad download.

also always extract them as your user, then copy them where you want. you never know whats packed inside things, so don't extract as root.

---

### Post by rvgsd on 2009-07-13
Thanks for helping! 
here is the link:
[http://www.xfce-look.org/content/show.php/ComixCursors?content=32627](http://www.xfce-look.org/content/show.php/ComixCursors?content=32627)
Any cursor set from here.
These cursors are also available through synaptic, but i have the same problem even after installing through synaptic.
I extracted them as a normal user, but moved them into the /usr/share/icons as root.

---

### Post by kerry_s on 2009-07-13
works fine for me, i just put it in my ~/.icons to test, logged out & back in.

---

### Post by rvgsd on 2009-07-13
wow, it doesn't work for me! do you have any ideas why it might not be working for me?
Also may I ask how did you take screenshot with the mouse pointer in?

---

### Post by kerry_s on 2009-07-13
> **rvgsd said:**
> wow, it doesn't work for me! do you have any ideas why it might not be working for me?
Also may I ask how did you take screenshot with the mouse pointer in?

nope, are you using xubuntu or just xfce4on top of something else?

the xfce4-screenshooter offers that option. i have it set to my print key.

---

### Post by rvgsd on 2009-07-13
Yeah..I am using Xubuntu 8.04. 
The screenshot plugin doesnt allow me to do so.

---

### Post by rvgsd on 2009-07-13
Screenshot of the plugin properties attached...

---

### Post by rvgsd on 2009-07-13
After searching on the internet again and agian, I found that this problem is a bug that has been reported. 
[https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/157447](https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/157447)
I guess i'll have to live with it!
Thanks for your help!

---

### Post by kerry_s on 2009-07-13
that looks like the old version, what xfce4 version is 8.04 using ?

i'm using debian testing xfce4.

---

### Post by kerry_s on 2009-07-14
alright try this, in **/usr/share/icons** create a folder named "**default**"
in there create a file called "**index.theme**" in that put:

```
[Icon Theme]
Inherits=your-theme

```

that should set your chosen theme as the system default, so if it does use the system it will still be the same theme your using.

---

### Post by rvgsd on 2009-07-14
Hey, the default folder already exists and also the index.theme file. I already had modified the 'inherits' entry yesterday and it didn't work. But I forgot that I had renamed the folder from comix to Comix :) I changed it!
Also there was this other entry 'GenericName'. I put the same value for it.
(I dont know if modifying this entry is necessary or not.) **But now it works!!** I have a consistent mouse pointer! Here's how my index.theme looks like:

```

[Icon Theme]
Inherits=Comix

[Desktop Entry]
GenericName=Comix

```

super! **Thanks** for your help man!
I am gonna post this workaround in the launchpad bugs thingy..hope it helps some other people out there.

---

