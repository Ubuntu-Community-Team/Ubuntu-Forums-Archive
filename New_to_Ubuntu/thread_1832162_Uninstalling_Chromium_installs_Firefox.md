---
title: "Uninstalling Chromium installs Firefox?"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by Dyzphagia on 2011-08-24
Well I installed Chromium to see how I liked it. I didn't, I went to remove it via package manager and it says it will install Firefox in it's place. I really don't need Firefox and I have tried  ```
sudo apt-get remove Chromium
``` It said it was a virtual package that can't be removed, then I tried  ```
sudo apt-get purge Chromium
``` It said it was a virtual package that can't be removed and that lib-camel-1.2-26 was automatically installed and is no longer required, so I used  ```
sudo apt-get autoremove
``` It removed it, but I still sadly have chromium.  How can I remove Chromium and not install Firefox?

---

### Post by aeiah on 2011-08-24
isnt it apt-get remove chromium-browser?

either way, im not quite sure why it is installing firefox. what browser are you planning on using? perhaps if you set it as your default browser, ubuntu wont try and install firefox for you.

```

sudo update-alternatives –config browser
```

should do the trick, although it might not be 'browser'. you could just issue ```
sudo update-alternatives
``` and go through until you get to the browser section

---

### Post by Dyzphagia on 2011-08-24
I tried the ```
sudo update-alternatives --config browser
```. I get an error stating that there are no alternatives for browser. Nightly is set as my default. I then tried ```
sudo apt-get remove chromium-browser
```, yet it still wishes for me to install Firefox.  Also I can no longer use ctrl + alt + t to bring up the terminal.

---

### Post by cottfcfan on 2011-08-24
Firefox is part of the default installation.
Personally I would not remove it.
The rule of thumb seems to be, if its part of the default installation, leave it installed.
If removing chromium reinstalls Firefox, I would let it.

---

### Post by Dyzphagia on 2011-08-24
So in the end I'm going to be stuck with both Firefox and Nightly? Almost bugs me as much as my unity problem

---

### Post by cottfcfan on 2011-08-24
You don't have to be stuck with anything. You can install as many Browsers as you like. I have Firefox, Chrome & Opera installed.
It's just safer not to remove Firefox, that's all.

---

### Post by Dyzphagia on 2011-08-24
Well looks like I'm going to just remove Chromium and reinstall Firefox. Thanks for the help.

---

### Post by dniMretsaM on 2011-08-24
What if you tried:
```
sudo apt-get remove chromium-browser
```You might get different results since the actual package name is chromium-browser, not chromium.

---

### Post by Dyzphagia on 2011-08-24
Yeah somebody above shown me that, tried it and it still came out to the same conclusion. Oh well, I'm just going to do Firefox and Nightly

---

### Post by lovinglinux on 2011-08-24
> **Dyzphagia said:**
> Yeah somebody above shown me that, tried it and it still came out to the same conclusion. Oh well, I'm just going to do Firefox and Nightly

Instead of using Firefox nightly, use the beta or aurora channels, so you get only one Firefox. We can do that with the mozillateam ppa.

See [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

---

