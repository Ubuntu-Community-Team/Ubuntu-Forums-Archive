---
title: "Cairo Dock Dissappeared and Gimp problem in 10.04"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2010-05-07
I just updated to 10.04 and upon installing Cairo Dock I accidentally set the call back zone to zero. Now that the docks auto-hide I can't access it and I can't edit the settings without seeing the dock and I can't see the dock without editing the settings. Is theres a way to access Cairo dock's settings without having to right-click on the actual cairo dock?

Also I noticed a similar problem that I've had with previous versions of Ubuntu. Gimp will not save pictures as a jpeg as the option is not even avaliable under the extensions. I have no clue how to fix this and its driving me nuts because I actually want to be able to post my pictures online. Is there a way to fix this so I can save pictures as a jpeg?

---

### Post by punkdrummer09 on 2010-05-07
For the Gimp problem, try reinstalling it? It might fix the jpeg problem.

---

### Post by Mustard on 2010-05-07
> **Captainflowers91 said:**
> I just updated to 10.04 and upon installing Cairo Dock I accidentally set the call back zone to zero. Now that the docks auto-hide I can't access it and I can't edit the settings without seeing the dock and I can't see the dock without editing the settings. Is theres a way to access Cairo dock's settings without having to right-click on the actual cairo dock?

I've never used cairo dock myself, but I would assume the settings would be controlled from a config file somewhere with the $HOME directory.  Another assumption would be that it would be a hidden file preceded by a '.' character.  If you were to browse through your HOME folder with 'View Hidden Files' option on, and look for a possible candidate for the config file.

Thats my best suggestion for something to do while waiting for an actual cairo dock user to come along with a more precise answer. :)

---

### Post by Mustard on 2010-05-07
This thread, which I googled up (using keywords cairo dock config file), probably points you in the right direction.
[http://ubuntuforums.org/showthread.php?t=835729](http://ubuntuforums.org/showthread.php?t=835729)

---

### Post by Captainflowers91 on 2010-05-07
I've tried reinstalling gimp and updating the save options, but its not fixed anything. I don't know if this means anything, but I've noticed that the only way I've fixed it in the past is by completely reinstalling ubuntu (which I REALLY don't wanna have to do). The times when I've had all my save options, Gimp has has a sorta outer space image when it was loading, but the times where gimp doesn't have the save options, it shows a lamb lying in bed with a crescent moon (I know thats a terrible description, but its the best I could do). I'm sure this has to do with the version of Gimp I'm running, but IDK how to fix it

---

### Post by Mustard on 2010-05-07
> **Captainflowers91 said:**
> I've tried reinstalling gimp and updating the save options, but its not fixed anything. I don't know if this means anything, but I've noticed that the only way I've fixed it in the past is by completely reinstalling ubuntu (which I REALLY don't wanna have to do). The times when I've had all my save options, Gimp has has a sorta outer space image when it was loading, but the times where gimp doesn't have the save options, it shows a lamb lying in bed with a crescent moon (I know thats a terrible description, but its the best I could do). I'm sure this has to do with the version of Gimp I'm running, but IDK how to fix it

Which version of Gimp are you using?

How was it installed?

---

### Post by Captainflowers91 on 2010-05-07
First I 


Add the launchpad repository :
sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn &&  sudo aptitude update
 Then install it with the following command :
sudo aptitude install gimp gimp-data gimp-plugin-registry  gimp-data-extras

---

### Post by Mustard on 2010-05-07
> **Captainflowers91 said:**
> First I 


Add the launchpad repository :
sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn &&  sudo aptitude update
 Then install it with the following command :
sudo aptitude install gimp gimp-data gimp-plugin-registry  gimp-data-extras

Is their a specific reason why you are installing the svn version of gimp, rather than the version in the 'main' repository?

---

### Post by Captainflowers91 on 2010-05-07
No, this was just the way I found to install it. I was using 

[http://theindexer.wordpress.com/2010/03/21/to-do-list-after-installing-ubuntu-10-04-aka-lucid-lynx/](http://theindexer.wordpress.com/2010/03/21/to-do-list-after-installing-ubuntu-10-04-aka-lucid-lynx/)

to configure my new install of 10.04. Do you think that this may have something to do with the problem with Gimp's save options?

---

### Post by punkdrummer09 on 2010-05-07
> **Captainflowers91 said:**
> I've tried reinstalling gimp and updating the save options, but its not fixed anything. I don't know if this means anything, but I've noticed that the only way I've fixed it in the past is by completely reinstalling ubuntu (which I REALLY don't wanna have to do). The times when I've had all my save options, Gimp has has a sorta outer space image when it was loading, but the times where gimp doesn't have the save options, it shows a lamb lying in bed with a crescent moon (I know thats a terrible description, but its the best I could do). I'm sure this has to do with the version of Gimp I'm running, but IDK how to fix it


Check this thread out:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=79927](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=79927)

It's a little old, but who knows, it might work.

---

### Post by Mustard on 2010-05-07
> **Captainflowers91 said:**
> No, this was just the way I found to install it. I was using 

[http://theindexer.wordpress.com/2010/03/21/to-do-list-after-installing-ubuntu-10-04-aka-lucid-lynx/](http://theindexer.wordpress.com/2010/03/21/to-do-list-after-installing-ubuntu-10-04-aka-lucid-lynx/)

to configure my new install of 10.04. Do you think that this may have something to do with the problem with Gimp's save options?

I don't know for sure, but its certainly a possibility.  

```
sudo aptitude remove gimp
```

Go to your System>Administration>Software Sources and temporarily disabling the ppa repository, by unticking the box on that line in the 'Other Software' tab. Then the commands below in a terminal..

```

sudo aptitude update
sudo aptitude install gimp

```

This should install the version from the 'main' repository.

You can then test to see if it has fixed the problem.

---

### Post by Captainflowers91 on 2010-05-07
No such luck :(. SCIM wasn't even installed

---

### Post by Mustard on 2010-05-07
> **punkdrummer09 said:**
> Check this thread out:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=79927](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=79927)

It's a little old, but who knows, it might work.

Its a pretty old thread that one.  I dont know how relevant the answer is the current version of Ubuntu.

---

### Post by Mustard on 2010-05-07
> **Captainflowers91 said:**
> No such luck :(. SCIM wasn't even installed?

Have you tried my suggestion from page 2 of this thread.?

I probably should have suggested you remove the old version of GIMP first, before you the repository changes. :)

---

### Post by punkdrummer09 on 2010-05-07
> **Mustard said:**
> Its a pretty old thread that one.  I dont know how relevant the answer is the current version of Ubuntu.

Yeah, that's what I thought so too, but I googled the problem and stumbled upon this. It wouldn't hurt to try.

---

### Post by Captainflowers91 on 2010-05-07
Ive tried loading the software sources and I can't find where the source is that your referring too

---

### Post by Mustard on 2010-05-07
> **Captainflowers91 said:**
> Ive tried loading the software sources and I can't find where the source is that your referring too

One of the the tabs is labeled 'Other Software'.  The ppa at launchpad that you installed should be ticked under that tab. Unticking it should remove that ppa from your sources list.

Alternatively you could manually edit your sources.list file. Which is another story altogether, but not that hard to do.

---

### Post by Captainflowers91 on 2010-05-07
I did what you suggested and even rebooted. Now Gimp won't even start. I have no clue why, but even though it says its installed, it won't start up

---

### Post by Mustard on 2010-05-07
> **Captainflowers91 said:**
> I did what you suggested and even rebooted. Now Gimp won't even start. I have no clue why, but even though it says its installed, it won't start up

That seems rather strange.  A long shot might be that the config files need to purged, as they are conflicting.

```
sudo aptitude purge gimp
#this should purge the config files as well as uninstalling gimp
```

then reinstall

```
sudo aptitude install gimp
```

If you run gimp from the command line, you should be able to see the error messages it is throwing out.  Often the error messages can be quite spurious, but occassionally the error messages you see in terminal can help locate the problem.

---

### Post by Captainflowers91 on 2010-05-07
Gimp still won't start at all :/ This makes absolutely no sense. I've restarted and everything. I've purged gimp before without this happening.

---

### Post by Calash on 2010-05-07
Type the following into the terminal and post the output.


```

sudo apt-get install gimp

```

```

cat /etc/apt/source.lst

```

```

gimp

```

---

