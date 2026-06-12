---
title: "problem with Software Center"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by djmd on 2010-02-13
Just installed Ubuntu today for the first time... so far so good, except I cannot install anything with the Software Center. There is no "install" button when I look at available software, and 'install' on the drop-down is grayed out.

I'm logged in with the ID I created when I installed. Also, I seem to be able to install packages with Synaptic, so I don't think it's a permissions issue. I'm sure it's somethint dumb though...

appreciate the help!

---

### Post by nhasian on 2010-02-13
on fresh installs, sometimes people forget to do system updates.  open up a terminal and type:

```
sudo apt-get update && sudo apt-get upgrade
```

You will have a lot of updates including updates to the kernel and software-center.  most likely you will need to reboot as well.  then the software center will operate properly.

---

### Post by sisco311 on 2010-02-13
> **djmd said:**
> Just installed Ubuntu today for the first time... so far so good, except I cannot install anything with the Software Center. There is no "install" button when I look at available software, and 'install' on the drop-down is grayed out.

I'm logged in with the ID I created when I installed. Also, I seem to be able to install packages with Synaptic, so I don't think it's a permissions issue. I'm sure it's somethint dumb though...

appreciate the help!

Hi and welcome to the forums!

Press Alt+F2 & run:
```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```
then try to run software-center again. If the install button works, then go to *System -> Preferences -> Startup Application* and enable *PolicyKit Authentication Agent* or add /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 to the startup applications.

---

### Post by djmd on 2010-02-13
Thanks for the quick replies! Strangely enough, the install button started appearing after I posted that question... but also, the update manager popped up, so I just finished all the system updates... anyway, seems to be working fine now.

I'm pretty excited about this- literally haven't installed Linux since my last 486. Boy have times changed... haha. Inherited a Dell Dimension 2400 and thought it would be a perfect machine to experiment with :)

---

