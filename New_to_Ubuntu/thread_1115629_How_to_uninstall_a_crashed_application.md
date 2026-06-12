---
title: "How to uninstall a crashed application"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-04-04
Hi all,
 My gnome menu crashed. When I try to send the files to the trash from usr, it wont let me. How do I un-install an application?
Thanks

---

### Post by cosine352 on 2009-04-04
> **AndyP79 said:**
> Hi all,
 My gnome menu crashed. When I try to send the files to the trash from usr, it wont let me. How do I un-install an application?
Thanks

this
> sudo apt-get remove 'application_name'
sudo apt-get autoremove 'application_name'

---

### Post by AndyP79 on 2009-04-04
> **cosine352 said:**
> this

Okay, so I tried this. It says everything is removed, even removed the themes. It was no longer in the options for the panel. Re-downloaded all the packages, and still no luck. I still get the error, asking if I want to delete this error in the gnome menu???? Can I try anything else?

---

### Post by hyper_ch on 2009-04-04
exacte error messages help.

---

### Post by AndyP79 on 2009-04-04
the panel encountered a problem while loading
"OAFIID:GNOME_GnoMenu".
Do you want to delete the applet from your configuration?

---

### Post by hyper_ch on 2009-04-04
also the command that you issued

---

### Post by AndyP79 on 2009-04-04
there was no command, i did that from the add to panel, clicking on the gnomenu choice

---

### Post by hyper_ch on 2009-04-04
you were give in post #2 commands to run from the cli.

---

### Post by AndyP79 on 2009-04-04
oh yea, sorry, I did that, and got a standard terminal response of it removing the applications, themes and all. Sorry, I lost my internet connection last night on my boat. 

This is the what I put in the terminal;

 ~ $ sudo apt-get remove gnomenu
[sudo] password for andrew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnomenu
0 upgraded, 0 newly installed, 1 to remove and 18 not upgraded.
After this operation, 315kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 117610 files and directories currently installed.)
Removing gnomenu ...


After this, i reinstalled it, but continued to get the message I posted above; So I tried the autoremove command, and it says that it is already removed:

 ~ $ sudo apt-get autoremove gnomenu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnomenu is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.


Usually when things like this happen, I freak,, and just reload the whole OS, but I am trying to avoid doing that anymore, and hopefully understand a little more about this stuffs. Thanks for the help so far.

---

### Post by SteveNorman on 2009-04-04
sometimes you have left over configuration files, and that is often why things go wrong. You have to go through and hunt down and remove all the leftover garbage before reinstalling.

do this:
```

sudo apt-get --purge remove gnomenu
sudo updatedb
locate gnomenu
```

then remove by hand everything you see using rm

I will get flamed for this, but I think apt-get is not as good as aptitude. So when you reinstall try aptitude instead of apt-get.

---

### Post by gandaran on 2009-04-04
> I will get flamed for this, but I think apt-get is not as good as aptitude. So when you reinstall use aptitude instead of apt-get.
all user configuration files in the hidden home folder are left behind whether you use apt-get, aptitude or synaptic package manager to install or remove the application, reinstalling an application never resolves the issues unless you clean up the user configuration files, another problem is if you make any modification to the applications root file system installation folder (in this case adding a theme) that altered folder will be left behind when removing the application, the solution is always to clean up before reinstalling.

---

### Post by AndyP79 on 2009-04-04
Hi All,
 Okay, I took the advices, and I have a clean install on here, works now.
 Thanks to everyone

---

