---
title: "dual boot; why does Grub list five different versions of Ubuntu?"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by the big e on 2011-02-15
I have a dual boot, with Windows Vista and Ubuntu on a Think Pad T500.
One thing that puzzles me is when I turn it on and get the boot menu, it lists five different numbered versions of Ubuntu, along with their respective recovery modes, instead of just one. 

What is happening here? Does it not throw away an old system when I update or something like that? Do I need to clean the system up in some way? 

It works just fine when I start it up, so does it matter?

---

### Post by lisati on 2011-02-15
This is normal: when there's an update to the Kernel, the older versions aren't automatically deleted, so you have something to fall back on if something goes wrong. It's usually safe to delete the old ones with Synaptic Package Manager.

---

### Post by Rubi1200 on 2011-02-16
Just to add to what lisati correctly said, this is quite normal.

There are a few different ways to clean up the GRUB menu:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)


If you want to remove the older kernels (but always leave at least one spare for troubleshooting purposes):

System > Administration > Synaptic

Search for the kernel image e..g. linux-image 2.6.xxx etc. and mark for removal
Also search for linux-headers and the same kernel number

There are always 3 files to remove for each kernel, 1 image and 2 headers.

---

### Post by the big e on 2011-02-16
Thank you both of you!

I have just taken a look into Synaptic Package Manager and it lists so much stuff I have never seen before.

So, a) those files you are suggesting I delete, where would they be found?

b) I just found out I have a few programming languages and a few games I didn't know I had, because they are not showing up on my applications menu. How would I access them?

---

### Post by drs305 on 2011-02-16
A simple GUI app that can easily remove older kernels (without all the brainwork) is Ubuntu Tweak. Here is a guide on how to install and use it. It's easy:

[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

It also does a lot more than removing kernels if you want to play with the other options ...

---

### Post by nynoah on 2011-02-16
Down load Ubuntu tweak and use that to delete old Kernals from your system.  You will find a lot of other useful tools in Ubuntu Tweak.  Great program.  Some here may not like it.  But it has always worked great for me.

---

### Post by 3rdalbum on 2011-02-16
> **the big e said:**
> 
b) I just found out I have a few programming languages and a few games I didn't know I had, because they are not showing up on my applications menu. How would I access them?

Type the name into the terminal; that's usually the way to start them.

For the programming languages, these are usually interpreters only - they're not a full environment that helps you write in the language, they just run whatever you have written. So you'd write your program in a text file, mark it as executable, and then drag it to the terminal window to run it.

You need a "shebang" on the first line of the file to tell Linux what program you want to use to run it; for instance, if this is a Python script you'd put this on the first line:

```
#! /usr/bin/python
```

---

### Post by 37fleetwood on 2011-02-16
can I just interject that for a newbie, unless you need the space, removing the kernels is a bit dangerous of an operation, I favor simply hiding them. the grub customizer works well for this and is so much safer. just un-check the extra ones leaving the newest two.

---

### Post by 37fleetwood on 2011-02-16
one other thing, what you're probably looking for is in Applications > System > Preferences > Main Menu. check the ones you want to show up and un-check the ones you never use. this way they are in the menu and you don't have to remember how to get them going again.;)

---

### Post by nynoah on 2011-02-16
Yes it is easier for a newby to just ignor it.  But really Ubuntu tweak makes it stupid proof.  Deleting old Kernals only really matters when a person has a **/ (partition) **  separate from his **/home**.

---

### Post by waynefoutz on 2011-02-16
I second the suggestion for Ubuntu Tweak. That is the safest method to do this operation with. Removing them with synaptic or some other method could possibly lead to a user deleting the kernel that person's using, ruining the install. I've fell victim to that before. Ubuntu Tweak will delete only the ones you aren't using.

---

### Post by Guilden_NL on 2011-02-16
> **nynoah said:**
> Yes it is easier for a newby to just ignor it.  But really Ubuntu tweak makes it stupid proof.  Deleting old Kernals only really matters when a person has a **/ (partition) **  separate from his **/home**.

Two thumbs up from me.  I agree 100% with you.

---

### Post by guilleme on 2011-02-16
You know, from newbie-to-newbie, I would suggest you to keep the entries in grub, or at least if you like learning by changing stuff, because that way you can normally boot to something if you mess up badly, it's saved me a couple of times! 
So, if the large list doesn't bother you, I'll suggest you to keep it, just in case.:)

---

### Post by rvchari on 2011-02-16
> **the big e said:**
> I have a dual boot, with Windows Vista and Ubuntu on a Think Pad T500.
One thing that puzzles me is when I turn it on and get the boot menu, it lists five different numbered versions of Ubuntu, along with their respective recovery modes, instead of just one. 

What is happening here? Does it not throw away an old system when I update or something like that? Do I need to clean the system up in some way? 

It works just fine when I start it up, so does it matter?

ubuntu kernels keep adding as they are not deleted automatically. it is advisable to keep one previous running version on hand (just incase something goes buggy with the newly installed kernel) if you are sure that everything is fine with the newly installed kernel, there are various options to clean and remove old linux headers / images.
i ll mention the easiest way (where you will not confuse with command line codes typing on the terminal)
install ailurus from the ppa

add this to your ppa... in synaptic
deb [http://ppa.launchpad.net/ailurus/ppa/ubuntu](http://ppa.launchpad.net/ailurus/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/ailurus/ppa/ubuntu](http://ppa.launchpad.net/ailurus/ppa/ubuntu) maverick main

then reload synaptic and install ailurus.

this package has multi options for all your needs....
start ailurus > clean up > unused linix kernels.

the package should handle ur cleaning problems in old linus kernels / removals

---

### Post by nynoah on 2011-02-16
Here is the link for Ubuntu Tweak.  You will find it does tons of other cool things for your Ubuntu system.

[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

---

### Post by the big e on 2011-02-16
Thank you to DRS305 and NYNoah for telling me about Tweak.

I have just downloaded Tweak and now I am exploring it and trying to understand what I see. I see that it links to a software repository I can install things from. Is this the same software repository that came with Ubuntu Software Center that's there by default, and if not, could there be conflicts between nearly-identical versions of the programs if updates occur in conflicting ways?

---

### Post by Paqman on 2011-02-17
> **the big e said:**
> I see that it links to a software repository I can install things from. Is this the same software repository that came with Ubuntu Software Center that's there by default

No, it's not.

> 
and if not, could there be conflicts between nearly-identical versions of the programs if updates occur in conflicting ways?

No, the package manager is smart enough to avoid that. However, the actual packages themselves are possibly not as stable or well tested as the packages from the main repositories. I would stick to getting your software from the official Ubuntu repositories if I was you.

---

