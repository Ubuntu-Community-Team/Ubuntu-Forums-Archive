---
title: "Flash for Firefox in Ubuntu"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by vicbee on 2010-07-11
Ok, so I am really new at this... and very quickly getting really frustrated with this.  I'm simply trying to install Flash (Adobe) and the first thing I'm asked is "what version" from a list of several .endings (!!!) wtf?!? then, whatever I download is only a list of files with no application...  I don't know, I may not be techy enough to figure this OS out with a need so simple I don't have to think about it in Windows.

Can someone explain to me how to install Flash in Firefox for Ubuntu please before I junk this OS and revert back to click, install, moving on....?  Much appreciated.

---

### Post by Brii on 2010-07-11
> **vicbee said:**
> Ok, so I am really new at this... and very quickly getting really frustrated with this.  I'm simply trying to install Flash (Adobe) and the first thing I'm asked is "what version" from a list of several .endings (!!!) wtf?!? then, whatever I download is only a list of files with no application...  I don't know, I may not be techy enough to figure this OS out with a need so simple I don't have to think about it in Windows.


Can someone explain to me how to install Flash in Firefox for Ubuntu please before I junk this OS and revert back to click, install, moving on....?  Much appreciated.
**EDIT:
Things aren't usually installed the same way on ubuntu as in windows. Where as you just download it and use the wizard to install it. 

There's about 3 ways to install things in Ubuntu, which are all mentioned down there, through Synaptic Package Manager, Ubuntu Software Center, and my favorite the terminal. Here's that way

Open terminal
Applications > Accessories > Teminal

and type in:

```
sudo apt-get install flashplugin-nonfree
```

I'm pretty sure that's it. If that doesn't work come back.

---

### Post by gandaran on 2010-07-11
it's very simple to install flash, open synaptic package manager, type flash in search box, there are three adobe flash packages there, don't worry, all of them have the same flash version, choose the flashplugin-installer package mark for install and click the apply button, thats all just wait till it finishes downloading the flash then try it out in firefox.
I recommend this flashplugin-installer package because it's the default ubuntu package and it gets updated when a new flash version comes out.

---

### Post by Gone fishing on 2010-07-11
You need to install software using apt-get, synaptic etc. If you go to Administration > synaptic you will find masses of software you can install.

You need to open synaptic and install ubuntu-restricted-extras. This enables you to view proprietary formats such as flash

Have a look at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I would also follow these [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) instructions and this will allow you to play encrypted DVDs etc

---

### Post by kukker32 on 2010-07-11
there's also the software center.. programs -> ubuntu softwarecenter search for flash.. and install

---

### Post by lovinglinux on 2010-07-11
If you find the above instructions complicated, install [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/) extension for Firefox. It will install the latest flash according to your browser architecture and remove possible conflicting plugins.

---

### Post by TCHebb on 2010-07-11
You may be finding all the different instructions above confusing, but they're really all doing the same thing: Installing the "flashplugin-installer" package. apt-get, Synaptic, and the Ubuntu Software Center are all ways of installing packages. Personally, I use apt-get, but new users coming from Windows will find the Software Center easier.

Likewise, the packages flashplugin-installer, flashplugin-nonfree, and ubuntu-restricted-extras all install the same package for Flash support: flashplugin-installer. If you only want Flash, install that one, as flashplugin-nonfree is a dummy package that just installs flashplugin-installer. However, I would suggest installing ubuntu-restricted-extras instead, which installs, along with flashplugin-installer, many other packages to support codecs such as MP3, AVI, and MPEG.

So, to install flash:
Open Ubuntu Software Center and search for "restricted extras."
Install "Ubuntu Restricted Extras."
Restart Firefox.

---

### Post by audiomick on 2010-07-11
+1 : install ubuntu-restricted-extras. I installs flash and a number of other things (mp3 an so on.) Also, have a look at the link in lovinlinux's signature. He has a lot of good advice to offer on Flash and optimising firefox.

---

### Post by gandaran on 2010-07-11
well I think this is a perfect thread on how to install flash, it has everything, if a newbie has any doubts this one will help understand how Ubuntu works, perfect!
this thread should be in sticky threads!

---

### Post by Gone fishing on 2010-07-11
I think I'd also recommend installing vlc and/or smplayer

---

