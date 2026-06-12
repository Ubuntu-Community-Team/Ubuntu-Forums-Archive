---
title: "Adding launchpad https: to software sources"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by baguahsing on 2010-07-08
How can you add launchpad to your software sources.  The reason I asked is that I found updated software for the indicator applet on launchpad but it was at a https: url.  I'm having problems using terminal to build or load software / packages.  Being a noob, I want to use synaptic until I master the terminal.  Hey I've only been at this for a week, a brand new linux / Ubuntu user.

---

### Post by philinux on 2010-07-08
> **baguahsing said:**
> How can you add launchpad to your software sources.  The reason I asked is that I found updated software for the indicator applet on launchpad but it was at a https: url.  I'm having problems using terminal to build or load software / packages.  Being a noob, I want to use synaptic until I master the terminal.  Hey I've only been at this for a week, a brand new linux / Ubuntu user.

If it ain't broke dont look for trouble.

Current version works fine. The 0.4 version as it says on launchpad is under development and is likely buggy. Stick with the stable version Ubuntu is using.

---

### Post by baguahsing on 2010-07-08
The reason I looked into upgrading was because I installed a new battery and now the indicator tells me I am at critcal level and I still have a solid green light on my laptop for the battery.  At full charge it reports 1 hour 40 minutes just it did with the old battery.  I thought updating the indicator applet might fix this issue.

---

### Post by Arand on 2010-07-08
I am assuming you are talking about a PPA (personal package archive) somewhere on launchpad, the instructions on how to add it as a repository should be available from there: (take the ppa:something/something line and add it as an entry in the "other software" section in the "software sources" manager, which is on the system -> administration menu).

Otherwise, simple terminal instructions are available here:
[https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)

I assume when adding it, you know how to downgrade/uninstall it if the PPA version is not for you.

PPAs are normally intended for testing material that are not released, for a reason, however if that is what you want to do, I don't see any reason in not answering..

- arand

---

### Post by philinux on 2010-07-08
Is it this bug.

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/579069](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/579069)

---

### Post by Arand on 2010-07-08
> **baguahsing said:**
> The reason I looked into upgrading was because I installed a new battery and now the indicator tells me I am at critcal level and I still have a solid green light on my laptop for the battery.  At full charge it reports 1 hour 40 minutes just it did with the old battery.  I thought updating the indicator applet might fix this issue.

It will likely not, since detection of charge levels are done by other modules (kernel, acpi...?)

EDIT: Or in this case upower/DeviceKit-power (as per bug report)

- arand

---

### Post by baguahsing on 2010-07-08
Initially after the first charge on the new battery the applet reported the 1hr 40min left and the time quickly fell off just as it did with the old battery.  Now, it keeps reporting the battery is critically low even though I have a full green led on the laptop.  I'm new to linux and Ubuntu, just 1 week old.  Please bear with me.

---

### Post by philinux on 2010-07-08
I found this.

[http://helpforlinux.blogspot.com/2010/05/battery-applet-for-gnome.html](http://helpforlinux.blogspot.com/2010/05/battery-applet-for-gnome.html)

Has anyone any experience of it?

---

### Post by baguahsing on 2010-07-08
Thanks all, I give it a try when I go home.

---

