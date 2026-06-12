---
title: "GDedi Installer - error: Dependancy is not satisfiable"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by Shiseiji on 2009-03-01
8.10 on a debranded HP Media (came sans OS so it is my big chance). 

I have been trying to install Deluge. I am "assuming" that when I get the subject message I need to go get the appropriate file and install it (though I am mystified why a file labeled architecture doesn't have the dependencies in it, but I digress). As I work my way through what I need, I got: "An older version is available in a software channel".  So I updated the Add/Remove list, but when I check the [Applications] [Add/remove] All Open Source Applications the file isn't listed. Suggestions? I see others have installed Deluge so I figure it is a noob thing. :???:

TIA,

Ron

---

### Post by binbash on 2009-03-01
there is a deluge ppa : 

deb [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) intrepid main

---

### Post by oldos2er on 2009-03-01
Deluge is in the universe repository. Check your software sources to make sure this is enabled.

---

### Post by Shiseiji on 2009-03-01
Thanks, I went to the University site and got the file to compile. But I don't see anyplace to change/add to the software sources.[COLOR="RoyalBlue"](Edit: Found it! [System][Software Sources])[/COLOR] I take your answer to mean that the Add/Remove list is accessing the University site even though I don't see it in my lists.

Am I correct in the assumption on needing to gather all the appropriate files and install them as the first part of my question?

Thanks again,

R

---

### Post by Xiong Chiamiov on 2009-03-01
If you've enabled universe, then you'll have to update your package list first before Deluge will show up in your lists.
```

sudo aptitude update && sudo aptitude install deluge

```

---

### Post by Shiseiji on 2009-03-01
Yes, I understood I needed to refresh the list as I was prompted to do so the first time I accessed the list. And I took that action once I saw how to add the university to my list. I still don't understand why I got the error message when Deluge wasn't in my list.

I am also trying to learn if when I get the subject message the correct action is to go get the appropriate files and install them from as many locations as it takes to obtain all the required dependencies. Or could I install files all day and still not have what I need?

Ron

---

### Post by RomeReactor on 2009-03-01
Hi. You should stick to the repositories whenever possible, or to .deb files from trusted sources before trying to compile from source.

Also take into account that not all available software shows up in Add/Remove; it's more of a tool to get software recommendations. To access all available programs try Synaptic, or Apt-Get/Aptitude from the terminal.

---

### Post by Shiseiji on 2009-03-01
I appreciate the help. I am going to assume for now:

1. No one who is posting knows why I got the error message with GDedi Installer.
2. No one who is posting knows what to do when GDedi Installer gives the subject error.
3. Use the command line script posted and not [Add/remove] programs or a search engine to look for software.

Thanks again for the work around. I will watch this thread and see if we get any other ideas posted. 

Ron

---

### Post by RomeReactor on 2009-03-01
> **Shiseiji said:**
> I appreciate the help. I am going to assume for now:

1. No one who is posting knows why I got the error message with GDedi Installer.
That was most likely due to not having the correct repositories enabled, so Gdebi was unable to install the necessary dependency.

> 2. No one who is posting knows what to do when GDedi Installer gives the subject error.
Take note of which dependency is missing, and search [here]("http://packages.ubuntu.com/") to find which repository provides it; then enable that repository, and try the installation again.

> 3. Use the command line script posted and not [Add/remove] programs or a search engine to look for software.
Remember that not all available software shows up in Add/Remove; Synaptic does show you the complete listing of packages available, provided the repositories you need are enabled.

Installing form Add/Remove or Synaptic will take care of any dependency needed; installing with Gdebi, you have to make sure the dependencies needed are available in the repositories, or that you get them elsewhere before installing the program--which can be much more complicated, as dependencies might have dependencies of their own, or they might conflict with already installed packages.

---

### Post by Shiseiji on 2009-03-01
Thanks again. I saw how vital "provided the repositories you need are enabled." is when I felt like I was chasing down endless rabbit holes when the dependencies had many, many layers and the architecture wasn't the depth I was hoping for. I did a successful Python build yesterday, but then really messed things over trying to clean up what I "thought" was being asked to do. Since it was a fresh Ubuntu install it was simply eating humble pie and reload and not many lost hours of work. It did became a reinforced lesson on asking where noobs are tolerated and understanding the answers. Hence the pointed questions. 

I do appreciate the gift of support. In my own little areas of expertise, I help people out at the local big box home centers when they need assistance on figuring out the correct fastener etc. when the clerks are absent or clueless. Maybe soon I can offer help in OpenOffice as MS Office 2007 dies what I hope is a quick death.

Ron

---

