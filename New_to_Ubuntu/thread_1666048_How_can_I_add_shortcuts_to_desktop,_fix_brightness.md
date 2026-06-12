---
title: "How can I add shortcuts to desktop, fix brightness adjustement and suspend operation?"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by sanurmi on 2011-01-13
I just installed Ubuntu 10.10 Netbook edition and I recognized that I can't add icons with shortcuts to the desktop at all, it it really so? If I press right click, nothin happens etc.

I have a Samsung N220 and another big problem is that suspend is not working and brightness adjustements button neither.

1) how to add shortcuts to the desktop?

2) How Can I fix the suspend operation? It just kill the machine.

3) How Can I fix brightness adjustement in Samsung N220?

Thanks a lot! 
Sami

---

### Post by ajgreeny on 2011-01-13
You can't add any shortcuts to the unity desktop, which is why it is not a very well liked system at the moment.  Logout and in again choosing **ubuntu-desktop** from the session menu and you will be back to a gnome desktop, where you can do all those things that you want.

Unfortunately I can't help with the suspend or brightness problems.

---

### Post by sanurmi on 2011-01-13
where is that session menu? I logged out, but i couldn't see any session menu. Just password filed and after that my 10.10 netbook dekstop opened. I saw the same advice somewhere before so is this really working in the latest Netbook or am I blind :)

---

### Post by ajgreeny on 2011-01-14
The login screen has a box for the username, or you can then just click on it when you see your name displayed.  After that the password box appears, where you type in your user password.  Below that and to the right in the status bar, there is an expandable "Session" box; click on that and the various options will appear.  This last step must be done before you hit enter after typing your password.

---

### Post by sanurmi on 2011-01-14
> **ajgreeny said:**
> The login screen has a box for the username, or you can then just click on it when you see your name displayed.  After that the password box appears, where you type in your user password.  Below that and to the right in the status bar, there is an expandable "Session" box; click on that and the various options will appear.  This last step must be done before you hit enter after typing your password.


Hi and thanks helping me!

I haven't that session box at all and I recognized that I haven't Ubuntu-desktop installed at all. I installed Ubuntu Netbook from USB stick. No I tried to install Ubuntu desktop but there isn't still that sessionbox. How can I change my desktop to that installed Ubuntu-Desktop?

Thanks
Sami

EDIT: I have the asutomatic log on without passwords and that's why there wasn't session box at all. SO this is solved, THANKS! I would be very happy if someone can help me to fix that Samsung N220 brightness adjustment problem, because now screen is dark, too dark.

---

### Post by dirtyhabanero on 2011-02-25
sanurmi:

There is one workaround for allowing users to add icons to the deskopt for UNE, and I can't find where I saw it last time...

Open terminal and type

gconf-editor

A window will open with some tree menu things on the left. Navigate to 

Apps > Nautilus > Preferences

Scroll down until you see a setting called show_desktop. Now you need to check this box somehow. I usually right-click and then select "Unset Key". Since the default value is false (unchecked). Go back to your desktop and you should be able to see it.

The only problem with this method is that it resets when you shutdown. 

Here is the original thread...[http://ubuntuforums.org/showthread.php?p=9045664](http://ubuntuforums.org/showthread.php?p=9045664)

And while I'm looking up more info on the topic, here is another site that explains a bit
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-netbook-default-settings/+bug/518626](https://bugs.launchpad.net/ubuntu/+source/ubuntu-netbook-default-settings/+bug/518626)

---

