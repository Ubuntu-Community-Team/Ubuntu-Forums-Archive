---
title: "How do I download software from website ?"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by ericstrom on 2009-05-03
How do I download software (Anki) directly from a web site? Add/Remove and Synaptic both see this software but they see an older version (which has a bug). I need the latest version. I go to the website , double click on the software I want to download and then I get the following error :

/tmp/anki_0.9.9.7.7-1_all-1.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

The site I'm going to is :  [http://ichi2.net/anki/download/index.html](http://ichi2.net/anki/download/index.html)


What does this error mean ? How do I download this software. New to Linux and using Jaunty....please help.

---

### Post by jespdj on 2009-05-03
Try this: Open a terminal (Applications > Accessories > Terminal). Type in the following command:
```
sudo dpkg -i /tmp/anki_0.9.9.7.7-1_all-1.deb
```
Enter your password when it asks for it.

---

### Post by skompier on 2009-05-03
Go to Add/Remove and search for gdebi. Make sure that's installed, if not, install it.

---

### Post by ericstrom on 2009-05-03
> **jespdj said:**
> Try this: Open a terminal (Applications > Accessories > Terminal). Type in the following command:
```
sudo dpkg -i /tmp/anki_0.9.9.7.7-1_all-1.deb
```
Enter your password when it asks for it.

I tried that just now. Seemed like a really simple solution. But I got the following error :

eric@eric-desktop:~$ sudo dpkg -i /tmp/anki_0.9.9.7.7-1_all-1.deb
[sudo] password for eric: 
dpkg: error processing /tmp/anki_0.9.9.7.7-1_all-1.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /tmp/anki_0.9.9.7.7-1_all-1.deb

Any suggestions ?

---

### Post by The Cog on 2009-05-03
> I go to the website , double click on the software I want to download and then I get the following error
The thing to do is to right-click on teh link in the browser and choose to download it. Once it is saved on your desktop, then **sudo dpkg -i Deskdop/anki_0.9.9.7.7-1_all-1.deb** should work, as should just double-clicking the icon for the file on the desktop.

---

### Post by arapa on 2009-05-03
Does file still exist in you tmp folder? Try re-downloading it to your home directory.

Then navigate to where you downloaded using nautilus (click Places > Home from the top panel). Right click on the file and choose properties. Select the 'Open With' tab. If 'GDebi Package Installer' is in the list make sure it is selected and then exit. Now try double clicking on the file.

---

### Post by blueridgedog on 2009-05-03
> **The Cog said:**
> The thing to do is to right-click on teh link in the browser and choose to download it. Once it is saved on your desktop, then **sudo dpkg -i Deskdop/anki_0.9.9.7.7-1_all-1.deb** should work, as should just double-clicking the icon for the file on the desktop.

Or....just save the package to the desktop, then simply double click it.  Firefox is brain dead about how to open it, but the OS will handle it just fine.

---

### Post by Techproof on 2009-05-03
> **ericstrom said:**
> How do I download software (Anki) directly from a web site? Add/Remove and Synaptic both see this software but they see an older version (which has a bug). I need the latest version. I go to the website , double click on the software I want to download and then I get the following error :

/tmp/anki_0.9.9.7.7-1_all-1.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

The site I'm going to is :  [http://ichi2.net/anki/download/index.html](http://ichi2.net/anki/download/index.html)


What does this error mean ? How do I download this software. New to Linux and using Jaunty....please help.

One thing you will need to keep in mind in future is that synaptic and the add/remove apps in linux will only search the default ubuntu ***[COLOR=Red]repositories[/COLOR]***, on the site you are downloading the software for they may list a reposiroty you can add to your repositories list in synaptic to download future versions of the software. The version you are currently seeing will be updated when the ubuntu repositories are updated to the latest versions of the software that is available and has been confirmed as a stable release.

Look up more information on "repositories" for assistance with installing packages in the future. From experience Ubuntu has one of the largest default repositories I have found out of the few distros I have used.

---

