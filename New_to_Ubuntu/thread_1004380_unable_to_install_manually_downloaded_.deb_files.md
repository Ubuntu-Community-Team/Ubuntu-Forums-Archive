---
title: "unable to install manually downloaded .deb files"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by maduranga on 2008-12-07
I tried to install several deb files which are downloaded manually by the firefox. But I get the following error once they are downloaded and attempted by ubuntu to run the installer. 

"/tmp/ubuntu-tweak_0.4.3-1~intrepid1_all.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences."

someone please help me.

---

### Post by catcharavind2003 on 2008-12-07
It seems you are trying to open file straight away, instead of first downloading it and the working with it locally. Try right-clicking on the link to the file, and then choose "save as", and in the dialog which opens use "save to disk", and not "open with " .
Then use your file manager to work with the file, e.g. nautilus or konqueror.
The Problem is probably that firefox somehow thinks it know how to handle the file, but then, when it actually tries, some helper application is not installed as expected by firefox.

---

### Post by HotShotDJ on 2008-12-07
> **maduranga said:**
> "/tmp/ubuntu-tweak_0.4.3-1~intrepid1_all.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences."I believe you'll have better luck if you use the "Save File" function rather than "Open with..." function when you click on the deb files in firefox.  Once the deb file is downloaded, you can double click on it to install via GDebi.

---

### Post by maduranga on 2008-12-07
thanks catcharavind2003. But pleas someone tell me how to solve the problem I have?

---

### Post by catcharavind2003 on 2008-12-07
> **maduranga said:**
> thanks catcharavind2003. But pleas someone tell me how to solve the problem I have?
Only two commands are needed to install a deb packages and have its dependencies automatically taken care of (if they are available in your repositories). 
The first command will unpack the package, and most probably give an error of missing dependencies. 
The second command instructs apt-get to fix this problem. If these dependencies are available in the repositories, it will install them, and sucessfully finish the installation of downloaded_package.deb. 
They both have to be run as root or using sudo. 
Code: 

dpkg -i downloaded_package.deb 
apt-get -f install 


If you are not too knowledgable yet with apt-get, dpkg, or Debian for that matter, get your new software from the oficial Debian repositories as much as you can (using Synaptic or apt-get). It has been reviewed, packaged and tested to integrate well with your Debian system.

---

### Post by HotShotDJ on 2008-12-07
> **catcharavind2003 said:**
> If you are not too knowledgable yet with apt-get, dpkg, or Debian for that matter, get your new software from the oficial Debian repositories as much as you can (using Synaptic or apt-get). It has been reviewed, packaged and tested to integrate well with your Debian system.I certainly endorse the idea of using repositories whenever possible -- and keeping 3rd party repositories to a minimum.  On those occasions (hopefully few and far between) when a package needs to be downloaded and then installed, the user doesn't even need to use the command line tools.  I have not yet had a failure with simply double-clicking on the deb file.

---

### Post by hailukah on 2008-12-07
> thanks catcharavind2003. But pleas someone tell me how to solve the problem I have?
In Firefox goto Edit | Preferences and click on the application tab.  About 3/4ths down the list is and entry for Software Package.  If you click the drop down to it's right you can choose the default option for the file type.  Mine's set to Always Ask, but you can set it to Save As, or choose to automatically use another application.  The default application to use in Ubuntu is GDebi.

---

