---
title: "Ubuntu and other operating systems."
date: 2009-05-22
forum: New to Ubuntu
---

### Post by yangt299 on 2009-05-22
Hi guys.

Just a quick question. If you are running Ubuntu as your main operating system, it is possible to install other operating systems and switch sessions from the login menu (Kubuntu, Xubuntu, etc.). However, it is also possible to install other linux operating systems such as Fedora Core in addition to Ubuntu on the same computer?

Thanks!

---

### Post by jakupl on 2009-05-22
> **yangt299 said:**
> Hi guys.

Just a quick question. If you are running Ubuntu as your main operating system, it is possible to install other operating systems and switch sessions from the login menu (Kubuntu, Xubuntu, etc.). However, it is also possible to install other linux operating systems such as Fedora Core in addition to Ubuntu on the same computer?

Thanks!

Yes, but you will have to reboot the computer in order to change operating system.
When you switch between eg. Kubuntu and Ubuntu only by logging out and in, you are actually not changing operating systems, you are just changing desktop managers

---

### Post by reg4c on 2009-05-22
Since you said that you wanted to install Kubuntu and Xubuntu, it is possible to do that just by installing those desktop environments. Then you can use any of the three. On the other hand, installing the desktop environment is not the same like installing the whole OS so your milage may vary.

Seach for installing XFCE and KDE in Ubuntu to get to play around...

---

### Post by yangt299 on 2009-05-22
So how is it done? Also, will the hard drive information be saved on the other operating system? eg. you have a file called test.html on your desktop on Ubuntu, will you also automatically have a file called test.html when you switch to your other operating system?

thanks again!

---

### Post by reg4c on 2009-05-22
If you are asking about what I suggested:

The operating system itself will stay the same, you will just install the "desktop environment" that is basically the difference between Kubuntu and Ubuntu. Kubuntu uses KDE while Ubuntu uses Gnome.

To install KDE in Ubuntu do:
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

To install XFCE in Ubuntu do:
```
sudo apt-get update
sudo apt-get install xubuntu-desktop
``` 

Cheers

---

### Post by Zzl1xndd on 2009-05-22
On a side note, if you did wanna play with other Distro's I would recommend using virtual machines.

---

### Post by reg4c on 2009-05-22
Ow, yeah, I forgot about that...

Although you do need 2GB RAM minimum, an excellent idea...

I suggest Virtual Box OSE from the "Add/Remove"

---

### Post by Zzl1xndd on 2009-05-22
> **reg4c said:**
> Ow, yeah, I forgot about that...

Although you do need 2GB RAM minimum, an excellent idea...

I suggest Virtual Box OSE from the "Add/Remove"

I second VirtualBox Great program.

---

### Post by yangt299 on 2009-05-22
Thanks guys. Could anyone explain what a virtual machine is? Sorry I'm a Ubuntu noob.

---

### Post by Zzl1xndd on 2009-05-22
Basically its running an OS on Virtualized hardware in the host Operating system. It will allow you to run a second OS in the one you are running now.

---

### Post by albinootje on 2009-05-22
> **yangt299 said:**
> Thanks guys. Could anyone explain what a virtual machine is? Sorry I'm a Ubuntu noob.

A Virtual Machine more or less imitates a real PC, which means that you can run other Operating Systems (as guest) inside (in your case) Ubuntu.

You can install VirtualBox, and it will provide you with an emulated videocard, emulated NIC, emulated (or real) cdrom drive.
Try it :
```

sudo apt-get update
sudo apt-get install virtualbox

```

See also : [http://en.wikipedia.org/wiki/VirtualBox](http://en.wikipedia.org/wiki/VirtualBox)

---

### Post by anystupidname on 2009-05-22
> **yangt299 said:**
> Hi guys.

Just a quick question. If you are running Ubuntu as your main operating system, it is possible to install other operating systems and switch sessions from the login menu (Kubuntu, Xubuntu, etc.). However, it is also possible to install other linux operating systems such as Fedora Core in addition to Ubuntu on the same computer?

Thanks!

If you decide to try other distros (fedora, gentoo, ...), as opposed to different window managers, (KDE, Gnome, XFCE,...) you can easily do so with Unetbootin.

```
# aptitude install unetbootin
```

Then run Unetbootin from your "system tools" menu and pick what you'd like to try and and when you reboot, you'll have another OS in your boot menu.

P.S. You CAN share your home folder among different distros although you sometimes run into some permission problems doing that. You'll probably want your home to be on a different partition if you do that too... Have fun ;)

---

### Post by ALIENDUDE5300 on 2009-05-22
If you want to install fedora as well as ubuntu, you'd be better off just compiling and installing RPM support and the additional packages you need. Try this for RPM support:
```
 sudo apt-get install rpm alien yum
```

---

