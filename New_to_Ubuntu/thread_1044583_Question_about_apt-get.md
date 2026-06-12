---
title: "Question about apt-get"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Malalo on 2009-01-19
Hi !

Just wondering if there's a way to visualize, using "apt-get", a list of the different packages available ?
I know there's a way to do so in Synaptic, but I'm looking for a particular Java package and can't find the correct name...

---

### Post by adult swim on 2009-01-19
synaptic package manager is the gui for apt-get

---

### Post by tegnoto89 on 2009-01-19
You can open synaptic and search "Java" and see what comes up - just an idea

---

### Post by OrangeCrate on 2009-01-19
Only mildly related to your question, but I found this to be really helpful in understanding apt. It's a good read, and reference guide:

[http://wiki.linuxhelp.net/index.php/Apt-get_Guide](http://wiki.linuxhelp.net/index.php/Apt-get_Guide)

---

### Post by Malalo on 2009-01-19
Ok I'll go into more details...

I'm trying to write a script to launch on new PCs I'm thinking of installing :

I have 10 machines I want to install Ubuntu on them, but with similar configurations. So I thought after installing Ubuntu on all machines, I'd only have to run the script to install the packages I need...

---

### Post by pedro3005 on 2009-01-19
find the package name with synaptic then add the line to the script
sudo apt-get install packagename

---

### Post by adult swim on 2009-01-19
see post 5 in this thread [http://ubuntuforums.org/showthread.php?t=1028668](http://ubuntuforums.org/showthread.php?t=1028668)
once you get a machine set up the way you like it, run the second command (you can skip the first, im not sure why that is there.)  it will create a text file of all the installed programs you have.  you can then take that text file to other computers and install the packages from it automatically using the next two commands.

---

### Post by lykwydchykyn on 2009-01-19
apt-cache has functions for searching through the package list at the CLI.  Sounds like you might want to look at using [ pre-seeding](https://help.ubuntu.com/8.10/installation-guide/i386/preseed-using.html).  Or have a look at [FAI](http://faiwiki.informatik.uni-koeln.de/index.php/FAI_multi-distribution)

---

### Post by Malalo on 2009-01-19
That's prefect, I'll try it out.

Thanks a lot to all (can't find "thanks" button !!)

---

### Post by collinp on 2009-01-19
> **Malalo said:**
> That's prefect, I'll try it out.

Thanks a lot to all (can't find "thanks" button !!)

They disabled the Thanks button for a while, it drew too hard on the forum hardware.

---

### Post by Malalo on 2009-01-19
> **Hellow said:**
> They disabled the Thanks button for a while, it drew too hard on the forum hardware.

Oh ok...
Also I can't find he "mark as solved" option in the thread tools.... same issue ?

---

### Post by collinp on 2009-01-19
> **Malalo said:**
> Oh ok...
Also I can't find he "mark as solved" option in the thread tools.... same issue ?

I believe so.

---

