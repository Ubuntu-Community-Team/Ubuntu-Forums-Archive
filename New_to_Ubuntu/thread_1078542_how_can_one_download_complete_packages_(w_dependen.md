---
title: "how can one download complete packages (w/ dependencies)?"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by sa125 on 2009-02-23
I'm forced to do offline installs in my office environment since I have a computer that has to stay offline. I have an online computer right next to it, so I wanted to know if there's a command to get a complete debian package with dependencies. I tried searching the apt-get manual, but either missed it or it's not there.

I'm tired of manually downloading packages one at a time, so what I'm looking for is just a bash command or custom script that will fetch a debian package and all of it's dependency packages into a specified (or current) directory. Is there something like that?

---

### Post by unutbu on 2009-02-23
To avoid the misery of downloading some debs and only later finding out you have unmet dependencies, go to Synaptic (on the offline machine). Mark the package you wish to install. Then go to File>Generate package download script. Save the script and Quit synaptic. The script is a text file which will contain the complete list of packages (debs) you will need to download from [http://packages.ubuntu.com/](http://packages.ubuntu.com/). 

Transfer the the script to the machine with an internet connection. If the online machine is a unix machine with the wget command, then you can run the script to download the necessary packages. If the online machine is a Windows machine, then you'll have to open the script with a text editor to find the urls of the necessary packages.

Once you copy the debs over to the offline filesystem, put them in a directory all by themselves. To avoid dpkg from complaining about unmet dependencies, open a terminal (Applications>Accessories>Terminal) and type

```
cd directory-with-the-debs
sudo dpkg -i *
```

(The * will list all the debs in one line, and when done this way dpkg can somehow decide the correct order the packages must be installed for you.)

---

### Post by oldos2er on 2009-02-23
[http://keryx.betaserver.org/](http://keryx.betaserver.org/)

---

### Post by unutbu on 2009-02-23
Thanks for the link,oldos2er. Keryx looks like a nice solution.

sa125, there is a tutorial here: [http://crashsystems.net/2009/01/keryx-tutorial/](http://crashsystems.net/2009/01/keryx-tutorial/). You might want to try Keryx instead of the method I posted above, because it looks like Keryx can find updates for your system -- something I don't think my posted method can do.

---

### Post by sa125 on 2009-02-24
Seems like an excellent utility program - I'll give it a try.

Thanks!

---

### Post by EXCiD3 on 2009-02-24
Hope Keryx works well for you, I'm the developer after all. If you need any help, let me know. :)

---

### Post by sa125 on 2009-02-25
> **EXCiD3 said:**
> Hope Keryx works well for you, I'm the developer after all. If you need any help, let me know. :)

It took me just one try to realize Keryx is awesome - it's like synaptic-to-go :)

Thanks!

---

### Post by EXCiD3 on 2009-02-25
:D Thanks! I've got lots of features planned for it and I cant wait until I have some more free time to actually start adding them.

---

