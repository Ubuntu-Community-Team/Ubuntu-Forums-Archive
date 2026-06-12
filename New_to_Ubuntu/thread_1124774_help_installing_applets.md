---
title: "help installing applets?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by iam_newhere on 2009-04-13
how do i install applets such as stacks, show desktop, workspaces?
i recently installed avant window navigator.

thanks!

---

### Post by Paqman on 2009-04-13
System > Admin > AWN Manager > Applets

Or right click on the AWN bar and choose "dock preferences".

---

### Post by iam_newhere on 2009-04-13
> **Paqman said:**
> System > Admin > AWN Manager > Applets

Or right click on the AWN bar and choose "dock preferences".

i did that but when i browse to select an applet.
i dont see an awn applet package.

im running xubuntu btw. with compositor enabled

---

### Post by iam_newhere on 2009-04-13
bump?

---

### Post by Paqman on 2009-04-13
So you've got AWN Manager open? Are you saying you don't have any applets available in the applet section? Have you installed all the applet packages in Synaptic?

---

### Post by iam_newhere on 2009-04-13
yeah i hav the task list.
i think i hav.

i went to synaptic and installed awn-manager and it came with many others to be installed.

any suggestion?

---

### Post by Paqman on 2009-04-13
Ok, let's make sure you've got all the applet packages installed. Click on all these links please:

[awn-applets-c-core]("apt:awn-applets-c-core")
[awn-applets-c-extras]("apt:awn-applets-c-extras")
[awn-applets-python-core]("apt:awn-applets-python-core")
[awn-applets-python-extras]("apt:awn-applets-python-extras")

If that doesn't work then go Applications > System > Software Sources > Third party and add this line:
```

deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu hardy main

```

Then open a terminal and paste in these lines one after the other:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 1024R/BF810CD5
sudo apt-get update

```

Then try clicking on those links again.

---

### Post by iam_newhere on 2009-04-13
> **Paqman said:**
> Ok, let's make sure you've got all the applet packages installed. Click on all these links please:

[awn-applets-c-core]("apt:awn-applets-c-core")
[awn-applets-c-extras]("apt:awn-applets-c-extras")
[awn-applets-python-core]("apt:awn-applets-python-core")
[awn-applets-python-extras]("apt:awn-applets-python-extras")

If that doesn't work then go Applications > System > Software Sources > Third party and add this line:
```

deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu hardy main

```

Then open a terminal and paste in these lines one after the other:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 1024R/BF810CD5
sudo apt-get update

```

Then try clicking on those links again.

ok. i will try that later. cuz this is a shared pc.
i will reply if it would work. thanks

---

