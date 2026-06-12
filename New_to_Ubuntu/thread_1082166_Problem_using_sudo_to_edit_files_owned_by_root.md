---
title: "Problem using sudo to edit files owned by root"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by woody1 on 2009-02-27
How do I use sudo to enable me to edit a file, i.e hpmud.rules in etc udev rules.d.
I supposedly have administer privileges, but when I try to save the file I get a message saying that I don't. The file is owned by root.

Another possibility, how do i change the read write privileges of the file

---

### Post by taurus on 2009-02-27
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/udev/rules.d/hpmud.rules
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by redseventyseven on 2009-02-27
Usually it's:
```
gksudo gedit {path}/{filename}
```
and then you type in your password (which doesn't display in the terminal - not even as *'s - but it does register your keystrokes)

in your case it should be

```
gksudo gedit /etc/udev/rules.d/hpmud.rules
```

Does that help, or is it something more complicated that that?

---

### Post by wolfen69 on 2009-02-27
or you can do 
```
gksudo nautilus
``` and navigate by gui and edit/save.

---

### Post by thtrgremlin on 2009-02-27
> how do i change the read write privileges of the file? i.e hpmud.rules in etc udev rules.d (paraphrased)

While the above replies are going to be able to do what you want, I would highly recommend against changing file permissions on system / config files unless you really know what kind of impact of file permissions in the system. For the most part it is a security thing, but it is not only an important security thing that can have unintended and unexpected consequences. Just had to throw that warning out there.

---

### Post by Hospadar on 2009-02-27
Just for your information, because its good to know, and different from windows:

In linux/unix/osx "administrator" doesn't mean "root" it just means you have the ability to use sudo to behave as root.  This is a security precaution so that if something bad were to be run as you (or you accidentally double clicked something) it wouldn't be able to eat your system files.

As such, it's a very poor idea to change permissions of system files to you so that you can edit them without having to type sudo, it kind of negates the whole point of having an OS with permissions.

---

### Post by woody1 on 2009-02-27
Thanks to redseventyseven and everybody else who took the time to respond, the gksudo worked. Also I was going to change the permissions back to root after making the changes if I had needed to do it that way.

Thanks all,
           Woody1

---

### Post by oldos2er on 2009-02-27
"Also I was going to change the permissions back to root after making the changes if I had needed to do it that way."

 Just as long as you know that's a dangerous thing to do. It's much safer to use 'sudo' or 'gksu' to give yourself temporary admin privileges.

---

