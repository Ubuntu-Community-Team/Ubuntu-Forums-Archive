---
title: "where's the best place to put repository's?"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by dj-toonz on 2009-09-13
Hi all, I'm updating my software on jaunty but keep making a mess of it :( where's the best place to put third party repository's?. Some sites say to add to etc/apt/sources.list and add #"name of the repository then a space & some say to add the name as a file  into etc/apt/sources.list.d as "what ever the software repository" is called i.e SongBird.list as that's where mediabuntu gets saved & add a # at the end of the file with the name of the software name (replaces the ppa address with the file name

how does everyone else do it ? getting confused now

---

### Post by yeats on 2009-09-13
I think it's up to you.  I tend to just add them to /etc/apt/sources.list, but I've done it the other way too.  Which is just to say that I don't think it matters too much either way. :-)

---

### Post by steveneddy on 2009-09-13
/etc/apt/sources.list

Just enter the path to software and enter keys and the system will do the rest.

---

### Post by Excedio on 2009-09-13
I just let my Software Sources do the work. System > Administration > Software Sources > Third-Party Software.

---

### Post by kansasnoob on 2009-09-13
> **dj-toonz said:**
> Hi all, I'm updating my software on jaunty but keep making a mess of it :( where's the best place to put third party repository's?. Some sites say to add to etc/apt/sources.list and add #"name of the repository then a space & some say to add the name as a file  into etc/apt/sources.list.d as "what ever the software repository" is called i.e SongBird.list as that's where mediabuntu gets saved & add a # at the end of the file with the name of the software name (replaces the ppa address with the file name

how does everyone else do it ? getting confused now

OK, since you said you're making a mess of it, let's back up and slow down!

Maybe we should look at your sources.list:

```
cat /etc/apt/sources.list
```

And then please explain what you're trying to add.

Medibuntu is easy!

---

### Post by earthpigg on 2009-09-13
not directly related to your question, but i have found this to be an outstanding tool:

Ubuntu Sources List Generator: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

pick your nation & version of Ubuntu to watch the magic happen.

---

### Post by kansasnoob on 2009-09-13
> **earthpigg said:**
> not directly related to your question, but i have found this to be an outstanding tool:

Ubuntu Sources List Generator: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

pick your nation & version of Ubuntu to watch the magic happen.

+1!

I found that while fiddling with Karmic after updates totally vacated my sources.list. No apparent problems so far!

---

### Post by theozzlives on 2009-09-13
You can add with GUI or /etc/apt/sources.list. If the particular sofware gives you a command (medibuntu for example) I just copy and paste the command line. Don't forget the keys.

---

### Post by dj-toonz on 2009-09-13
How come I made a mess of it, I was adding the repos to my sources.list as normal but I must of had a cock up somewhere as every time I went to do a sudo apt-get update it was failing with a error about some repos coudn't but found so I had to do a re-install anyway as I've just rebuilt a new system & using the system in the sig as a test system  
so now  I've let Ubuntu-tweak do the work for me now :). it even adds the keys aswell (I had no problem adding repositories, but was getting confused as to why mediabuntu adds its self to /etc/apt/sources.list.d & not sources.list where all the default repositories go? It's the same as when you use ubuntu-tweak it adds the files in /etc/apt/sources.list.d with the name of the software i.e OpenOffice.org for the ppa repository for OpenOffice. I used to use Fedora before coming back to Ubuntu and got used to adding the repositories as individual files, much tidier that way i think then having loads of deb://***whatvever the repository is*** & don't know what it is for. I now why about the comment box as I've added comments for the deb:// to what the software is 

cheers everyone

---

