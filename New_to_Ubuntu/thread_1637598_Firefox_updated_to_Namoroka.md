---
title: "Firefox updated to Namoroka?"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by Shadowgamon on 2010-12-04
I updated firefox today and it is now Namoroka... whats up with that?

I did also install firefox 4.0 a little while ago, but I was fairly sure it was alongside , considering it got a separate upgrade. 
 
How do remove then reinstall all firefox data? I want a completely clean install of firefox (minus 4.0 beta since the linux version is incomplete/not much different)

---

### Post by susema on 2010-12-04
```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa && sudo apt-get update
```
```
sudo apt-get install firefox-4.0
```

---

### Post by Shadowgamon on 2010-12-04
i'm not trying to get firefox 4, I'm trying to set firefox ( and now thunderbird X_X)  back to their natural and current official releases, cause they're both set to pending releases

---

### Post by BeachBuddah on 2010-12-04
Susema,

I'm watching this thread.  I TRIED to install ff4.0 the other day but was completely baffled by the instructions on the mozilla website.  Thank you for posting the apt-get option.   BUT...(there's always a but)

Now that it is installed, how do I access it - it didn't show up on the menu (that would be too easy) and I'm not sure what to click elsewhere in the file system.

TIA for your help.

---

### Post by lovinglinux on 2010-12-05
> **Shadowgamon said:**
> I updated firefox today and it is now Namoroka... whats up with that?

I did also install firefox 4.0 a little while ago, but I was fairly sure it was alongside , considering it got a separate upgrade. 
 
How do remove then reinstall all firefox data? I want a completely clean install of firefox (minus 4.0 beta since the linux version is incomplete/not much different)

The problem is that you are using the ubuntu-mozilla-daily ppa to install Firefox 4, which also updates Firefox 3.6 and Thunderbird with the latest unstable packages.

To revert to Firefox instead of Namoroka you need to disable the ppa from the Software Center and reinstall Firefox.

```
sudo apt-get install --reinstall firefox
```

See my tutorial for other methods of installation of Firefox 4 that do not interfere with 3.6.

[http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html](http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html)

---

### Post by Shadowgamon on 2010-12-05
> **lovinglinux said:**
> The problem is that you are using the ubuntu-mozilla-daily ppa to install Firefox 4, which also updates Firefox 3.6 and Thunderbird with the latest unstable packages.

To revert to Firefox instead of Namoroka you need to disable the ppa from the Software Center and reinstall Firefox.

```
sudo apt-get install --reinstall firefox
```See my tutorial for other methods of installation of Firefox 4 that do not interfere with 3.6.

[http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html](http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html)
uh...
How do I go about doing that?
I also have no idea how to go about uninstalling it :X
> **BeachBuddah said:**
> Susema,

I'm watching this thread.  I TRIED to install ff4.0 the other day but  was completely baffled by the instructions on the mozilla website.   Thank you for posting the apt-get option.   BUT...(there's always a but)

Now that it is installed, how do I access it - it didn't show up on the  menu (that would be too easy) and I'm not sure what to click elsewhere  in the file system.

TIA for your help.

its probably under the name minefield

---

### Post by lovinglinux on 2010-12-05
> **Shadowgamon said:**
> uh...
How do I go about doing that?
I also have no idea how to go about uninstalling it :X

Open Ubuntu Software Center, then click "Edit >> Software Sources", then click the "Other Software" tab, then untick the line that contains **ubuntu-mozilla-daily**, then click "Close".

Then execute this on a terminal:

```
sudo apt-get update
sudo apt-get install --reinstall firefox
```

---

### Post by Shadowgamon on 2010-12-05
> **lovinglinux said:**
> Open Ubuntu Software Center, then click "Edit >> Software Sources", then click the "Other Software" tab, then untick the line that contains **ubuntu-mozilla-daily**, then click "Close".

Then execute this on a terminal:

```
sudo apt-get update
sudo apt-get install --reinstall firefox
```
Ok thats a lot simpler than I thought it would be :) 

thanks

---

