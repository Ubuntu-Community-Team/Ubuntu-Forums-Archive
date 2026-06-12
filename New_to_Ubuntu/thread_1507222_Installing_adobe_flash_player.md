---
title: "Installing adobe flash player"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by ex-para on 2010-06-11
I have installed Ubuntu 8.04 on a laptop and I am having trouble installing Adobe Flash Player, I have other laptops with the same OS and I can't remember having this problem with Adobe. I would appreciate any information about it.

---

### Post by TeoBigusGeekus on 2010-06-11
If you install the restricted extras
```
sudo apt-get install ubuntu-restricted-extras
```
you will have flash support.

---

### Post by rcayea on 2010-06-11
Or, as another option, you can install Ubuntu-Tweak. Download it from its website and then you can easily find Flash in the list of installable items.

---

### Post by zipperback on 2010-06-11
Open a terminal window. 

Click on Applications -> Accessories -> Terminal

Now copy and paste the following line of text into the terminal window.

sudo apt-get install flashplugin-nonfree

When prompted for your password, enter it and press Enter.

It will download and install flash for you.

You don't need Ubuntu Tweak to install Flash.

When it is done, close the terminal window, and then launch your browser. You can test it by going to youtube.com or similar site.

- zipperback
:popcorn:

---

### Post by slakkie on 2010-06-11
[http://blog.opperschaap.net/2009/11/13/upgrade-flash-on-ubuntu-after-a-release-upgrade/](http://blog.opperschaap.net/2009/11/13/upgrade-flash-on-ubuntu-after-a-release-upgrade/)

Do this and you are good to go with flash.

---

### Post by pricetech on 2010-06-11
Are you running 32 bit or 64 bit Hardy ??

---

### Post by rcayea on 2010-06-12
> **zipperback said:**
> Open a terminal window. 

Click on Applications -> Accessories -> Terminal

Now copy and paste the following line of text into the terminal window.

sudo apt-get install flashplugin-nonfree

When prompted for your password, enter it and press Enter.

It will download and install flash for you.

You don't need Ubuntu Tweak to install Flash.

When it is done, close the terminal window, and then launch your browser. You can test it by going to youtube.com or similar site.

- zipperback
:popcorn:



Ubuntu-Tweak is just another option. That is all it is.

---

### Post by Jakiejake on 2010-06-12
64 or 32 bit?
What browser?

---

### Post by fremantle on 2010-06-12
restricted extras add a whole lot of stuffs, which u might not want. just get flash playr individually

---

### Post by ex-para on 2010-06-12
thanks for the replies, 32 bit Firefox.

---

### Post by Jakiejake on 2010-06-12
> **ex-para said:**
> thanks for the replies, 32 bit Firefox.

Close Firefox then Run this command in terminal
> apt-get install flashplugin-installer
Then Open Firefox and enjoy!

---

### Post by ex-para on 2010-06-13
Thanks again for the replies.

---

### Post by Jakiejake on 2010-06-25
> **ex-para said:**
> Thanks again for the replies.

Thats Okay
Enjoy Ubuntu!

---

