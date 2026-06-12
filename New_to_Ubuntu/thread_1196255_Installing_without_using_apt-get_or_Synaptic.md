---
title: "Installing without using apt-get or Synaptic?"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by RobertL on 2009-06-24
Will I mess up things if I install software without using apt-get or Synaptic Package Manager?

What prompts the question is that I'm having trouble getting my printer to work ever since I upgraded to jaunty and there is a new version of the printer driver ("hplip") that I'm tempted to install. It is two versions newer than the version in the repositories and fixes some problems. It is packaged with a linux installer and instructions but the instructions don't say anything about apt.

---

### Post by Bachstelze on 2009-06-24
> **RobertL said:**
> Will I mess up things if I install software without using apt-get or Synaptic Package Manager?

What prompts the question is that I'm having trouble getting my printer to work ever since I upgraded to jaunty and there is a new version of the printer driver ("hplip") that I'm tempted to install. It is two versions newer than the version in the repositories and fixes some problems. It is packaged with a linux installer and instructions but the instructions don't say anything about apt.

You won't mess anything up, but it might get tricky to remove it if you ever want to. In any case, you should of course uninstall your current version in Synaptic before you install the new one, to avoid conflicts.

---

### Post by BbUiDgZ on 2009-06-24
> **RobertL said:**
> Will I mess up things if I install software without using apt-get or Synaptic Package Manager?

What prompts the question is that I'm having trouble getting my printer to work ever since I upgraded to jaunty and there is a new version of the printer driver ("hplip") that I'm tempted to install. It is two versions newer than the version in the repositories and fixes some problems. It is packaged with a linux installer and instructions but the instructions don't say anything about apt.

apt-get will use the debian package manager (dpkg)to install things and it'll keep a record of which debian packages (.deb) you have installed and work out dependencies for new software you install using apt-get and install those dependencies. 
with me?

if you can get a debian package for your printer driver e.g printdriver.deb. this means you can use dpkg to install it and if any dependencies need met you can use apt-get to meet them.

to install a .deb file (debian package) in terminal type:
```
sudo dpkg -i nameoffile.deb
```
to meet the dependencies type:
```
sudo apt-get install -f
```

So what if there is no debian package i hear you say?

Most "generic" linux programs will come in a .tar.gz which is an archive file much like a .zip or .rar.

to extract a .tar.gz file to a folder with the same name as the archive type:
```
sudo tar -zxvf nameoffile.tar.gz
```

change to the folder you just created and extracted the archive contents to
```
cd nameoffile
```
you should find a readme file of some sort that will instruct you how to install the nameoffile software. (in your case a print driver).

Now to answer your question... will you break your system?
i have no idea, it depends on the software you are installing

i hope this is of some help

---

