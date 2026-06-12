---
title: "Change the order of operating systems"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by 7azem on 2010-07-27
Hi!
i have both Ubuntu and windows on my Netbook, but every time i boot the first OS option is always Ubuntu, I want to change that to become windows again! is that possible!? and how to do it!?
thanks a lot! :)

---

### Post by VH-BIL on 2010-07-27
try installing startup-manager from synaptic and set the default os to windows.

---

### Post by wojox on 2010-07-27
> **VH-BIL said:**
> try installing startup-manager from synaptic and set the default os to windows.

Definitely the easiest way.

---

### Post by 7azem on 2010-07-27
well can u then give me a link to download this start-up manager please!

and how to do it! i'm really a noob in such stuff! :S

thanks a lot! :)

---

### Post by WRDN on 2010-07-27
It's in the repositories, so you can install it from there. Open the Terminal by clicking Applications > Accessories > Terminal (in GNOME), or press Alt+F2 and type "gnome-terminal". Then type:

```
sudo apt-get install startupmanager
```

---

### Post by LowSky on 2010-07-27
Or go to System>Administration>Synaptic

search for start-up manager and install it from there

or go to Applications>Ubuntu>software center

search for start-up manager and install it from there

OR go here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
search for startupmanager and download this file: [http://mirrors.kernel.org/ubuntu/pool/universe/s/startupmanager/startupmanager_1.9.13-4ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/s/startupmanager/startupmanager_1.9.13-4ubuntu1_all.deb) then install it

Ubuntu has so many ways of doing one task

---

### Post by WRDN on 2010-07-27
> **LowSky said:**
> 
*snip*
OR go here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
search for startupmanager and download this file: [http://mirrors.kernel.org/ubuntu/pool/universe/s/startupmanager/startupmanager_1.9.13-4ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/s/startupmanager/startupmanager_1.9.13-4ubuntu1_all.deb) then install it

Ubuntu has so many ways of doing one task

Doesn't this prevent updates being retrieved by apt for the package?

---

### Post by Krabby.Linux on 2010-07-27
I like GRUB :-) You can edit menu.lst if you want to.

---

### Post by philinux on 2010-07-27
> **7azem said:**
> well can u then give me a link to download this start-up manager please!

and how to do it! i'm really a noob in such stuff! :S

thanks a lot! :)

Easy way.

In firefox address bar type apt:startupmanager and hit the enter key.

The menu entry will be in Admin section.

---

### Post by Deersindal on 2010-07-27
**Applications>Ubuntu Software Center**

Type in "startup-manager" and select the application and click install.

**Then go to System>Administration>StartUp-Manager**

Enter your password and the second drop-down menu on the "Boot options" tab is the default operating system.

I know you're dying to make memtest the default ;)

---

### Post by Cavsfan on 2010-07-27
"gksu gedit /etc/default/grub" (without the quotes)

Change this "GRUB_DEFAULT=0" to the number you want.
It starts 0,1,2,3 etc.
I have mine set to 2 for Windows 7 as the default (which is the 3rd one down).

Just make sure you enter "sudo update-grub" or "sudo update-grub2" (either)
or the changes will not "take".

---

### Post by uRock on 2010-07-27
It is nice to see a command line method. Every time I install and use startupmanager it distorts the splash screens and is irreversible.

---

### Post by philinux on 2010-07-27
> **uRock said:**
> It is nice to see a command line method. Every time I install and use startupmanager it distorts the splash screens and is irreversible.

Thats ok but what happens after a new kernel gets installed.

I've no need for SUM as I'm all linux.

---

### Post by uRock on 2010-07-27
> **philinux said:**
> Thats ok but what happens after a new kernel gets installed.

I've no need for SUM as I'm all linux.
I don't know what it does when a new kernel is installed. When I recently installed and used it, I only changed the grub screen resolution.

In the future I will use nothing but commands to make the changes.

---

### Post by anglican on 2010-07-27
> **philinux said:**
> Thats ok but what happens after a new kernel gets installed.

I've no need for SUM as I'm all linux.
You can also set GRUB_DEFAULT to the name of the OS you want as default e.g.:

```
GRUB_DEFAULT="Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic"
then
sudo update-grub
```That way if you install a new kernel, your default remains unchanged. It's one of the nice new features of grub2 ;)

H

---

### Post by philinux on 2010-07-27
> **anglican said:**
> You can also set GRUB_DEFAULT to the name of the OS you want as default e.g.:

```
GRUB_DEFAULT="Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic"
then
sudo update-grub
```That way if you install a new kernel, your default remains unchanged. It's one of the nice new features of grub2 ;)

H

Yeh thats a better solution for a dual boot windows user who wants win first.

---

### Post by Cavsfan on 2010-07-27
> **philinux said:**
> Thats ok but what happens after a new kernel gets installed.

I've no need for SUM as I'm all linux.

The new kernel just gets added at the bottom and does not affect the default OS.

However there is a way to fix grub permanently so that only whatever you want to appear on the grub menu does
and it is maintenance free.
Mine displays this only:

[COLOR="Blue"]Ubuntu Lucid Lynx 10.04
Ubuntu Lucid Lynx 10.04 Safe Mode
Windows 7[/COLOR]

The default with a 60 second timeout is set to 2 (Windows 7).
And that is it. When a kernel is added, my menu does not change.

---

### Post by Cavsfan on 2010-07-27
This is also on a pretty nice 1920x1200x32 picture. The whole menu is maintenance free.
It does not ever change from the 3 blue lines above unless I want it to.

---

### Post by Don1500 on 2010-07-27
If you are using Grub2. Everytime you get a new kernel the boot will still load the (X) number OS. 

Windows is loaded after all the Ubuntu Kernels and memory tests. Soooo it will screw up your load options. After a new kernel and the system does an "Update-grub" Most likely it will load a Memory test as default.

Unless this was fixed in some revision of Grub2 that I don't know about.

---

### Post by Cavsfan on 2010-07-27
> **Don1500 said:**
> If you are using Grub2. Everytime you get a new kernel the boot will still load the (X) number OS. 

Windows is loaded after all the Ubuntu Kernels and memory tests. Soooo it will screw up your load options. After a new kernel and the system does an "Update-grub" Most likely it will load a Memory test as default.

Unless this was fixed in some revision of Grub2 that I don't know about.

I have a custom Grub and it is setup so that it does not change at all period.
There can be 3 kernels come through update and my 1st option as shown on my first post will load the most recent kernel.
It is totally maintenance free. I don't even have Memtest display, just the 3 lines.
And what text those 3 lines display is set by me too.
I can let you know how if you want.

---

### Post by Cavsfan on 2010-07-27
I used to have to edit the default line every time a kernel was added, but not anymore.
Totally maintenance free and it's nice with a dual boot system! :D

---

### Post by uRock on 2010-07-27
> **Cavsfan said:**
> I used to have to edit the default line every time a kernel was added, but not anymore.
Totally maintenance free and it's nice with a dual boot system! :D

On the recent Grub update did you stay with the old version or upgrade to the maintainer's version?

---

### Post by Cavsfan on 2010-07-27
> **uRock said:**
> On the recent Grub update did you stay with the old version or upgrade to the maintainer's version?

I did the side by side comparison and then ending up taking the new version. Just had to make one change I think and it was good to go.
I have one custom file in the grub mix that has the 3 entries I want and the rest do not appear as they are set to non-executable.

---

### Post by Cavsfan on 2010-07-27
> **philinux said:**
> Thats ok but what happens after a new kernel gets installed.

I've no need for SUM as I'm all linux.

Phil, this would even help you. You could have just a line for Lucid and a line for Lucid (Recovery Mode).
2 lines that you never have to touch again period.
When ever a new kernel comes down the pipes, the 1st option will always load the newest kernel.

**Ranch Hand** showed me how to do this a while back and you know he knows his stuff.
I have never had a single problem with it.

---

### Post by federer_reddevil on 2011-01-13
how can I change the order in which it appears on bootin

I already have set windows as default in ubuntu 10.10 but how can I move it to the top

---

### Post by Cavsfan on 2011-01-13
> **federer_reddevil said:**
> how can I change the order in which it appears on bootin

I already have set windows as default in ubuntu 10.10 but how can I move it to the top

  Edit this file with this command **gksu gedit /etc/default/grub**
Set this to zero **GRUB_DEFAULT=0**.
The numbering starts 0,1,2,3 etc.
Then always do **sudo update-grub** to make the changes stick.

If you went by the tutorial in my signature, you would also need to edit **gksu gedit /etc/grub.d/06_custom** 
and put the windows entry at the top instead the bottom as in my tutorial. It is the box in Step 4.

And after any change to grub2 do **sudo update-grub**.

---

### Post by federer_reddevil on 2011-08-21
sorry for taking so long to reply but i kind of forgot where i posted and only today managed to figure it out it worked thank you

> **Cavsfan said:**
> Edit this file with this command **gksu gedit /etc/default/grub**
Set this to zero **GRUB_DEFAULT=0**.
The numbering starts 0,1,2,3 etc.
Then always do **sudo update-grub** to make the changes stick.

If you went by the tutorial in my signature, you would also need to edit **gksu gedit /etc/grub.d/06_custom** 
and put the windows entry at the top instead the bottom as in my tutorial. It is the box in Step 4.

And after any change to grub2 do **sudo update-grub**.

i did as you said in tutorial and moved it to the top but after the 3 (windows,ubuntu and ubuntu recovery) the old 5 are still down the list how to remove them from list and only keep the first 3

---

### Post by Cavsfan on 2011-08-23
> **federer_reddevil said:**
> sorry for taking so long to reply but i kind of forgot where i posted and only today managed to figure it out it worked thank you



i did as you said in tutorial and moved it to the top but after the 3 (windows,ubuntu and ubuntu recovery) the old 5 are still down the list how to remove them from list and only keep the first 3


To just have the custom entries displayed, enter **sudo chmod -x /etc/grub.d/10_linux && sudo update-grub**.
This will make the bottom 5 not show up. Keep in mind that the most recently installed kernel will run when you select **Ubuntu**. not the highest numbered kernel.

This is from step 6 in my tutorial.

When you enter **sudo update-grub** You should see only the image name you are using for your background.
Then only your custom entries will display.

Keep in mind if you run into trouble and need to access other kernels, just enter **sudo chmod +x /etc/grub.d/10_linux && sudo update-grub**. 
(+x makes it executable, -x makes it unexecutable.

---

### Post by anewguy on 2011-08-23
> **Krabby.Linux said:**
> I like GRUB :-) You can edit menu.lst if you want to.  

Doesn't apply when using grub2.

---

