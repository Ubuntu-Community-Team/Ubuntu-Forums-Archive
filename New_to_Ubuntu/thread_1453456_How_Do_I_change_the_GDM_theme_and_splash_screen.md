---
title: "How Do I change the GDM theme and splash screen"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by jaco223 on 2010-04-13
How can I go about setting GDM to allow root logins? I've tried setting root passwd from
a terminal which seems the same as sudo passwd. 

Any help is greatly appreciated.

Jaco

P.S. I want to login as root to find a way to change the GDM theme and splash screen.

---

### Post by J V on 2010-04-13
You can't do that on karmic... but I'm sure you can do it with gk/sudo if you find a workaround.

Please try using sudo to make a workaround, gksudo nautilus and sudo bash will give you basicly full root control over the file manager, the terminal, and any programs started from either. (Dangerous! Make sure you shut them down when you're done!)

---

### Post by nerdy_kid on 2010-04-13
i think it is against forum policy to unlock the root account....

[edit]
to change the theme and background ive heard that
```

sudo -u gdm gnome-appearance

```
will do it.

if gnome-appearance doesnt work just find the name of the app that switches the theme/wallpapers for your desktop -- i use KDE so i cant get it.

---

### Post by philinux on 2010-04-13
> **nerdy_kid said:**
> i think it is against forum policy to unlock the root account....

It is. I've amended the thread title to reflect the correct support query.

Using sudo or gksudo is the correct method.

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by undecim on 2010-04-13
Logging in as root won't allow you to change the GDM background. Also, setting a root password is a security problem.

If you want to change the background, try pressing ALT+F2 and pasting this command:
```
gksudo -u gdm gnome-appearance-properties
```

Then change the background there. (NOTE: since you are running this as the GDM user, you won't be able to see the contents of your home directory. If you have an image in your home directory you want to use, you will have to put it in /var/gdm and make sure that the owner is gdm. You can do all this from a file manager if you run it by pressing ALT+F2 and type "gksudo nautilus")

---

### Post by jaco223 on 2010-04-13
> **undecim said:**
> Logging in as root won't allow you to change the GDM background. Also, setting a root password is a security problem.

If you want to change the background, try pressing ALT+F2 and pasting this command:
```
gksudo -u gdm gnome-appearance-properties
```Then change the background there. (NOTE: since you are running this as the GDM user, you won't be able to see the contents of your home directory. If you have an image in your home directory you want to use, you will have to put it in /var/gdm and make sure that the owner is gdm. You can do all this from a file manager if you run it by pressing ALT+F2 and type "gksudo nautilus")

Undecim, I don't think it will be so easy to change my gdm theme. I tried to go to /var/gdm, but there is not a directory with that name. I then tried the appear-properties, but it looks like that is just to change the background and theme of my desktop. I also tried gksudo nautilus, but find nothing associated with gdm.

I did whereis gdm and got back /etc/gdm  /usr/lib/gdm and /usr/share/gdm.
I don't see any images or themes in any of those directories.

I don't know where to go from here.

Jaco

P.S. Philinux I apologize for posting to unlock root, I didn't know that was illegal.

---

### Post by mcduck on 2010-04-13
> **jaco223 said:**
> Undecim, I don't think it will be so easy to change my gdm theme. I tried to go to /var/gdm, but there is not a directory with that name. I then tried the appear-properties, but it looks like that is just to change the background and theme of my desktop. I also tried gksudo nautilus, but find nothing associated with gdm.

I did whereis gdm and got back /etc/gdm  /usr/lib/gdm and /usr/share/gdm.
I don't see any images or themes in any of those directories.

I don't know where to go from here.

Jaco

P.S. Philinux I apologize for posting to unlock root, I didn't know that was illegal.

Changing the GDM theme in 9.04 and later works exactly as Undecim suggested. Running that command opens the Appearance dialog as user "gdm", and that allows you to set the wallpaper, theme & fonts for the GDM login screen.

That's as much theming as you'll get, the GDM version used in 9.04 and later doesn't support the old style themes any longer.

---

### Post by jaco223 on 2010-04-13
> **mcduck said:**
> Changing the GDM theme in 9.04 and later works exactly as Undecim suggested. Running that command opens the Appearance dialog as user "gdm", and that allows you to set the wallpaper, theme & fonts for the GDM login screen.

That's as much theming as you'll get, the GDM version used in 9.04 and later doesn't support the old style themes any longer.

Mcduck, I'm a little confused here. I ran the command Undecim provided, and it opens the appearance  settings window, but I don't see a way to get the theme I want to use in there. I apologize for my lack of knowledge. I downloaded a theme from gnome look and want to use it, are you saying I can't install a theme for gdm?

Jaco

---

### Post by mcduck on 2010-04-13
> **jaco223 said:**
> Mcduck, I'm a little confused here. I ran the command Undecim provided, and it opens the appearance  settings window, but I don't see a way to get the theme I want to use in there. I apologize for my lack of knowledge. I downloaded a theme from gnome look and want to use it, are you saying I can't install a theme for gdm?

Jaco

Like I said, the GDM used in 9.04 and later doesn't support that kind of themes any more.

The Appearance dialog, when opened as user "gdm", allows you to change the GTK and icon theme, fonts and background image for the login screen.

---

### Post by undecim on 2010-04-14
> **jaco223 said:**
> Undecim, I don't think it will be so easy to change my gdm theme. I tried to go to /var/gdm, but there is not a directory with that name. I then tried the appear-properties, but it looks like that is just to change the background and theme of my desktop. I also tried gksudo nautilus, but find nothing associated with gdm.

I did whereis gdm and got back /etc/gdm  /usr/lib/gdm and /usr/share/gdm.
I don't see any images or themes in any of those directories.

I don't know where to go from here.

Jaco

P.S. Philinux I apologize for posting to unlock root, I didn't know that was illegal.

Like mcduck explained, GDM doesn't support the old themes anymore. Changing settings from the command I provided should change them for the gdm user which handles the login screen.

As for the lack of a /var/gdm directory, I could be wrong about that path. I don't have GDM on my computer anymore, so I don't have a reference for myself, but the gdm user has a home directory somewhere on the system. If you run "grep gdm /etc/passwd" in a terminal, you will see gdm's passwd entry, which will include this directory.

---

### Post by Adam's AI on 2010-04-14
I'm pretty new to linux, so I hope I understand your question properly. I've been wondering about this myself and I think as some have pointed out above that it's not about being logged in as root but that gdm was changed with 9.10 and themes don't work anymore.

There are several threads on these forums and elsewhere that detail downgrading gdm from 2.28 to 2.0 (which I am thinking of trying) but are all prefaced with a strongly **'this might break your system!'**. [Here's a link]("http://ubuntuforums.org/showthread.php?p=8350408").

Hope that helps.

---

### Post by Adam's AI on 2010-04-14
Also, being new to this forum and linux I was wondering if someone could explain to me why asking about unlocking root is against forum policy. I wasn't asking about how to unlock it, and I don't intend this as flame-bait, I am genuinely curious.

Thanks

---

### Post by undecim on 2010-04-14
> **Adam's AI said:**
> Also, being new to this forum and linux I was wondering if someone could explain to me why asking about unlocking root is against forum policy. I wasn't asking about how to unlock it, and I don't intend this as flame-bait, I am genuinely curious.

Thanks

I didn't think it was against the rules to ask about it (no one should ever discourage someone from asking a question), but it's against the rules for people offering support to tell someone to log in as root.

The reason for this is that it's VERY easy to break your system as root. Moreover, enabling root on a computer can be a security hole.

Ubuntu's (and a lot of Linux distros) security model involves the fact that the user only account only has limited control over the system. A user can still perform any administrative task with "sudo" or "gksu", which will run a single command as the root user, but require your password. This way, if an attacker uses (for example) a firefox flaw to gain access to your computer, they have only limited access. They cannot install rootkits, keyloggers, or other malware without gaining root access. If you are logged in as root however, an attacker will already have root access, and has free reign over your computer.

In short, logging in as root is dangerous, and anything you can do as root, you can do with the "sudo" or "gksu" commands.

---

### Post by wojox on 2010-04-14
Confucius say he who play in root eventually kill tree. :P

---

### Post by Adam's AI on 2010-04-14
> **undecim said:**
> I didn't think it was against the rules to ask about it (no one should ever discourage someone from asking a question), but it's against the rules for people offering support to tell someone to log in as root.

Ahhh, that makes mores sense to me. Thanks!

---

### Post by jaco223 on 2010-04-15
Mcduck, , when I run the command you gave me, I get this.
Is that what I should get before accessing GDM as user?

Thanks,

Jaco

---

### Post by undecim on 2010-04-15
> **jaco223 said:**
> Mcduck, , when I run the command you gave me, I get this.
Is that what I should get before accessing GDM as user?

Thanks,

Jaco

You can safely ignore that warning.

---

### Post by jaco223 on 2010-04-15
I ran the command 

```
gksudo -u gdm gnome-appearance-properties
```
But after selecting a new background and logging out, My change did not take effect.

---

### Post by wojox on 2010-04-15
Try [GDM2]("http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html")

---

### Post by jaco223 on 2010-04-16
> **wojox said:**
> Try [GDM2]("http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html")

I just tried GDM2 with no luck. I guess it just can't be changed. Why did they(Gnome Devs)
lockdown GDM like that? I remember years ago with Debian/Woody, changing the GDM
appearance was a piece of cake.

Jaco

---

### Post by mcduck on 2010-04-17
> **jaco223 said:**
> I ran the command 

```
gksudo -u gdm gnome-appearance-properties
```
But after selecting a new background and logging out, My change did not take effect.
Then try this one (actually this is what I've been using all the time):
```
gksudo -u gdm dbus-launch gnome-appearance-properties
```
The downside to this is that you'll get two accessibility icons in the notification area, one will disappear on it's own when you log out and back again, and the other one goes away when you go to System/Preferences/Keyboard, and turn off "Accessibility features can be toggled with keyboard shortcut"-option on the Accessibility-tab

> **jaco223 said:**
> I just tried GDM2 with no luck. I guess it just can't be changed. Why did they(Gnome Devs)
lockdown GDM like that? I remember years ago with Debian/Woody, changing the GDM
appearance was a piece of cake.

Jaco
They didn't "lock down" anything, GDM was rewritten to get it to handle many new features, and keeping support for the old themes simply wasn't possible. In other words the support for the old themes isn't locked down, it simply doesn't exist any more.

On the other hand changing the things that you *can* change in GDM is now a lot easier than it was before, you don't need to edit text files to change the icons or wallpaper of the login screen. ;) So the new GDM took away some theming possibilities, and at the same time gave us some new theming possibilities plus some much needed new features to the GDM itself. Sometimes you just have to give up some old stuff to be able to move forwards...

---

### Post by towheedm on 2010-05-07
You cannot theme GDM from 9.10 and above.  It is highly customizable though.  Check out the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

---

### Post by Belfry on 2010-05-10
The Xubuntu 10.04 gdm doesn't link up to gnome in quite the same way, so this method doesn't work:

```

*after logging into ctrl+alt+f1*
sudo -u gdm xfce4-appearance-settings

```

The interface comes up alright, but no change is affected.

I did stumble onto this to change my gdm wallpaper and theme:

```

sudo -u gdm gconftool-2 /desktop/gnome/interface/gtk_theme -s --type=str Mist
sudo -u gdm gconftool-2 /desktop/gnome/background/picture_filename -s  --type=str /home/user/bg1.jpg

```

These commands list other things you can fiddle with:
```

sudo -u gdm gconftool-2 /desktop/gnome --all-dirs
sudo -u gdm gconftool-2 /desktop/gnome/background -R
sudo -u gdm gconftool-2 /desktop/gnome/interface -R

```

And this will give a solid dark-blue background:
```

sudo -u gdm gconftool-2 /desktop/gnome/background/picture_filename -u
sudo -u gdm gconftool-2 /desktop/gnome/background/primary_color -s --type=str "#163253"

```

---

