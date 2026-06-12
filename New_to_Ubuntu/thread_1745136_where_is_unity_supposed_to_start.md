---
title: "where is unity supposed to start?"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by outleradam on 2011-04-30
I upgraded my netbook from Ubuntu NetBook Edtition using the standard method presented to me when I turned on the Netbook.  I selected "Use package maintainer's version" for each option presented.  Upon reboot,  the Unity interface does not start.  I am presented a purple screen with the new background, but the menus are all absent and the netbook does nothing.

In order to start the interface, I must press ctrl+alt+F2, log in as my username, and then type "unity".   Then when I switch back to the X interface with ctrl+alt+f7, the unity inteface loads and works properly.

How am I supposed to start it?   I've tried using the rc.local
```

export DISPLAY=:0
sudo -u adam unity
```
but it does not work that way either.   I must do it manualy.    How can I get it working again?

---

### Post by outleradam on 2011-05-02
):P Anyone?   I was running Ubuntu Netbook Edition, now unity must be started manually.  Any way to fix this?

---

### Post by elliotcroft on 2011-05-02
Is this before or after the login screen?

---

### Post by outleradam on 2011-05-03
I auto-login.   I see no graphics on the screen at all.   Just the proper background.
 
 
I can start apps like nautilus from a terminal using ctrl+alt+F2
```
export DISPLAY=:0
natuilus
```
The problem is that I have no default interface until I start unity.

---

### Post by Paqman on 2011-05-03
What happens if you create a new account and log in to it? If it starts Unity ok then it's just the settings in your account that are messed up. If not then it's system-wide.

---

### Post by outleradam on 2011-05-10
i did 
```
 sudo useradd adam2
sudo passwd adam2

```
then i logged out and logged in as adam2.  same problem.

---

### Post by outleradam on 2011-05-12
Anyone?  Do I have to format this computer and start over?

---

### Post by coljohnhannibalsmith on 2011-05-12
I like many others have had many problems with online distro upgrades.

These often leave behind legacy packages that cause problems after the upgrade.

Personally, I usually have better luck with bare-metal installs/upgrades.  This way 'no' legacy packages are left behind.  ***It sounds to me like you're at this point.***

BTW, it is my understanding that an upgrade from CD option is now available; and I've read that some users are having good experiences with it.  There may also be an OS repair feature on the CD; but don't quote me on this...




Hannibal

---

### Post by sadaruwan12 on 2011-05-12
> **coljohnhannibalsmith said:**
> I like many others have had many problems with online distro upgrades.

These often leave behind legacy packages that cause problems after the upgrade.

Personally, I usually have better luck with bare-metal installs/upgrades.  This way 'no' legacy packages are left behind.  ***It sounds to me like you're at this point.***

BTW, it is my understanding that an upgrade from CD option is now available; and I've read that some users are having good experiences with it.  There may also be an OS repair feature on the CD; but don't quote me on this...




Hannibal

I do agree with him some proprietary drivers like from nVIDIA might cause a problem so better if you can do a clean install or do a upgrade from the CD.

---

### Post by outleradam on 2011-05-12
> **sadaruwan12 said:**
> I do agree with him some proprietary drivers like from nVIDIA might cause a problem so better if you can do a clean install or do a upgrade from the CD.
 I have never installed any nVIDIA drivers.
 
I'm telling you it went like this..  
1. Fresh install of Ubuntu 10.10 Netbook edition.
2. light usage,  performed all standard upgrades, no backports or pre-release, no modifications.
3. When asked, I upgraded...  Selected "use package maintainer's version".  
4. On reboot, I had no Unity interface. I had it before the upgrade on 10.10 Netbook, and it disappeared with the upgrade to 11.04.  
 
Now I've got no interface, only a blank X display with a background.  Unity requires me to manually go to a terminal and type "unity".
 
So, I guess I'll reformat.  It seems simple, but hey..  Noone knows about Unity yet.

---

