---
title: "sudo apt-get &lt;all downloaded apps&gt; script to save in /home partition to reinstall"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by mikodo on 2010-10-07
Hello everyone, 

I ran out of room in the title to ask my question properly. Can someone show me a script to use to save all my downloaded apps in my /home partition, so when I hose my system again, or when I upgrade the release, I can just run a script to reinstall them?

I know I saw this somewhere, but I can't remember where. Anyways it is something like this...

```
sudo apt-get update && sudo apt-get install <package; package; package; etc...>
```Can someone correctly tell me what it would be?

Also, is there a quick and automated way to reinstall in Software Sources the Other Software PPA's and Authentication Signing Keys for Trusted Providers? Could I save a one shot script for re-installing these too?

Thanks.

---

### Post by CharlesA on 2010-10-07
Try this:

```
dpkg -l > installedpkg
```

That'll give you a list of all the installed packages. I don't know if that'll help any for reinstalling them or not.

---

### Post by drs305 on 2010-10-07
Synaptic. File, Save Markings ( & tick the lower left box 'Save full state, not only changes').

When you want to install from the list: File, Read Markings.

---

### Post by CharlesA on 2010-10-07
> **drs305 said:**
> Synaptic. File, Save Markings ( & tick the lower left box 'Save full state, not only changes').

When you want to install from the list: File, Read Markings.

Nice. That's a way better way to do it.

---

### Post by lbrty on 2010-10-07
I have found this way to be the best way.

[http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

Summary:
> **abhiroopb said:**
> 
Open a terminal and paste the following into it:

```
$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`
```(the last command will take some time)

Now if you scroll to your home folder, you should find a folder called "dpkg-repack" which should have all the deb files of all your installed packages.


RE-INSTALL
If you want to re-install the packages, navigate to the folder with the packages and input the following command in the terminal:
```
sudo dpkg -i *.deb
```

---

### Post by mikodo on 2010-10-07
> **drs305 said:**
> Synaptic. File, Save Markings ( & tick the lower left box 'Save full state, not only changes').

When you want to install from the list: File, Read Markings.

Hey, I was actually looking at this and couldn't find a help guide or anything on how to use these functions. So I have saved a folder with all the apps with File, Save Markings, but I don't understand how to use the Read Markings in an install. Can you elaborate on this drs305?

Thanks.

---

### Post by drs305 on 2010-10-07
> **mikodo said:**
> Hey, I was actually looking at this and couldn't find a help guide or anything on how to use these functions. So I have saved a folder with all the apps with File, Save Markings, but I don't understand how to use the Read Markings in an install. Can you elaborate on this drs305?

Thanks.

The first command just creates a text file. If you look at it with any text editor, you will see a package name and "install".

If you want to install the same list, you would open Synaptic, File, Read Markings and then point to the file you saved. That would mark them for installation and then (I presume) you would press "Apply".

---

### Post by mikodo on 2010-10-07
@ drs305 and lbrty:

I got messing around with your suggestions, directions and links and forgot to acknowledge and thank you both!

THANKS!

If you don't mind, I am going to leave this thread open for a bit, to see if anyone else has anything to say/recommend before marking it as solved.

Mike  :)

---

### Post by drs305 on 2010-10-07
> If you don't mind, I am going to leave this thread open for a bit, to see if anyone else has anything to say/recommend before marking it as solved.


No problem! There are lots of ways to accomplish things in Linux.

If you are looking for other ways, here is how I do it from the command line:

Create a list of installed packages, named "installed-pkgs" on my Desktop.
```
sudo dpkg --get-selections > ~/Desktop/apps/installed-pkgs
```

Install the packages listed in ~/Desktop/installed-pkgs:
```

sudo dpkg --clear-selections && sudo dpkg --set-selections < ~/Desktop/installed-pkgs 
sudo apt-get update && sudo apt-get dselect-upgrade 
```

---

### Post by mikodo on 2010-10-07
drs305,

It is not an either/or situation, but for now... I especially like the way you do it, from the command line, as you posted last.

I have started with using that for the backups.

Thanks everyone!
Mike  :smile:

---

### Post by drs305 on 2010-10-07
> **mikodo said:**
> drs305,

It is not an either/or situation, but for now... I especially like the way you do it, from the command line, as you posted last.

I am have started with using that for the backups.

Thanks everyone!
Mike  :smile:

Just to be clear, you are only saving the *lists* via this method, as opposed to *lbrty's* method which actually stores the .debs  No packages are actually saved or stored on the machine using this method.


**Added:** When you import the list back into Synaptic, then you can install them via Synaptic as if you had manually selected each package for installation.

No need to respond...  Happy Ubuntu-ing!

---

### Post by mikodo on 2010-10-07
@ drs305,

Thanks for the clarification. I didn't realize that, and expected it would return the installed apps in a fresh/clean install, when run.

So, with lbrty's suggestion it is!

Mike

---

### Post by mikodo on 2010-10-08
[B]"Added: When you import the list back into Synaptic, then you can install them via Synaptic as if you had manually selected each package for installation."
[/B] 
Well then, this looks like, exactly what I am looking for.

Thanks so much everyone!

GNU/Linux; the Ubuntu Distro and the people here, helping others is inspiring! 

As a noob and a casual user, I try to do my part too! I burned a Live CD of an .iso of Lucid; downloaded some free beginner books and burned them in PDF on to an another CD, this week, for a friend to put on her older PC's, for her two children to use and learn on. One desktop is also going with her mother back to Trinidad. It is a good feeling to spread the joy!!

The machines are fully capable of running Lucid; Mom was using Windows 7 on them, she got fed up with the Malware etc... and wouldn't listen to me initially about Ubuntu and bought herself a Mac. Oh well, the kids and her mother are going to learn Linux.

Mike

---

