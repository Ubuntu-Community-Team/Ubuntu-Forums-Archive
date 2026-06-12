---
title: "[SOLVED] Can't install Open Office.org3"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by gshockxc on 2008-12-02
I downloaded the Debs 64 file for HH, but I can't seem to get the install to work.  I've tried both the command line installer and clicking on the install files.  Neither one works.  Should I be running the normal linux file?  I don't recall if I downloaded the 64-bit version of Ubuntu or not.  Is there an easy way to tell?

---

### Post by Silare Alvreon VI on 2008-12-02
Yeah. Extract the archive...

If there is no DEBS directory, you didn't get a DEB one.

If there is, go into it and double-click on of the .debs and if it complains that i386 architecture isn't compatible, you didn't get a 64-bit one.

See how that works out - if you actually did get the amd64 DEBs though, then what commands were you using?

---

### Post by alienexplorers on 2008-12-02
I loaded 3.0 by going to the openoffice site and downloading the deb file.  I then went to the file and un-tared.  I then went to the directory I extracted to and then to the debs directtory.  I then ran from terminal dpkg -i *.deb.......

---

### Post by Silare Alvreon VI on 2008-12-02
Hmm... can you post what Terminal spewed back at you then?

---

### Post by gshockxc on 2008-12-03
> **alienexplorers said:**
> I loaded 3.0 by going to the openoffice site and downloading the deb file.  I then went to the file and un-tared.  I then went to the directory I extracted to and then to the debs directtory.  I then ran from terminal dpkg -i *.deb.......

I'm up to the desktop-integration, and it won't let me go any further.  See the attached screenshot.

---

### Post by Tilex on 2008-12-03
You might want to remove the package "openoffice-unbundled, which conflicts with the desktop-integration .deb file.

---

### Post by Silare Alvreon VI on 2008-12-03
Try the following command:

sudo apt-get remove openoffice.org-core openoffice.org-unbundled openoffice.org-debian-menus

And then try that dpkg -i * command again.

---

### Post by gshockxc on 2008-12-03
> **Silare Alvreon VI said:**
> Try the following command:

sudo apt-get remove openoffice.org-core openoffice.org-unbundled openoffice.org-debian-menus

And then try that dpkg -i * command again.

Same result, different method.  I double-clicked on the Desktop-Integration folder and that told me which file was in conflict.  Then I went to Add/Remove, found the file, and selected it to be removed that way.  Then, I just double-clicked the file again, and it installed successfully.  

Thanks a lot for your help.  I'm starting to get the hang of it.  Thanks for walking me through it.

---

### Post by Silare Alvreon VI on 2008-12-03
No problem. If you want an explanation of how any of this worked, feel free to ask. Good to see it all worked out though, man. ^_^

---

### Post by gshockxc on 2008-12-03
> **Silare Alvreon VI said:**
> No problem. If you want an explanation of how any of this worked, feel free to ask. Good to see it all worked out though, man. ^_^

Yeah, absolutely.  I've played around with Xubuntu a couple of times a year ago, so I did a little bit with the config.sys files, but not much.

Please, feel free to educated me.  I'm anxious to learn as much as I can.

---

### Post by Silare Alvreon VI on 2008-12-03
Well, which part of the process did you not understand? I'm willing to explain the whole thing if you want also, but if there's a specific part of it that just was confusing, I'll explain that too.

---

### Post by gshockxc on 2008-12-03
> **Silare Alvreon VI said:**
> Well, which part of the process did you not understand? I'm willing to explain the whole thing if you want also, but if there's a specific part of it that just was confusing, I'll explain that too.

Well, I think the most confusing part now is just learning all the terminal commands.  At first, I was very confused about the DEBS that you were talking about.  But I didn't realize that the extraction process gave the folder the same name as the download file.  So I would have had to do something like: cd /home/gshockxc/Downloads/OOo3...../DEBS ... etc.

I created my own DEBS folder, not realizing that there was one buried in the OOo3 folder.  So when I tried to run the dpkg commands, there were no debs files to install, hence the error.  Once I figured that out, things worked fine.  Then the Desktop-Integration was a minor hiccup, but I figure a way around that, although probably not as efficient if I knew the proper commands to use.

How do you learn all the commands that you use?  Is it just experience, a book, is there a Ubuntu reference?  It seems like they go on forever.

---

### Post by Silare Alvreon VI on 2008-12-03
In truth, the whole desktop-integration thing was not a Terminal command problem. That was a thing with packages butting heads and not liking each other. The command "sudo apt-get remove ________" was for removing each package that didn't like the desktop-integration one you were trying to install. But you understand the whole DEBS deal now, right?

With Terminal however, the commands go on and on. And in many ways, Linux is just a bunch of Terminals running different things at the same time. 

But have you tried going into Terminal and typing "firefox" or "nautilus" as commands? They start up the exact program, and if the program has errors or crashes and you look back into the Terminal, it tells you what outputs they gave out. Everything has a strong base off of the Terminal. In fact, anything you can do in GUI form you can do with the Terminal, even if some aspects of it aren't as familiar.

If you don't know what a terminal command does though, but you know it exists, for the most part you can type the command and then either "--help" or "-h" after it. It should give a list. If not, just type the command on its own even.

In my case with learning commands, I just played with them a lot and knew some people. It's just experience (although I've only been on Linux for a few months, so I'm not super-experienced either...). I learned basic things like 'sudo' is to grant temporary root privileges, etc. from some friends too, so if you have any friends who know Linux, hit them up. And after using them enough, you just really kinda' memorize it (try typing sudo apt-get install to install something instead of going into Synaptic, you'll suddenly one day remember how to use it).

---

### Post by gshockxc on 2008-12-03
> **Silare Alvreon VI said:**
> In truth, the whole desktop-integration thing was not a Terminal command problem. That was a thing with packages butting heads and not liking each other. The command "sudo apt-get remove ________" was for removing each package that didn't like the desktop-integration one you were trying to install. But you understand the whole DEBS deal now, right?

With Terminal however, the commands go on and on. And in many ways, Linux is just a bunch of Terminals running different things at the same time. 

But have you tried going into Terminal and typing "firefox" or "nautilus" as commands? They start up the exact program, and if the program has errors or crashes and you look back into the Terminal, it tells you what outputs they gave out. Everything has a strong base off of the Terminal. In fact, anything you can do in GUI form you can do with the Terminal, even if some aspects of it aren't as familiar.

If you don't know what a terminal command does though, but you know it exists, for the most part you can type the command and then either "--help" or "-h" after it. It should give a list. If not, just type the command on its own even.

In my case with learning commands, I just played with them a lot and knew some people. It's just experience (although I've only been on Linux for a few months, so I'm not super-experienced either...). I learned basic things like 'sudo' is to grant temporary root privileges, etc. from some friends too, so if you have any friends who know Linux, hit them up. And after using them enough, you just really kinda' memorize it (try typing sudo apt-get install to install something instead of going into Synaptic, you'll suddenly one day remember how to use it).

I'm familiar with most of what you explained from bits and pieces I've learned over the years.  One of the things I like about Linux is just what you explained.  The GUI is not tied to the OS like in Windows.  If the GUI crashes, I can still run the OS in Linux.  As you know, that doesn't work in Windows.  

Thanks for the help on all of this.  You've been a tremendous source of information.  I really appreciate it.

---

