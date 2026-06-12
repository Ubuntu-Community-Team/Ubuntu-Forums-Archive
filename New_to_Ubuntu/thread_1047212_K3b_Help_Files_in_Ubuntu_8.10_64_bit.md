---
title: "K3b Help Files in Ubuntu 8.10 64 bit"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by neotasic1 on 2009-01-22
This has been an ongoing problem for me which I can't seem to solve. Any help would be appreciated.  I am running Ubuntu (not Kubuntu) and after installation of K3b (the CD and DVD burning application) I am unable to access the help files. I get the error message "couldn't find service khelpcenter".  

I have got around this by running khelpcenter from the terminal, but then when I navigate to K3b manuals I get the error message "There is no documentation available for /k3b/index.html" On the basis of this I presume these files are missing or not installed, but searching these forums, and Google has not produced any pointers as to how to install them (khelpcenter4 is installed in Synaptic) nor have I found any reference to this, although this problem is present on at least 5 separate computers to which I have installed this program (both 32 and 64 bit)

Can anyone point me in the right direction? Any suggestions would be appreciated.

---

### Post by hyper_ch on 2009-01-22
it has nothing to do with 32/64bit but with KDE 3.5 / KDE 4

---

### Post by neotasic1 on 2009-01-22
> **hyper_ch said:**
> it has nothing to do with 32/64bit but with KDE 3.5 / KDE 4

Sorry, I don't fully understand the answer - do you mean the files do not install unless you have the entire KDE desktop environment - i.e not available unless I use the KDE desktop or Kubuntu? Or is this a bug in KDE 3.5/4?

Because it would appear that they do exist in /usr/share/doc/kde/HTML/en/k3b, but the format is docbook (which I understand is a Konquerer file - doesn't parse properly with Firefox) and the k3b help menu doesn't seem to find or interpret them correctly.

---

### Post by stchman on 2009-01-22
> **neotasic1 said:**
> This has been an ongoing problem for me which I can't seem to solve. Any help would be appreciated.  I am running Ubuntu (not Kubuntu) and after installation of K3b (the CD and DVD burning application) I am unable to access the help files. I get the error message "couldn't find service khelpcenter".  

I have got around this by running khelpcenter from the terminal, but then when I navigate to K3b manuals I get the error message "There is no documentation available for /k3b/index.html" On the basis of this I presume these files are missing or not installed, but searching these forums, and Google has not produced any pointers as to how to install them (khelpcenter4 is installed in Synaptic) nor have I found any reference to this, although this problem is present on at least 5 separate computers to which I have installed this program (both 32 and 64 bit)

Can anyone point me in the right direction? Any suggestions would be appreciated.

If you are running Ubuntu (Gnome) the KDE help files are not installed.  Do the following in a terminal.

```
sudo apt-get -y install kcontrol khelpcenter
```

You will now be able to access KDE help files and KDE look and feel.  Now when you are running K3b or any other KDE app you can use the Help portion.

---

### Post by neotasic1 on 2009-01-22
> **stchman said:**
> If you are running Ubuntu (Gnome) the KDE help files are not installed.  Do the following in a terminal.

```
sudo apt-get -y install kcontrol khelpcenter
```

You will now be able to access KDE help files and KDE look and feel.  Now when you are running K3b or any other KDE app you can use the Help portion.

I think you are on the right track here, but using the above in the terminal produces this output:-

neotasic1@sevenofnine:~$ sudo apt-get -y install kcontrol khelpcenter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kcontrol is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdebase-workspace-bin kdelibs4c2a
E: Package kcontrol has no installation candidate

Just a quick question before I try to install these alternatives - will it install the entire KDE desktop or just the minimum I need to get these files, as I would prefer not to install the entire desktop?

---

### Post by stchman on 2009-01-22
> **neotasic1 said:**
> I think you are on the right track here, but using the above in the terminal produces this output:-

neotasic1@sevenofnine:~$ sudo apt-get -y install kcontrol khelpcenter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kcontrol is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdebase-workspace-bin kdelibs4c2a
E: Package kcontrol has no installation candidate

Just a quick question before I try to install these alternatives - will it install the entire KDE desktop or just the minimum I need to get these files, as I would prefer not to install the entire desktop?

The package kcontrol is replaced in Intrepid.  The khelpcenter is available.

This gives you a bare minimum for KDE.
Do the following:

```
sudo apt-get -y install kdebase-workspace-bin kdelibs4c2a khelpcenter
```

This should get you what you want.

---

### Post by neotasic1 on 2009-01-25
> **stchman said:**
> The package kcontrol is replaced in Intrepid.  The khelpcenter is available.

This gives you a bare minimum for KDE.
Do the following:

```
sudo apt-get -y install kdebase-workspace-bin kdelibs4c2a khelpcenter
```

This should get you what you want.

Thank you very much, I will try this in the next day or so.

---

### Post by CharlesWaterhouse on 2009-01-28
> **stchman said:**
> The package kcontrol is replaced in Intrepid.  The khelpcenter is available.

This gives you a bare minimum for KDE.
Do the following:

```
sudo apt-get -y install kdebase-workspace-bin kdelibs4c2a khelpcenter
```

This should get you what you want.

I have just found this thread as I have a similar problem. In my case I can access the Gwenview help file(user manual) from Intrepid but trying to access Kontact/Kmail help gives the same result as neotasic1 found. Unfortunately running your suggestion above doesn't help - situation remains unchanged. 

Something else very strange - in Kontact, when I go to the help menu and select "Kontact introduction" it gives two options "Read manual" or "Visit Kontact website" - clicking either of these launches Thunderbird rather than Firefox which seems most strange!

Thanks for the mention of your Ubuntu Linux Resource website - am just starting to explore it & it looks great.

Cheers

---

### Post by capnthommo on 2009-01-28
hi there, like to say thanks for this one from me too.  real useful as i use K3B quite a lot, for data backup to disk.
cheers
nigel
:guitar:
R and R - rock and roll or rest and recreation - same thing either way!

---

