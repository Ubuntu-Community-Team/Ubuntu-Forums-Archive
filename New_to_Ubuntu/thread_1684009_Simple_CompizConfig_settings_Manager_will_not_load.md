---
title: "Simple CompizConfig settings Manager will not load."
date: 2011-02-08
forum: New to Ubuntu
---

### Post by CyralSnear on 2011-02-08
Hi, very new to Ubuntu and i have to say the future looks promising for my laptop.
I had DockbarX and Compiz installed and was all working beautifully until an error poped up. 
After uninstalling DockbarX Simple CompizConfig settings manager will not load. 
i have tried going into Synaptic Package Manager and re-installing it, which failed.
Any input would be appreciated.

---

### Post by Kirboosy on 2011-02-08
Welcome to the Forums! :)

Can you post the error message?

---

### Post by CyralSnear on 2011-02-08
Thanks for the welcome and reply:p, unfortunately i don't have the error message. This problem happened last night

---

### Post by Kirboosy on 2011-02-08
Hmmm.... Maybe you should try reinstalling everything related to compiz and see if that fixes anything.

Also have you tried install the "compizconfig-settings-manager"? I prefer that over the simple manager.

---

### Post by Tyggna on 2011-02-08
Also, try running it from a terminal--sometimes there are issues running it from the applications bars.

Applications->Accessories->Terminal
$]ccsm

---

### Post by CyralSnear on 2011-02-08
I have tried reinstalling everything related to compiz before and didnt work. the compizconfig-settings-manager is installed as well and works fine but lacks features and looks very basic. 


after trying to run in terminal i get this - 
$ ccsm
Info: No sexy-python package found, don't worry it's optional.
libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
Loading icons...
then loads  compizconfig-settings-manager.

---

### Post by Tyggna on 2011-02-08
> **CyralSnear said:**
> I have tried reinstalling everything related to compiz before and didnt work. the compizconfig-settings-manager is installed as well and works fine but lacks features and looks very basic. 


after trying to run in terminal i get this - 
$ ccsm
Info: No sexy-python package found, don't worry it's optional.
libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
Loading icons...
then loads  compizconfig-settings-manager.

K, well, there are two problems there that are relatively easy to fix.

First one, just type in: 
```
sudo apt-get install python-sexy
```

Next is a little more involved.
Type in:
```

updatedb
whereis libgconf.so
```
if it says anything after libgconf: on the output of that, then type in:
```

dir=`whereis libgconf.so | awk '{print $2}'`
ln -s $dir /usr/lib/compizconfig/backends/libgconf.so
```

If there isn't anything after the whereis command, then try reinstalling libgconf2.  I don't know the exact version of it on your version of ubuntu--so you'll have to hunt that down.

---

### Post by CyralSnear on 2011-02-08
Thank you,

its true about the ubuntu community, friendly and very helpful 

thank you all for the input, 1000 internets in the post

Terminal 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-sexy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python-sexy' has no installation candidate



im using 10.10 Maverick Meerkat

---

### Post by Tyggna on 2011-02-08
> **CyralSnear said:**
> 
E: Package 'python-sexy' has no installation candidate

im using 10.10 Maverick Meerkat

Dang, I need to update.  

Try sexy-python instead of python-sexy.  Also, might just be quicker to search for the package in your package manager.  Don't know if that'll entirely fix the issue.  It seems that the greater problem is the second one posted in the output.

---

### Post by CyralSnear on 2011-02-08
Couldnt find sexy-python in package manager so tried 
sudo apt-get install sexy-python

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package sexy-python

---

### Post by CyralSnear on 2011-02-08
I hate to do this but, bump

---

### Post by Kirboosy on 2011-02-08
You could try getting the package from [here]("https://launchpad.net/ubuntu/+source/sexy-python")

---

