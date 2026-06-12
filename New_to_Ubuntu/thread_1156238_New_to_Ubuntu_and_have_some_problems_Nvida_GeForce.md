---
title: "New to Ubuntu and have some problems: Nvida GeForce 8800GT"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by pachiko-ichiro on 2009-05-11
Hello everyone,

I am new to Ubuntu..  I just did a fresh install of the new 9.04(jaunty) OS.
Intel(R) Core2 Duo CPU
Nvida GeForce 8800GT

I have had some problems already.. .

I installed the drivers using the terminal. 
Now when ever I have the option for a more graphical desktop, many things stop working. 

For example Pidgin.. It will start but it will comepletely freeze forcing me to restart the computer. 

Another example is firefox... When I type in the search box and press enter nothing will happen. This also includes the address bar. However, if I go to desktop setting /visual settings and change it to very basic these problems go away. 

Any ideas?

---

### Post by bapoumba on 2009-05-11
I've added some infos to the title.

---

### Post by AndThenWhat on 2009-05-11
Okay, firstly I think you should try installing nVidia drivers using the Hardware Drivers app.  Go to (System -> Administration -> Hardware Drivers).

If nothing shows up then you may have more look switching to a kernel that supports your video card.

---

### Post by Jazzy_Jeff on 2009-05-11
> **AndThenWhat said:**
> Okay, firstly I think you should try installing nVidia drivers using the Hardware Drivers app.  Go to (System -> Administration -> Hardware Drivers).

If nothing shows up then you may have more look switching to a kernel that supports your video card.

There is nothing wrong with the support for this video card. I am using it without a problem. Try to reinstall with the information posted from AndThenWhat.

---

### Post by AndThenWhat on 2009-05-11
I also found an alternative method that people have had success with installing your graphics card:

Open Synaptic Package Manager (System -> Administration -> Synaptic Package Manager) then:

1. type "envyng" into the Quick Search box
2. Check the list item "envyng-qt" (Mark for installation)
3. Click the Apply button at the top

Then the EnvyNG program should be installed which will help you install your video card driver, look under the Applications or System menus.

---

### Post by pachiko-ichiro on 2009-05-13
Idid the last, and it failed. It said I didn't have enough disk space. 

However I have this Distro on a 1t hard drive and it is shared with OpenSuse.

Opensuse was installed first. 

How do I make it have more disk space, I know there is 445g free.

---

