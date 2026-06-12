---
title: "add Kubuntu (KDE) to Ubuntu"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by freeman2000 on 2009-05-13
I would like to add Kubuntu (KDE 4.2) to Ubuntu.  This is supposed to be an easy task.  Simply go to Synaptics and look for "kubuntu-desktop", mark it, and let it download with all its dependencies.  However, I get the following error message:

The following packages have unresolvable dependencies.  Make sure all required repositories are added and enabled in the preferences.  
Unresolved dependencies:  "kubuntu-desktop"
depends:  "language-selector-qt" (not going to be installed).
recommends:  "openoffice.org-kde"  (not going to be installed).


In Software Sources I have all 4 Ubuntu repositories checked - main, universe, restricted, and multiverse.  I have all 4 update options checked - security, updates, proposed, and backports.  I also have Canonical checked in the 3rd party software section.  

I tried to "Mark for Download" the "language-selector-qt" package, and then "Mark for Download" the "kubuntu-desktop" package, but it gave me the same error message.  I then tried to "Mark for Download" the "openoffice.org-kde" package, but it wanted to remove all the openoffice.org packages that I have related to Ubuntu, which I shouldn't have to do.  Any ideas/suggestions?  Thanks.


[edit]  Forgot to mention that I also tried to download "kubuntu-desktop" from Terminal and got the following error message:  
E: Invalid operation kubuntu-desktop

---

### Post by nhasian on 2009-05-13
does this guide help you at all?

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by lavinog on 2009-05-13
> **freeman2000 said:**
> 
[edit]  Forgot to mention that I also tried to download "kubuntu-desktop" from Terminal and got the following error message:  
E: Invalid operation kubuntu-desktop

That usually means you didn't use apt-get or aptitude correctly
it should be:
```
sudo apt-get install kubuntu-desktop
```
or
```
sudo aptitude install kubuntu-desktop
```
I think you left out the 'install' option

I would try the aptitude method. It should ask you questions on how you want to deal with the dependency issues.
If anything it should give you insight as to why you are having dependency issues.

---

### Post by kurok on 2009-05-13
sudo apt-get install kde has always worked for me

---

### Post by ravi_buz on 2009-05-13
If u like to do it in graphical way , search for kubuntu desktop in synaptic and install it , If u have a slow Internet connection download kubuntu alternative cd and install via that

---

### Post by freeman2000 on 2009-05-13
Here's my attempt to download in Terminal, and the error message that I received:  


xxxxxxxxx@xx:~$ sudo apt-get install kubuntu-desktop
[sudo] password for xxxxxxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: language-selector-qt but it is not going to be installed
                   Recommends: openoffice.org-kde but it is not going to be installed
E: Invalid operation kubuntu-desktop
xxxxxxxxx@xx:~$ 


I like the term it used - "impossible situation".    I had even less luck in Synaptics.   Any ideas?  Thanks.


[edit]   I was trying to follow that guide from Psychocats when trying to install it from Synaptics.  I also included "install" in my Terminal input.  The error message from my 1st post is the response I got from Synaptics, with the edit remark from Terminal.

---

### Post by lavinog on 2009-05-13
Have you tried using aptitude instead?

---

### Post by CowzRule on 2009-05-13
Are you running "Ubuntu Karmic Koala (testing)"?
That may be why you're having problems with dependencies.

---

### Post by freeman2000 on 2009-05-14
Thanks for all the replies.  Problem solved - I think.  Yes, I am running Karmic Koala testing, and APTITUDE did give me additional info.  It appears that the repositories have OpenOffice v3.0.1 and I have OO v3.1 installed, so Update Manager is balking at the backwards compatibility.  I'll have to wait a few days for the repositories to get to OO v3.1 in order to download "kubuntu-desktop" and install KDE 4.2.3.  Thanks to all.

---

