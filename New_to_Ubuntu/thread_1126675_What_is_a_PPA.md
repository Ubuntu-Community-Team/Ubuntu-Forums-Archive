---
title: "What is a PPA?"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by cfogelberg on 2009-04-15
Um, this is a dumb question, but what is a PPA and how do I use it/get access to it?

I ask because I have the synpatics problem on amd64 (syndaemon crashes all the time) and comments on the bug report ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/282735]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/282735")) says that using the -wgrant3 ppa might be a solution.

Hence my question :)
Christo

---

### Post by KhaaL on 2009-04-15
PPA stands for a personal package archieve, you use it by adding its adress to your  /etc/apt/sources.list file, which you need superuser priviligies to modify!

so in your case you need to add these lines to the mentioned file above:

deb [http://ppa.launchpad.net/wgrant/ppa/ubuntu](http://ppa.launchpad.net/wgrant/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/wgrant/ppa/ubuntu](http://ppa.launchpad.net/wgrant/ppa/ubuntu) jaunty main


just type the command:
gksudo gedit /etc/apt/sources.list

Make sure to do a backup first!

---

### Post by cfogelberg on 2009-04-16
Great, thanks! :) xto

---

### Post by nandemonai on 2009-04-16
As a side note I find it cleaner to add additional repositories to the /etc/apt/sources.list.d/ directory. Simply make a new file in there, name it repo-name.list, insert the repo line(s) and you're good to go.

---

### Post by fballem on 2009-04-16
A third option for adding a repository is to use the Software Sources tool (System > Administration > Software Sources). The PPA will normally include the address of the Archive and a Key file.

When you select Software Sources from the menu, you will be asked for your password. If this is correct, then the Software Sources panel will be displayed.

On the panel, select the Third Party tab (see screenshot - Sofware Sources).

To add a PPA:

1. Select the Add button on the Software Sources screen.
2. You will then get a panel that will allow you to type in the PPA (or paste it in if you have done a copy of the source). (See Add Source screenshot)
3. Select the Add button and the PPA will be added to your source.

When you are returned to the Software Source screen, you will then add the Key. In the PPA, select the link to the key. This will open up a browser window that contains a lot of gibberish. In your browser, select File > Save Page As and save the page to your desktop. This is the key file.

On Software Sources:

1) Select the Authentication tab (see Authentication screenshot).
2) Select the Import Key button.
3) You will then be able to browse to the key file that you saved and select import.

You will get a notification that your packages are out of date. This is fine and when you select OK, the system will update the package list.

Select the close button on the Software Sources screen, and you can then add the application using Synaptic.

The instructions sound worse than they actually are, but for those of us who are used to GUI as opposed to command line, this is how it's done.

Hope this helps,

---

