---
title: "automatic updates does not work"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by mörgæs on 2010-08-20
Hi, I have installed a minimal Ubuntu 10.04 on a Compaq Armada M700. Everything works except the automatic updates.

Another machine with a full installation of 10.04 reminds me of updates several times a week, but not this one.

In System -> Software sources (I believe this is the English name) I have checked 'search for updates daily', but it does not seem to work.

Have I missed a package during installation?

---

### Post by phillw on 2010-08-20
Hi,

if you use the minimal installation CD, the auto update should be turned off by default (We use it for lubuntu), [Method 2](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/KeepLubuntuUptoDate) will add the update icon and the auto update system for you. (The actual methodology of pressing which buttons on your Synaptics package manager could be different, but you're looking to add **update-manager** via Synaptic to install it.

Regards,

Phill.
P.S. I'll subscribe to this thread, if you get stuck do just reply with what desktop (ubuntu/Gnome, xubuntu/xcfe, kubuntu/kde etc.) you have put on and I'll get you the specific instructions.

---

### Post by mörgæs on 2010-08-20
Thanks for a fast answer (and for the subscription).

Update-manager works fine, if I open it by hand. What I am missing is the automatic notifications in the top panel. I have tried to 'add to panel' various icons, but to no avail.

I am installing Ubuntu for a not very techically minded friend. The more automatic steps in the daily routine the better.

It is a classic Ubuntu/Gnome desktop.

---

### Post by murphycc on 2010-08-20
Morgaes,

I too have this problem. I started a thread in the last week, but hadn't seen any solutions to getting the kpackagekit version to auto-update, other than manually updating through terminal.

Here is a link to my thread:

[http://ubuntuforums.org/showthread.php?t=1552242](http://ubuntuforums.org/showthread.php?t=1552242)

Not sure if Phill has any other comments too...

-Chris

---

### Post by zeroseven0183 on 2010-08-20
Do you want your friend to get notified when there are updates or do you want it to automatically update and install the packages?
You can actually hide that activity. Sometimes, doing things silent mode is better.

---

### Post by phillw on 2010-08-20
> **mörgæs said:**
> Thanks for a fast answer (and for the subscription).

Update-manager works fine, if I open it by hand. What I am missing is the automatic notifications in the top panel. I have tried to 'add to panel' various icons, but to no avail.

I am installing Ubuntu for a not very techically minded friend. The more automatic steps in the daily routine the better.

It is a classic Ubuntu/Gnome desktop.

Well, you should have Update Manager in the "admin" area, launch it and click on the **Settings ** button.

If you have the programme running, then it may be quicker for one of the people on IRC to just talk you through it.

If you just click on [Ubuntu Beginners Live Help](http://webchat.freenode.net/?channels=ubuntu-beginners) one of the people will help you.

Regards,
Phill.
P.S. I'm sorry, but I'm away for a couple of days, but I will catch up on how you have gotten on. I know the people on the ubuntu beginners help IRC will quickly talk you through what settings you need, as opposed to us going through all the options with several hours delay.

---

### Post by mörgæs on 2010-08-21
> **zeroseven0183 said:**
> Do you want your friend to get notified when there are updates or do you want it to automatically update and install the packages?
You can actually hide that activity. Sometimes, doing things silent mode is better.

Yes, that is an option. I prefer just having automatic notifications, but if everything else fails, I will try the automatic installation. Thanks.

---

### Post by mörgæs on 2010-08-21
After reading murphycc's thread I found out that **update-notifier** was missing. How embarassing... 

I will try for a few days and see if it works now. Thanks for all the suggestions.

---

### Post by cetoka on 2010-08-21
I have the same problem as you and Murphycc.I asked this question in another forum and the answer I got was:Ubuntu 10.04 update works on some computers but not on others.So what I did is to make a shortcut of updates on the upper panel and I check everyday from there.

---

### Post by mörgæs on 2010-08-23
With **update-notifier** installed it all works well, and this nine years old machine is getting a new life in the free and open world.

---

