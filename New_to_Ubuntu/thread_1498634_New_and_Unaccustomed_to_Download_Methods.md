---
title: "New and Unaccustomed to Download Methods"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by Hastor on 2010-06-01
I recently borrowed a game from a friend who uses windows. Initially, I assumed I would 

have to end up using some roundabout way of installing it such as wine or some other 

issue. I ended up not being able to do anything. I can't run the setup and whenever I 

mount the disk file I just get a bunch of icons which I have no clue how to interact with. 

When I attempt to open some of the icons such as setup.exe or launch.exe it asks me for it 

to be allowed as an executable file. The only problem is that when I go to permissions to 

try to allow the file to be executable I get a message saying that permissions could not be 

determined. Any help would be deeply appreciated. Thank you.

---

### Post by bigsmitty64 on 2010-06-01
Depends on what game you are trying to run ([COLOR=Red]**some won't run with wine**[/COLOR]). Did you try using Virtual Box? You won't get anywhere trying to run a windows executable in Ubuntu. I would strongly suggest downloading Virtual Box through the Ubuntu Software Center, you can install windows in that, and then install your game in the virtual windows environment. Hope this helps at all :)

---

### Post by NUboon2Age on 2010-06-01
Did you install Wine?  If not that could be why you got that error message.  The easiest way might be to install Wine with the Ubuntu Software Center -- that'll make sure all the necessary packages get installed.  After that it'd be interesting to search in Synaptic for Wine to see if in the installed packages there are newer version of Wine available to install and if so, do it.

Then when you double-click on the exe files and it gives the executable permisions error you'll probably be able to check it off and you'll be onto the next step of this puzzle.

---

### Post by NUboon2Age on 2010-06-01
> **bigsmitty64 said:**
> Depends on what game you are trying to run (some won't run with wine). Did you try using Virtual Box? You won't get anywhere trying to run a windows executable in Ubuntu. I would strongly suggest downloading Virtual Box through the Ubuntu Software Center, you can install windows in that, and then install your game in the virtual windows environment. Hope this helps at all :)

Wine should allow them to run the .exe file.    It'd be a good idea to check the [Wine Application Database]("http://appdb.winehq.org/") to see if the program has been tried and what the results were.  VirtualBox is probably a better bet overall to actually getting the game running, but of course that will have its own challenges and learning curve.

---

### Post by nhasian on 2010-06-01
first install wine by clicking [here]("apt:wine")

then after you mount the cd, right click on setup.exe and choose "run with wine"  finally cross your fingers and hope it works.

---

### Post by Hastor on 2010-06-01
I checked synaptic and even clicked the download. The only thing my computer is telling me is that Wine is just about as installed as it gets. I'll get back to you if I can fanagle 

something out of the virtual machine. Before I get into actually using the machine I've got a bit of a question. How am I supposed to get the software for the Windows OS? I've used a 

virtual machine before and I know that at some point I'm going to need a CD with windows on it to actually put an OS on the machine.

---

### Post by NUboon2Age on 2010-06-04
> **Hastor said:**
> I checked synaptic and even clicked the download. The only thing my computer is telling me is that Wine is just about as installed as it gets. I'll get back to you if I can fanagle 

something out of the virtual machine. Before I get into actually using the machine I've got a bit of a question. How am I supposed to get the software for the Windows OS? I've used a 

virtual machine before and I know that at some point I'm going to need a CD with windows on it to actually put an OS on the machine.

Yes, you'd still need a windows iso or .vdi file to run it on VirtualBox.

What is the game?  

You should check [http://appdb.winehq.org/](http://appdb.winehq.org/) to see if there are reports on its wine compatibility.  Also you could check with Crossover (the developers of Wine -- they have a commercial version of Wine that is somewhat ahead of the open-source version that might do the trick.  Also PlayonLinux is a frontend for Wine that can help to run Wine more smoothly for some programs.

---

