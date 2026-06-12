---
title: "Home Folder"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by orphanlast on 2010-06-03
Obviously installing programs on Linux is way different than it is on Windows. Now... my question is, "Is the home folder like the 'Program Files" for Linux?" and also, if I were to delete a program's folders from there, would I wind up actually deleting the program itself. If not, then where would I actually find where the program's information is actually stored. If there's a place that I can see that, then can I just delete the folder and have the program be uninstantiated that way?

I ask some of these questions because sometimes installing can be a rough process when you find a nice program that's no in the Synaptic Package manager or in the Ubuntu Software Center. Even after you install a program you can't just uncheck and completely remove a program from Synaptic if the program doesn't belong in there in the first place... So sometimes it's rough uninstalling programs.

I also installed a third party game called World of Goo (great game). But... I can't seem to make a desktop shortcut for it, and I can't seem to find a place to put the folder... So the folder that holds all of its information and pertinent folders is sitting on my desktop and there's a tiny folder inside the the Home Folder that's already ".world of goo"

Can someone please explain this.

---

### Post by Irony on 2010-06-03
Your home folder holds you personal files and configuration files.

Programs are generally held in /usr or /opt - sometimes programs install in the home folder but generally not. If you typed sudo when you installed then it went to /usr or /opt. If you installed a .deb then you can see it in synaptic and it will tell you where it is actually installed.

The .world of goo file can be deleted which will set the program back to its defaults.

---

### Post by philinux on 2010-06-03
If you open system>admin>synaptic package manager and then search for a program you can then see things like installed files. It will show where they are installed.

Linux File system. [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

---

### Post by Mark Phelps on 2010-06-03
> **orphanlast said:**
> ...Now... my question is, "Is the home folder like the 'Program Files" for Linux?"
Basically, no.  The /home folder is more like the old Document and Settings, or the new Users, folders.

> ... also, if I were to delete a program's folders from there, would I wind up actually deleting the program itself. 
What you would most probably delete is configuration settings you have set for the program.  Standard procedure is for a program to create a hidden folder under /home and write the settings there.

> Even after you install a program you can't just uncheck and completely remove a program from Synaptic if the program doesn't belong in there in the first place... So sometimes it's rough uninstalling programs.
Which is generally why we recommend that folks NOT download and install programs from source -- but use Synaptics instead.

---

### Post by 3rdalbum on 2010-06-03
> **orphanlast said:**
> Obviously installing programs on Linux is way different than it is on Windows. Now... my question is, "Is the home folder like the 'Program Files" for Linux?" and also, if I were to delete a program's folders from there, would I wind up actually deleting the program itself. If not, then where would I actually find where the program's information is actually stored. If there's a place that I can see that, then can I just delete the folder and have the program be uninstantiated that way?

I ask some of these questions because sometimes installing can be a rough process when you find a nice program that's no in the Synaptic Package manager or in the Ubuntu Software Center. Even after you install a program you can't just uncheck and completely remove a program from Synaptic if the program doesn't belong in there in the first place... So sometimes it's rough uninstalling programs.

Linux is a true multi-user system, so what's in your home directory pertains to your user account only.

I'd recommend looking for repositories and PPAs for whatever software you want to use, if it's not in the normal Ubuntu repository. For instance, if your want the Gloobus program, you'd do a search for "gloobus ppa" and find this URL: [http://ubuntu-tweak.com/source/gloobus-dev-gloobus-preview/](http://ubuntu-tweak.com/source/gloobus-dev-gloobus-preview/)

That page has instructions for adding that repository to your Software Sources, so then you CAN use Synaptic to install, update and remove the software.

You can't do that with all software, and not yet with paid software (this feature will come), but when you can it is excellent.

---

### Post by orphanlast on 2010-06-03
> **Mark Phelps said:**
>  Which is generally why we recommend that  folks NOT download and install programs from source -- but use Synaptics  instead.

Well, that's generally a problem because people need to download  whatever programs they feel they need or want, especially when  commercial ones aren't available. I hear people always talking about the free programs and the freedom of Linux, which I agree. those are pluses.

But I know how to get all my programs for free on Windows and there's really no hoops I need to jump through in order to get them... and there's not a general rule why I wouldn't be able to do it. I just can. The operating system will let me.

As fond as I am of Linux, with my current experience with it, I just have to ask a question about that last statement there. If Microsoft or Apple were to have stipulations like that for their programs do you think there's be a justified frustration from the consumers? Do you think the Linux community would point and laugh? If so, then maybe that needs to be fixed. Things would need to be standardized in the linux programing world to make that not be a problem. Which I've heard is starting to happen but all the programmers are kicking and screaming that they want to do things their way.

Their way is nice, but nothing works in a way that a consumer would appreciate... be that consumer a person playing around at home or a full blown business.

---

### Post by bodhi.zazen on 2010-06-03
> **orphanlast said:**
> Well, that's generally a problem because people need to download  whatever programs they feel they need or want, especially when  commercial ones aren't available. I hear people always talking about the free programs and the freedom of Linux, which I agree. those are pluses.

But I know how to get all my programs for free on Windows and there's really no hoops I need to jump through in order to get them... and there's not a general rule why I wouldn't be able to do it. I just can. The operating system will let me.

As fond as I am of Linux, with my current experience with it, I just have to ask a question about that last statement there. If Microsoft or Apple were to have stipulations like that for their programs do you think there's be a justified frustration from the consumers? Do you think the Linux community would point and laugh? If so, then maybe that needs to be fixed. Things would need to be standardized in the linux programing world to make that not be a problem. Which I've heard is starting to happen but all the programmers are kicking and screaming that they want to do things their way.

Their way is nice, but nothing works in a way that a consumer would appreciate... be that consumer a person playing around at home or a full blown business.

I think you completely missed the point of the advice you were given.

If an application is available in the Ubuntu Repositories, which are quite large, you should use the repositories (apt-get, synaptics, add/remove programs). Not only is this easier for new users, but upgrades are easier and you will have less problems "under the hood" such as conflicting libraries.

If there is some application you want or need that is not in the Ubuntu repositories you are as "free" as in freedom to do what you want as you are in Windows. The method of installation will vary depending on how the application is distributed.

Some apps my be distributed as .deb (VirtualBox comes to mind), others as binaries (firefox or songbird), but many others come as source code. In the event you do not use the Ubuntu repositories you will need to manually download any dependencies, install the application, and update the program as needed. You would need to download and compile source code manually. IMO it  is rather trivial to compile from source code, but I am more experienced then the average new user and I would imagine most new users would not have any idea where to begin compiling applications.

If the application is in the repositories all this is provided for you (apt resolves dependencies for example). By using the repositories many of these tasks are automated (dependencies, removal, etc).

See : [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

In terms of installing third party applications, you are not more restricted by Ubuntu then by Windows (IMO you are much more restricted by Windows). You will of course need to resolve dependencies and clean up manually. For an experienced user, removal is trivial I would simply use find or script removal. It is the same as on Windows, you can remove a program, but you often need to manually clean up afterwords, including editing the registry. Same with Ubuntu, you may need to manually clean up after removing an application, the exact steps are just different in Linux. Different, not easier or harder.

Because of the sheer size of the Ubuntu repositories it is much less common to feel the need to install third party applications outside the repositories.

---

