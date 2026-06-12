---
title: "why isn't most of the software in .deb format?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by kapi on 2009-04-13
Yeah I kind of know the answer . . . because not every linux system used .deb. 

Was thinking that Ubuntu would really take off if all of the software was in the .deb format. Then the transition for new users migrating from ubuntu would be able to say:

 "yeah Ubuntu is great, ms has the .exe and linux Ubuntu has the .deb, its the same process, just double click to install".

Its just a thought, I have been using ubuntu for five months now and still don't know the full score as far as installing a program from a tarball.  As it turns out I'm having to go back to xp on a different pc and use ubuntu on this second one because of the proprietary format of IE and the web design hassle. Ubuntu is good, free, secure and reliable but I suspect looses many users due to the proprietary war and their dependence on specific software.

---

### Post by LostMagix on 2009-04-13
There are quite a few people out there doing just that!

turning tar balls into .debs can take time however.

If you look hard enough you can find a .ded for most packages.

---

### Post by Simian Man on 2009-04-13
Why isn't all software in .rpm format.  It's what I use, so it's obviously superior.  Then I could just tell my friends to install Fedora or OpenSuse and double-click all their software!!11!

---

### Post by hyper_ch on 2009-04-13
debian has probably one of the largest precompiled repository out there and ubuntu is quite massive also (compared to other distros).

---

### Post by rasmus91 on 2009-04-13
> Why isn't all software in .rpm format. It's what I use, so it's obviously superior. Then I could just tell my friends to install Fedora or OpenSuse and double-click all their software!!11! or Mandriva =P


Yeah, had the same thought... Tarballs aren't bad though, i think were just to used to double clicking.

---

### Post by darthmob on 2009-04-13
[http://www.getdeb.net/](http://www.getdeb.net/)

you can download lots of programs as .deb there!

---

### Post by epswinde on 2009-04-13
Installing from a tarball depends heavily on the program you're installing.  After you unpack any .tar.gz or .tar.bz2 file, there should be a readme or an install file in there.  If all goes according to plan, that should be plenty of instruction on how to procede.  If you see a makefile, then the commands
```
./configure && make && sudo make install
```
will compile the source code and install it on a debian system.  But, your mileage may vary -- compiling code often requires hunting down dependencies (the infamous dependency hell).

Still other tarballs will be nothing more than an installation script.  Usually this will just involve running
```
./INSTALL
```
or some variation thereon to install it.  This is particularly common with proprietary programs (cisco vpn client, matlab, maple, come to mind).  In these cases it is imperative to consult the documentation inside the tarball or on the webside from whence it came.  These install scripts sometimes need to be tweaked before they'll work on your system (they could be written for RHEL and you're running it on ubuntu).  With these types of programs it is important to remember that ubuntu is a rather young distro, and proprietary products change slowly, and linux is often the last version to be changed in this manner.  Good ones though (MATLAB, maple) are POSIX complient, and use X11 as their interface, and install flawlessly with minor tweaking on any flavor of linux or unix i've tried.

If you find an .rpm, you can use alien to convert it to a .deb for use on a debian box.  However, both formats have different features, so this doesn't work 100% of the time.  Usually, i'll just compile from source, but that's not always available.  Again, your mileage may vary.

That's my speil on installing programs.  The other thing to remember is that google is your friend, chances are your question has been asked and answered before.  If you find the answer rather than it being given to you, you'll probably learn more about how your system works, thus making you a more valueable member of the community.

---

### Post by Paqman on 2009-04-13
It's starting to be really common to find a .deb available for pretty much any software that's out there. Better yet, lots of people provide a PPA. There's a lot to be said for one distro becoming the main player, as it forces a certain amount of standardisation.

---

### Post by kapi on 2009-04-13
Thanks, I was on getdeb the other day.

My point was really geared towards attracting ms users and making the transition as easy as possible for them. Nearly everyone I speak to concerning operating systems has never heard of ubuntu and kind of look at me with suspicion when I tell them about how good it is.

I think in order for ubuntu to be come really main stream like mac as an ms alternative, Ubuntu needs to (whether they like it or not) make the installation of programs one kind of defacto standard. Then MS windows watch out. . .because once the software developers see that people are making ubuntu and linux a serious competitor then they will open their doors and produce more software for the new audience. Its simple make it easier as well as free and secure and they will come to ubuntu in droves.

---

### Post by halitech on 2009-04-13
unless you need the most up to date software (or an odd piece) then for most users its just a matter of opening up synaptic (or Add/Remove) and selecting the program they want to install. Downloading from possible "unsafe" locations just opens the door to getting into big trouble. I find it a lot easier to open synaptic and do a search for a program type (or sudo apt-get install programname from the terminal if I know the name) then scouring the web trying to find software to do what I want

---

### Post by Eisenwinter on 2009-04-13
> **Simian Man said:**
> Why isn't all software in .rpm format.  It's what I use, so it's obviously superior.  Then I could just tell my friends to install Fedora or OpenSuse and double-click all their software!!11!
+1. thanks.

---

