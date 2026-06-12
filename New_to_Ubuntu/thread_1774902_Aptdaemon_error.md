---
title: "Aptdaemon error"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by KeremE on 2011-06-03
Hi, I just installed Ubuntu 11.04, but when I tried to install Dropbox, the following error occurred. Does anyone know what may be the problem?


There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Details:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

---

### Post by jtarin on 2011-06-03
> E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this packageTry Reinstall/Install the ttf-mscorefonts package. Search for it in Synaptic. If it's installed try to fix it. From the Synaptic menu look for "Fix Broken Packages" or something like that. I'm not on my Ubuntu machine at the moment. Make sure the package is high-lighted.

---

### Post by KeremE on 2011-06-04
I updated the ttf-mscorefonts package and it works now. Thanks!

---

### Post by jtarin on 2011-06-04
> **KeremE said:**
> I updated the ttf-mscorefonts package and it works now. Thanks!Great !!! Mark this thread as solved to help someone else.

---

### Post by tomcatification on 2011-06-19
> **jtarin said:**
> Try Reinstall/Install the ttf-mscorefonts package. Search for it in Synaptic. If it's installed try to fix it. From the Synaptic menu look for "Fix Broken Packages" or something like that. I'm not on my Ubuntu machine at the moment. Make sure the package is high-lighted.


Ive found said package but it wont let me install it!!! :'(

---

### Post by jtarin on 2011-06-19
Are you using Synaptic to install? What it the error message.?
What version of Ubuntu?

---

### Post by tomcatification on 2011-06-19
im using the 11.4 version of linux and yes im useing synaptic i found the package i marked for installation and nothing happens do i need to be admin at all???? 

thanks :)

---

### Post by jtarin on 2011-06-19
> **tomcatification said:**
> im using the 11.4 version of linux and yes im useing synaptic i found the package i marked for installation and nothing happens do i need to be admin at all???? 

thanks :)Ater marking your installation you have to "APPLY" your selection from the toolbar.

---

### Post by tomcatification on 2011-06-19
its not letting me click on it... do i need to be admin???

---

### Post by jtarin on 2011-06-19
> **tomcatification said:**
> its not letting me click on it... do i need to be admin???
Normally when Synaptic opens it ask for your password.

Try ```
sudo apt-get install ttf-mscorefonts 
```
or
The Ubuntu Software Center and search and install ttf-mscorefonts

---

### Post by tomcatification on 2011-06-19
> **jtarin said:**
> Normally when Synaptic opens it ask for your password.

Try ```
 
sudo apt-get install ttf-mscorefonts 
```or
The Ubuntu Software Center and search and install ttf-mscorefonts



the message that comes up when i open synaptic is: 

Starting without administrative privileges

You will not be able to apply any changes. However, you can still export the marked changes or create a download script for them


BTW ive set my account to admin but this message still comes up and also ttf-mscorefonts is not installed

ive try sudo apt-get but this is everything that canme up  sudo apt-get install ttf-mscorefonts
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ttf-mscorefonts

---

### Post by jtarin on 2011-06-19
Main Menu>_The Ubuntu Software Center_: and search and install ttf-mscorefonts

---

### Post by tomcatification on 2011-06-19
i cant because of the aptdaemon error! 

i cant install anything what so ever on the software centre :'( 

this is what im trying to fix!

how to i fix the admin message ?

sorry if im being a pain in the ***

---

### Post by jtarin on 2011-06-19
Let's try this```
sudo sh -c "mv /var/lib/dpkg/status /var/lib/dpkg/status.bak; sudo apt-get update"
```This will move your existing "status" to "status.bak" and a new will be generated. Then after the update runs try the corefont install again. Post any errors.

---

### Post by tomcatification on 2011-06-19
ok what ive done is ive reinstalled linux and ive downloaded the ttf package from the software centre but i look on synaptic and its not installed.

The reason i think for the error is java, ill try the codes but is there a alternative for java.

---

