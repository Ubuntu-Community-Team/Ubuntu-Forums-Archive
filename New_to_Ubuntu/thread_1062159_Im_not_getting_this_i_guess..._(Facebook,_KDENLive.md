---
title: "Im not getting this i guess... (Facebook, KDENLive)"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by MikeBasilico on 2009-02-06
2 Problems...

Facebook Photo uploader: Downloaded the add-ons like it told me, and the menus worked, but it said "couldnt validate liscense" when i hit upload, i decided to sleep on it, now it doesnt work at all.

KDENLive: Yes i've follow the instructions to update it on 8.10, i get error messages on both of the steps from [here]("http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages")
when i add the to the 3rd party software i get an error:
```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B00E04A9D58062FB

```
when i enter the update line in terminal it loads and asks for permissions then i get
```
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
then it says i have updates, then it says i can only run a partial update, then iget an error that says it cant authenticate


I thing im doing something wrong in general, or have system troublr, because i feel everything is harder than linux should be

---

### Post by taurus on 2009-02-06
Download the script, launchpad-update.zip, and run it.

[http://ubuntuforums.org/showthread.php?t=1047743](http://ubuntuforums.org/showthread.php?t=1047743)

---

### Post by MikeBasilico on 2009-02-06
what is the key to run it
and is there any alternatives to terminal

im a visual person, command lines freak me out

---

### Post by taurus on 2009-02-06
Sorry but you have to unzip it and run it from a terminal.

```
cd ~/Desktop
unzip -x launchpad-update.zip
sudo ./launchpad-update
```

---

### Post by MikeBasilico on 2009-02-06
I ran it, and im still getting the same errors

thanks for helping

---

### Post by MikeBasilico on 2009-02-06
Is there a different distro that is more automatic that i should try?

I'm a professional in video production, not computers, i wanted to fight the man with linux, and its not going so well haha

---

### Post by LowSky on 2009-02-06
automatic in what? you need to bebe more specific?

Taurus gave you a scrip that should fix

did you do this to install the program
> Ubuntu Intrepid
After contacting Ubuntu packagers, it seems that Jaunty packages will never enter backports. Therefore it is recommended to install Kdenlive using alternative repositories.
Here is our recommended choice to install Kdenlive 0.7.2:

Go to your system menu > Software sources > Third-Party Software 
Click add and paste this line in:
deb [http://ppa.launchpad.net/baudm/ubuntu](http://ppa.launchpad.net/baudm/ubuntu) intrepid main 
Close software source and click reload 
Then type:
sudo apt-get update && sudo apt-get install kdenlive dvgrab frei0r swh-plugins


also you should report errors about kden to here
[http://kdenlive.org/forum/users-forums/installation-binary-packages](http://kdenlive.org/forum/users-forums/installation-binary-packages)

Also Facebook should just work, it does for me.

---

### Post by MikeBasilico on 2009-02-06
Automatic like, you just press a button and it updates instead of going through all this for every program

---

### Post by MikeBasilico on 2009-02-06
i installed them yes, before and after adding the script, and got the same errors both times

---

### Post by LowSky on 2009-02-06
not every program does this, you are trying to install a program that isnt included in the repos, and doesn't have a .deb extractable container.
so you are stuck doing it by hand.

Most applications are availible form the the Add/remove, or through Synaptic, both in the application and System>admin Menus respectively

---

### Post by carml on 2009-02-06
To update your software you can go to System->Administration->Synaptic package manager. ;)

---

### Post by MikeBasilico on 2009-02-06
KDEN is in the repository, just an old version, i would deal with it, but this is what my menus look like

[IMG]http://img299.imageshack.us/img299/4354/96951742io5.gif[/IMG]

---

### Post by MikeBasilico on 2009-02-06
i tried upgrading in synaptic and got a new error
```
E: /var/cache/apt/archives/kdenlive_0.7.2.1-0baudm1_i386.deb: trying to overwrite `/usr/share/applications/kde/kdenlive.desktop', which is also in package kdenlive-data


```

---

### Post by carml on 2009-02-06
Try to uninstall the previous version first,then try to install the newer version .

---

### Post by MikeBasilico on 2009-02-06
It randomly is working now...i dont even know what i did

now what about facebook?

---

