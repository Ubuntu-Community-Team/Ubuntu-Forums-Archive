---
title: "Add shutdown icon to Gnome Panel"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by MeisterDave on 2009-06-02
Hi there, I just installed Ubuntu 9.04 and now I'm trying to customize the Gnome Panel. What I'm trying to achieve is: I want to add an icon to that bar which shuts down the computer at once. How do I do that???

If I right-click on the panel and choose "Add to panel..." I can add a shutdown icon, but that button opens another window which lets me choose whether to shut down or restart the computer. That's not what I want. I'd also like to change the icon to this red button with the white circle in it. (The one that is used for the "logoff" button by default.) I hope you can help me with that, since I'm scouring Google for an answer for about an hour now... and I'm quite desperate... ;) Thanks in advance.

---

### Post by MichaelSammels on 2009-06-02
Right click the panel, and then "Add to Panel"

Search for "Shut Down" and drag it to your panel.

---

### Post by steeleyuk on 2009-06-02
You probably won't get something like that by default, you'd have to make your own. It'd be a bit of a pain if a user added a button to their panel, and then accidentally hit it while doing something.

---

### Post by MeisterDave on 2009-06-02
Ok, I can accept that it cannot be done easily. However, I'd still like to change the icon. Can you help me with that? I'd like to have that red logoff icon instead of the default gray one. Neither can I find the corresponding file, nor can I figure out how to change the image. Why is that so complicated? When I add a custom application launcher to the panel, he lets me choose an icon. :(

---

### Post by steeleyuk on 2009-06-02
You'd probably need to go through the source, or at least find the filename of the icon to be able to change it.

Or, you could try another icon set.

---

### Post by binbash on 2009-06-02
add a custom application launcher to the panel and for command write this : 

shutdown -rh now

HOWEVER you may need to deal with sudoers to get the permissions for shutdown command.

---

### Post by philinux on 2009-06-02
There is a really nice shutdown icon in this set. Dark gradient red.
[http://ubuntuforums.org/showthread.php?t=1108045](http://ubuntuforums.org/showthread.php?t=1108045)

---

