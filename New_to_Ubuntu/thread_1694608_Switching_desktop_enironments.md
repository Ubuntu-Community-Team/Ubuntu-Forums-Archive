---
title: "Switching desktop enironments"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by Awesome96 on 2011-02-24
After installing dual-booting Xubuntu with Wubi I decided I'd rather use the gnome desktop environment, so I installed it like this:
sudo apt-get install ubuntu-desktop
and everything worked out fine, then I restarted my computer. In the dual boot menu it still said xubuntu, however when I got to choose kernel it was listed as ubuntu-generic instead of xubuntu-generic or something. At the login screen I chose ubuntu session from the drop-down menu and logged in. Everything was fine until I realised that I had two terminals, one from the default packages from ubuntu and one from xubuntu. The problem is that the terminal from the xubuntu install isn't listed as installed software in the software center, and I don't know what the package name is so I can't uninstall it through the terminal. Anyhow I decided to remove the old xfce DE like so:
sudo apt-get remove xubuntu-desktop
But of course the old packages are still there, even after autoremove.
How do I remove the terminal when it's not listed?

---

### Post by thefasterblueone on 2011-02-24
you could try purging the configuration files like this:

```
sudo apt-get remove --purge xubuntu-desktop
```

---

### Post by Smart Viking on 2011-02-24
*xubuntu-desktop* and *ubuntu-desktop* are metapackages, that contains a list of lots of other packages. To find out what the name of the program is, is easy when you have it in the menu. You find out what command is used to execute it in the "edit menus" thing.

---

### Post by ajgreeny on 2011-02-24
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) gives you a command to rid your machine of xubuntu and all the packages it has installed.  It should allow you to get a pure gnome system.

---

### Post by Awesome96 on 2011-02-25
> **ajgreeny said:**
> [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) gives you a command to rid your machine of xubuntu and all the packages it has installed.  It should allow you to get a pure gnome system.

Thank you, that worked like a charm. However I still have one question: Before I was trying to remove the additional terminal, so I started up Synaptic Package Manager and found the package name, which was xterm. I tried to remove it but it said that it would also mess up ubuntu-desktop, disabling the updates or something, I'm not entirely sure. How come? Why is the removal of one package which isn't even part of the current DE so important to the current DE?

---

### Post by ankspo71 on 2011-02-25
Hi,
Is it possible that the terminal you didn't want was called xfce4-terminal or lxterminal?

If you want(ed) to remove xterm because it keeps automatically popping up as the default terminal, you can configure your default terminal like this in terminal:
```
sudo update-alternatives --config x-terminal-emulator
```
I'm not sure if Ubuntu's desktop has a GUI utility to configure the default terminal. I know Kubuntu does though.

Xterm is required by ubuntu-desktop because alot of applications in Ubuntu need xterm in order for them to work. This is where dependencies and dependents all come into play.

You can see this when you search Synaptic Package Manager for 'xterm'. Right click on xterm, select properties, then click on the dependencies tab. 

Choose 'dependencies' from the dropdown menu to see a list of applications needed for xterm to work. Xterm depends on those packages.
Command equivalent:
```
apt-cache depends xterm
```

Now choose 'dependents' from the dropdown menu to see a list of applications that need xterm for them to be able to work. Those packages depend on xterm.
Command equivalent:
```
apt-cache rdepends xterm
```

When APT removes those packages it is because it follows the list of dependents in the deb package (they won't be removed if they are depended on by another package on the system). 

Hope this helps explain it a little.

---

