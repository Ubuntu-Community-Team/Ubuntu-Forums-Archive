---
title: "VMware or an alternative and use of dokuwiki"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by rovington on 2010-06-22
I have just installed the Ubuntu server on an old PC, up and running fine, got to grips with web forwarding and dynamic IP solved.
 
Tried to install the Vmare and wow what a nightmare ! I tried all sorts of methods suggested by different sites and cannot get VMware to install, have given up.
 
I have never before used Ubuntu so its all new to me.
 
I am trying to work out the best method of creating webs on it, I particulary like the idea of dokuwiki, having never used the OS before I am not sure how to approach such an install or even if it will work. Ideally I would want to be able to log in to a control panel interface for dokuwiki but I am at a loss as to which methods I should be using, am I with the right OS?
 
I have read lots have had problems with VMware, is there an alternative I can use, I feel like I have learned a college course worth of Ubuntu today, it seems a pity to give it up now.
 
Any suggestions?

---

### Post by cariboo on 2010-06-23
VirualBox is in the repositories, I use it quite a bit for testing other distributions. You can install by typing at the prompt:

```
sudo apt-get install virtualbox-ose
```

Dokuwiki is in the repositories also, from the prompt type:

```
sudo apt-get install dokuwiki
```

The above commands assume you did a default server install with no gui.

---

### Post by Windows Nerd on 2010-06-23
> **cariboo907 said:**
> VirualBox is in the repositories, I use it quite a bit for testing other distributions. You can install by typing at the prompt:

```
sudo apt-get install virtualbox-ose
```Dokuwiki is in the repositories also, from the prompt type:

```
sudo apt-get install dokuwiki
```The above commands assume you did a default server install with no gui.

I would like to add a note:

The package in the repositories for Virtualbox is the Open-Source Version. That means no USB support for your Virtual Machines, which you get in the PUEL version, which is NOT Open-Source. If you wish to use USB's with VirtualBox, use the PUEL version, which you can find on the VirtualBox website at:  [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) .  Choose the one for **Linux** hosts. 

Just letting the OP know, though I think you already know this, and just forgot to mention this.

Scott

---

