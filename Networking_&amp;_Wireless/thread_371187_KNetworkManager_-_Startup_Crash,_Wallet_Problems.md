---
title: "KNetworkManager - Startup Crash, Wallet Problems"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by DannyG on 2007-02-26
I have got my Wireless Card (BCM4318) working no problem, and I installed KNetworkManager (Kubuntu obviously).

When I start my laptop up, I log in and see the KNetworkManager icon for a moment, and then it disappears and becomes a blank area where it used to be. The wallet manager then asks me for the the password so it can unlock the WEP key, so I put the password in but nothing else happens.

So I log off, and log back, and this time KNetworkManager opens and stays open, and I am again prompted for the Wallet password. I put in the wallet password but then KNetworkManager pops up and asks me for my WEP key again!

What the hell is going on?

---

### Post by DannyG on 2007-02-26
Update:

I changed my session to:

[B]On Login:
-> Start with an empty session[/B]

Now when I start my laptop, KNetworkManager doesn't start, so is there a way to add KNetworkManager to the startup services?

---

### Post by mafitzpatrick on 2007-04-08
I'm having the same problem - it seems slightly crazy to ask for your login password, immediately after login to confirm you want to start a standard feature (networking).

Does anyone know of a way to "always allow" KNetworkManager access to the details in the Wallet?  Other elements of KDE appear to have that ability, but I cannot find the option in KNM.

Thanks,

---

### Post by Fitzcarraldo on 2007-04-08
^See the following thread (one of several on this topic in the Ubuntu forums):

[http://ubuntuforums.org/showthread.php?t=192281](http://ubuntuforums.org/showthread.php?t=192281)

---

### Post by mihail on 2007-04-21
> **DannyG said:**
> Update:
Now when I start my laptop, KNetworkManager doesn't start, so is there a way to add KNetworkManager to the startup services?

I have also changed the setting to "Start with an empty session". In addition, I created 'knetworkmanager.desktop' file to /usr/share/autostart with the following contents:

```
[Desktop Entry]
Encoding=UTF-8
Name=knetworkmanager
GenericName=Network Manager
Exec=knetworkmanager
Terminal=false
X-KDE-autostart-after=panel
X-KDE-StartupNotify=false
X-DCOP-ServiceType=Unique
X-KDE-autostart-condition=klipperrc:General:AutoStart:true
OnlyShowIn=KDE;
Categories=Qt;KDE;Utility;X-KDE-Utilities-Desktop;
Type=Application
```

Now knetworkmanager is started for each and every user during login. User specific autostart scripts are placed into ~/.kde/Autostart. More information is available at: [http://gentoo-wiki.com/HOWTO_Autostart_Programs](http://gentoo-wiki.com/HOWTO_Autostart_Programs)

However, sometimes I STILL have the problem DannyG described; knetworkmanager just displays an empty place on tray. Logout-login (as DannyG said) resolves the problem, but I might need to enter my WPA key manually. ...and Yes, I have my wallet subsystem configured properly. For instance, Kopete works perfectly.

What I'm trying to do, is that knetworkmanager could log on to WPA wireless network w/o asking any passwords (doesn't make ANY sense to enter different passwords when logging on to computer).

---

### Post by mihail on 2007-04-21
> **Fitzcarraldo said:**
> ^See the following thread (one of several on this topic in the Ubuntu forums):

[http://ubuntuforums.org/showthread.php?t=192281](http://ubuntuforums.org/showthread.php?t=192281)

This article seems to focus mainly on Ubuntu and Gnome. I'm not an expert on this issue, but at least I'm not using Gnome keyrings on KDE (I'm using Kubuntu 6.10). There was one reply from user using Xubuntu, however...

I'm still trying to browse through ubuntu forums and find Kubuntu & knetworkmanager specific help. ...without too much luck at the moment...

---

### Post by mihail on 2007-04-21
Just one addition: just updated to Kubuntu Feisty - still I have the same problem. After first login, knetworkmanager seems to crash. Empty slot is shown on tray, as DannyG described. Have to say: this Linux thing is still full of crappy things :(

Linux community should fix the following things before ANY new things are developed:
- I-have-to-tweak-my-xorg.conf-to-use-"special"-resolutions
- Wireless networking

And yes, I'm personally willing to help to get these important things to get sorted out!

---

### Post by dejitarob on 2007-04-21
> **mihail said:**
> Just one addition: just updated to Kubuntu Feisty - still I have the same problem. After first login, knetworkmanager seems to crash. Empty slot is shown on tray, as DannyG described. Have to say: this Linux thing is still full of crappy things :(

Linux community should fix the following things before ANY new things are developed:
- I-have-to-tweak-my-xorg.conf-to-use-"special"-resolutions
- Wireless networking

And yes, I'm personally willing to help to get these important things to get sorted out!
Have you tried searching for problems with your specific network card? I understand getting your setup to work perfectly can be frustrating, but Linux is not unique in the regard of requiring some tinkering. At the very least, Windows takes quite a bit of installing (sometimes reinstalling) drivers and rebooting. In my experience Linux is much easier to maintain once you get it working.

I installed Fiesty from scratch and knetworkmanager works great for my wireless + wpa2 connection. The only bit of annoyance is the prompting for my kwallet manager password every time I startup. It would be great if there was an option to store it simply in plain text somewhere so it didn't require kwallet manager. I would make a patch but I have no idea even what coding language it is in let alone how to do create a patch, so I'll just wait patiently :]

---

### Post by dejitarob on 2007-04-21
This bug appears to describe your problem: [https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/94831](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/94831)

---

### Post by mihail on 2007-04-22
> **dejitarob said:**
> I installed Fiesty from scratch and knetworkmanager works great for my wireless + wpa2 connection. The only bit of annoyance is the prompting for my kwallet manager password every time I startup. It would be great if there was an option to store it simply in plain text somewhere so it didn't require kwallet manager. I would make a patch but I have no idea even what coding language it is in let alone how to do create a patch, so I'll just wait patiently :]

I solved this problem by setting my kwallet password to empty string (=no password at all). Yes, of course this might be a bit unsecure, but now I only need to enter password once (when loggin on to KDE).

---

### Post by dejitarob on 2007-04-23
Ah thanks. I thought when I first setup kwallet it wouldn't let me do this but when I went to 'change password' just now it did.

---

### Post by Eriol_Ancalagon on 2007-05-21
> **mihail said:**
> I solved this problem by setting my kwallet password to empty string (=no password at all). Yes, of course this might be a bit unsecure, but now I only need to enter password once (when loggin on to KDE).
I've done the same.


Does anybody else think having a password to the wallet being somewhat insane?  Heck, even in Windows these days you need to log into an account.  Why the hell do you need to log in AGAIN for "secure" areas?  SSO is a beautiful thing.  All other info is accessed per-user, so why not this stuff?  Sure if you have some custom reason to gate access to certain things cross-users, MAYBE there's a reason to have a password, but for user-specific wallets?  Why would you even NEED a password?  It's in your user dir, that should be enough.

---

### Post by davebailey on 2007-06-02
Yeah, setting a blank password is a **great** idea! That way, any software running on your system can access ALL your accounts and passwords say, to capture them for further use, without your being any the wiser.

The extra login is to give you a chance to say, no, actually, I don't want to give the software that access.

Better to set a short password that's easy to type in than none at all.

---

