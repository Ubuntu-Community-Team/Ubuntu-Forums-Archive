---
title: "How to install new login screen?"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by ArpitRaj on 2010-12-26
I have installed Ubuntu 10.10 64-bit recently.
I downloaded a theme for login screen of .tar.gz type
When I goto Appearance Preferences>Themes>Install> Select and Open respective .tar.gz file, an error window pops up saying its not a valid theme.

How can I install new login screens/themes? Where should this file be and do I need any other software?

Arpit

---

### Post by walt.smith1960 on 2010-12-27
No guarantee but you could try this.  Download the file to your hard drive and try to install from the hard drive file. I've had success with this in the past.  Theme installers do seem 'fidgety' for want of a better term.

---

### Post by mcduck on 2010-12-27
Sorry to tell you, but the theme you downloaded is most likely intended for the old version of GDM.

Recent Ubuntu versions use GDM2 instead, and it doesn't (yet) have support for such themes. (It *does* allow the user to choose background image, GTK theme, fonts and icons for the login screen quite easily, though, which is something the old GDM couldn't do...)

---

### Post by ArpitRaj on 2010-12-27
> **mcduck said:**
> Sorry to tell you, but the theme you downloaded is most likely intended for the old version of GDM.

Recent Ubuntu versions use GDM2 instead, and it doesn't (yet) have support for such themes. (It *does* allow the user to choose background image, GTK theme, fonts and icons for the login screen quite easily, though, which is something the old GDM couldn't do...)

So how can I install new themes or I can't at all right now? Can't I update the GDM version, if yes, then how?

Also how can I check whether I have a stable version of Ubuntu or a beta version? I downloaded the "x64 iso file" on 19 dec 2010.

---

### Post by mcduck on 2010-12-27
> **ArpitRaj said:**
> So how can I install new themes or I can't at all right now? Can't I update the GDM version, if yes, then how?

Also how can I check whether I have a stable version of Ubuntu or a beta version? I downloaded the "x64 iso file" on 19 dec 2010.

Like I said, GDM2 doesn't use that kind of themes. And it's not a question of updating. To use the themes for the old GDM version you'd have to *downgrade*. Not recommended.

Like I said, the GDM2 used in 10.10 uses same kind of theming (with GTK2 themes, icons and other options) you can use to customize your own desktop.

No Ubuntu release is currently at Beta. So you can't have a beta version. Also you already said in your first post that you are running 10.10? That's the latest stable version.

---

### Post by mcduck on 2010-12-27
If you want to change how your login screen looks like, all you have to do is launch the Appearance Properties-dialog (the same one you use to change your own desktop settings) as user "gdm".

So, open a terminal, and run the following command:
```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

Set the theme, background etc as you like them and close the window.
You'll also get two accessibility icons in your notification area. One will disappear on its own once you log out and back again, the other one will disappear if you go to System/Preferences/Keyboard and turn off the "Accessibility features can be toggled with keybaord shortcuts"-option.

---

### Post by ArpitRaj on 2010-12-27
Thanx 4 d info

I have 1 more question.....
I applied the updates using update manager and now I get following options on dual boot screen :
1. 2 options for ubuntu boot(prev + latest) 
2. 2 options for recovery mode (prev + latest)
3. 2 other options (memtest something)
4. 1 Windows boot option (no problem with this)

Can I remove the previous settings' option for ubuntu(as the menu is crowded with total of 7 options)and how?

Arpit

---

### Post by mcduck on 2010-12-27
Yes. Just uninstall the old kernel versions, and the menu entries will be automatically removed as well.

The simple way to do this is to use the Computer Janitor (in System/Administration). Although you should check the list of things it wants to uninstall before proceeding, some people have claimed that it might remove things you'd actually want to keep (never happened to me, so I can't really say much about that).

And the other way is to just do it manually, using Synaptic Package Manager. Search for old versions of *linux-headers* and *linux-image* packages and uninstall them. (Make sure you don't remove the latest version you are actually using at the moment...)

---

### Post by Frogs Hair on 2010-12-27
If you have Ubuntu Tweak it is easy to change the login background from login settings . You will not be able to change the greeter.

---

### Post by ArpitRaj on 2010-12-27
How can I access data and files from NTFS drives using shell prompt?

Also how can I undo the changes made by the previous command from a shell prompt? And how can I delete history of commands written in the prompt?

---

### Post by Casper35th on 2010-12-27
If you want to install new themes for....say your desktop you can go here: 

[http://www.bisigi-project.org/?page_id=6&lang=en](http://www.bisigi-project.org/?page_id=6&lang=en)

Follow the instructions its very easy. Or like Frogs Hair said install Ubuntu Tweak and you can change the login screen wallpaper.

---

### Post by fjzahin on 2011-01-13
use Ubuntu tweak to change ur login screen! :D 

1. This is the most simple method. First you should install Ubuntu Tweak. Open the terminal and type:

sudo add-apt-repository ppa:ubuntu-tweak-testing/ppa && sudo apt-get update
sudo apt-get install ubuntu-tweak

2. Then access it through Applications &#8594; System Tools &#8594; Ubuntu Tweak

[http://www.multimediaboom.com/wp-content/uploads/2010/10/ubuntu-login-1.jpg](http://www.multimediaboom.com/wp-content/uploads/2010/10/ubuntu-login-1.jpg)

---

