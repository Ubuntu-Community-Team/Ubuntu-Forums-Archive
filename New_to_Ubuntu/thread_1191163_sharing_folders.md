---
title: "sharing folders"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by coops351 on 2009-06-18
right im pretty new to sharing on ubuntu. currently im running ubuntu 9.04 and all my music is saved on one my partitions. i have set up a network between my desktop pc (linux system) and my laptop (vista)

im wondering how do i mount folders into the share folder so that my vista system can access it?

much appreciated

luke

---

### Post by coops351 on 2009-06-18
right im pretty new to sharing on ubuntu. currently im running ubuntu 9.04 and all my music is saved on one my partitions. i have set up a network between my desktop pc (linux system) and my laptop (vista)

im wondering how do i mount folders into the share folder so that my vista system can access it?

much appreciated

luke

---

### Post by bodhi.zazen on 2009-06-18
Use Samba ;)

The graphical configuration should work out of the box.

Open nautilus, right click a directory -> share -> follow the instructions for samba =)

---

### Post by coops351 on 2009-06-18
how do you do that? sorry such a noob lol

---

### Post by coops351 on 2009-06-18
dont worry all sorted thanks for the help :)

---

### Post by bodhi.zazen on 2009-06-18
Sweet :)

Not too hard, even for a self proclaimed noob =)

---

### Post by coffeecat on 2009-06-18
Have you already set up a share folder in your home folder? If you have, you will have been prompted to install the bits of samba that don't come with a default install. So, assuming you have a share set up, all you have to do is to create symlinks in your share folder to the folders in the partition containing the music you want to share.

There are two ways of doing this: from the terminal and in the GUI. Without more information about your music partition I can't give you the exact terminal commands, but this is how you do it in the GUI.

Right-click on the music folder and select 'Make Link'. A symlink folder called 'Link to Music' (or whatever) will appear. Now drag and drop that into your share folder, and a second 'Link to Music' will appear in your share folder and you can access any files in it by double-clicking just as with the original folder. You can now delete the original link and rename the link in your share folder if you want. Repeat this for any other folders in that partition that you want to appear in your shared folder.

When you access your share folder in Vista, you should now be able to navigate into 'Music' in the normal way by double-clicking. Which is more than you can do the other way around. :p I once tried setting up a shortcut in Vista in a shared folder, but I couldn't navigate into it from another network machine. Windows! Tch! Pshaw! :wink: 

But if you haven't yet managed to set up a share folder in Ubuntu, post back with details of what you have done and someone will be able to help you.

---

### Post by swerdna on 2009-06-19
> **coops351 said:**
> right im pretty new to sharing on ubuntu. currently im running ubuntu 9.04 and all my music is saved on one my partitions. i have set up a network between my desktop pc (linux system) and my laptop (vista)

im wondering how do i mount folders into the share folder so that my vista system can access it?

much appreciated

luke
@coops351: it's really confusing for the responders when you double post the same question, especially if you solve the problem on thread #1 and leave it hanging on thread #2. I wouldn't be surprised if some folks got miffed.

---

### Post by coffeecat on 2009-06-19
> **swerdna said:**
> I wouldn't be surprised if some folks got miffed.

Agreed. Double-posting is very, very ill-mannered. Are you listening, coops351?

---

