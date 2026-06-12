---
title: "Many problems after upgrading from 8.10 to 9.04, need some help"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by legolas_w on 2009-05-10
Hi
Thank you for reading my post. I upgraded ubuntu 8.10 to ubuntu 9.04 and now I have the following problems:

- I can not open gnome-terminal, it returns an error like: 

```

There was an error creating the child process for this terminal

```

- I can not install the restricted driver, When I open the System> Administration> Hardware Driver it shows that I can install the NVidia driver, when I press the activate button and then I enter the password it shows a window indicating that a download process wants to start, but close right after openning without downloading and installing anything or without showing any error message.

- I want to have 9.04 GDM (Login Window) So I select System> Administration > Loging window and then I selected the theme. After I restart the theme was showing in an incorrect resolution like for example the resolution was 800*600 or something like that therefore the theme can not be seen correctly and only the username/password box is shown.

- When I had 8.10 I installed startup manager and tried to use some other bootup screen and theme. now I want to use native Ubuntu bootup screen and theme, what should I do?

Thank you very much.

---

### Post by legolas_w on 2009-05-10
Another problem:

When I right click on the top panel to add something to the panel, it just shows two menu entries:
```

Help
About Panel

```

While it must show more items like "add to panel". If you know a solution for this problem, let me know please.

---

### Post by Ms_Angel_D on 2009-05-10
Doesn't sound like the upgrade went well, I'm not sure how to fix the issues you mentioned, but to be honest I suggest backing up your stuff and doing a fresh install.

---

### Post by kansasnoob on 2009-05-10
Try running the command:

```
sudo apt-get install --reinstall ubuntu-desktop && sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by Didius Falco on 2009-05-10
I did a quick search and found a couple of Bugtracker reports on LaunchPad.

The first one I skimmed through is here:

[https://bugs.launchpad.net/ubuntu/+bug/245956](https://bugs.launchpad.net/ubuntu/+bug/245956)

While it offers a user kludge, it was ultimately decided that this bug was a duplicate of [https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927](https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927)

I'm still reading through that one...

Regards,

Didius

---

### Post by kansasnoob on 2009-05-10
Try what I posted! If at some point you removed the desktop meta-package through the time you used Intrepid it would break the upgrade procedure.

---

### Post by louieb on 2009-05-10
:confused: Had multiple problems with the 8.10 to 9.04 upgrade too. 
[http://ubuntuforums.org/showpost.php?p=7146572&postcount=328](http://ubuntuforums.org/showpost.php?p=7146572&postcount=328)

Restored my laptop back to 8.10. But saw enough of 9.04 I liked, so I did a fresh install. Fresh install solved most of my problems. 

I did try the apt-get install ubuntu-desktop but it just said it was already installed. Next time an upgrade goes this bad I'll try the --reinstall option.

---

