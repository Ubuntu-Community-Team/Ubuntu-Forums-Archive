---
title: "Wine has jumble words, won't install MS Firefox"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by seedlings on 2009-01-20
Ubuntu has only been up and running for a couple of days (thanks, minsf).

Here's what happened:
1) Downloaded Wine via "Add Remove".  
2) Downloaded the Windows Firefox to the dextop.  
3) Right click FirefoxSetup.exe on the desktop and select "Open with Wine Windows Program Loader".

A small window opens and it looks like there are 3 lines worth of words typed on top of each other - so jumbled that I can't read it.  The first word looks like "Cannot.." and the only thing I can click is "OK".

I removed Wine, then re-installed it with the command:

```
sudo apt-get install wine
```

But it still does the same thing.

I opened Applications>Wine>Configure Wine and all the words on all the tabs are jumbled together.

If you have advice, that would be great!  One of the other threads said that the Windows Firefox is needed in order to run TurboTax.

---

### Post by gettinoriginal on 2009-01-20
I would suggest that your wine was not installed properly (hiccup), then you tried to use it to install something.  In terminal copy/paste:
```
sudo apt-get --purge remove wine
```
```
sudo apt-get --purge autoremove
```
This way you get rid of wine and any of its config files.  Then I would try installing it from Synaptic instead of Add/Remove.

P.S. Is there any special reason you need "windows firefox" ??

---

### Post by seedlings on 2009-01-20
> **gettinoriginal said:**
> I would suggest that your wine was not installed properly (hiccup), then you tried to use it to install something.  In terminal copy/paste:
```
sudo apt-get --purge remove wine
```
```
sudo apt-get --purge autoremove
```
This way you get rid of wine and any of its config files.  Then I would try installing it from Synaptic instead of Add/Remove.

P.S. Is there any special reason you need "windows firefox" ??

Sorry, but what do you mean by "installing it from Synaptic instead of Add/Remove"?  Is Synaptic who wrote Wine?  I'll look for a website.

I "need" windows firefox because I'd like to run Turbo Tax.  Instructions are here:
["http://ubuntuforums.org/showthread.php?t=1035581&highlight=turbo+tax"]("http://ubuntuforums.org/showthread.php?t=1035581&highlight=turbo+tax")

---

### Post by gettinoriginal on 2009-01-20
No, Synaptic is your package manager, you will find it at System > Administration > Synaptic Package Manager,(it will ask for your password) wait for it to open and then in the search box type Wine. Check the box for installation, then go the green arrow at the top marked "Apply" and it will install Wine for you.  Then close Synaptic Package Manager.  But before you try to install anything with it, check at Applications to make sure Wine is installed correctly this time. :p

---

