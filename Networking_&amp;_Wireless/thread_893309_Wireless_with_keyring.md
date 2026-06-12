---
title: "Wireless with keyring"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by Simoo on 2008-08-18
Hi all,

Is it possible to stop the network manager from using the gnome keyring?

I am aware that the keyring is a good thing for security but having to type a password in every boot (when it is likely the user has already logged on with a password) just to get on a network is not user freindly.

I also understand if the keyring was going to be accessed for many things through out the session it would be beneficial but it's not. In this case it is annoying a user who has already authenticated him/herself.

I am setting up an xubuntu machine for a small business for a specific job and I can just hear the comment ... "Windows remembered the wireless password so I didn't have to type it in every time" coming back to me!

Any help would be welcome, Thanks.

I should have used the xubuntu flag, sorry. That is what I'm using. Not sure if the same thing happens in Ubuntu.

---

### Post by Simoo on 2008-08-18
OK after a bit more research it would seem there is a fix, or explanation, for Ubuntu here:

[http://ubuntuforums.org/showthread.php?t=804292&highlight=wireless+keyring](http://ubuntuforums.org/showthread.php?t=804292&highlight=wireless+keyring)

But that will not work for xubuntu. The only fix I found for that was to switch no manual network mode instead for roaming but that wouldn't work for me as I couldn't connect with manual mode and it was still asking for my keyring password.

[http://ubuntuforums.org/showthread.php?t=792779](http://ubuntuforums.org/showthread.php?t=792779)

As it stands the user has to log on, then also put their keyring password in to get on the network.

Is there anyway of either excluding netwok manager from the keyring or having the keyring automatically sign in when the user logs on?

---

### Post by Simoo on 2008-08-18
Well I hope this post is useful to someone some day!

To get the keyring to log in with GDM and gnome screen saver you need to install 'libpam-gnome-keyring'

It's probably installed by default on ubuntu but it wasn't on xubuntu 8.04.

After you have installed you will then have the option (a tick box under where you enter your keyring password) to enable the keyring to login with you when you do so in GDM.

It's also worth noting that this method will not work with GDM auto login, which kinda makes sense. Although it would still be nice to have the option for it to do so as auto login suggests you want to boot up with no password requests.

PS.
If one of the admins has time it might be worth relabeling this thread xubuntu. Thanks.

---

### Post by xanikseo on 2009-05-27
Bumping an old thread, sorry, but I made an important discovery which I haven't found anywhere else!
You can make nm-applet not use keyrings to connect to certain wireless hotspots - therefore you don't need a password to unlock the keyring thing as it isn't needed.

Right click on nm-applet -> "Edit connection"
Go to the "Wireless" tab
Click on the wireless hotspot you want to automatically connect to
Click the "Edit" button
At the bottom of the window, you should see a tick box which says "Available to all users".
Tick it and click Apply!

Voila!
You can now auto-login without having to enter the keyring password every time without any workarounds whatsoever.

---

