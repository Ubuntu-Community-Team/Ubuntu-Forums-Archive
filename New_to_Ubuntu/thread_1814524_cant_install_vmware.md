---
title: "cant install vmware"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by cosmoshell on 2011-07-29
~/Downloads$ sudo sh ./VMware-Workstation-Full-7.1.4-385536.x86_64.bundle
bash: syntax error near unexpected token `('

---

### Post by cosmoshell on 2011-07-29
bump

---

### Post by Mark Phelps on 2011-07-30
Most folks around here use Virtualbox -- which is what you should be using, instead of VMWare.

---

### Post by scorchgeek on 2011-07-30
It looks to me like the problem is that you're running a bash script using sh. Why are you running sudo sh? You should just be able to run the file directly:
```
sudo ./VMware-Workstation-Full-7.1.4-385536.x86_64.bundle
``` (Do you even need sudo? I'm not sure.)

If that doesn't work, the file isn't marked as executable; try
```
chmod +x ./VMware-Workstation-Full-7.1.4-385536.x86_64.bundle
```

But ditto on using VirtualBox instead; I just wanted to help you if you're dead set on using VMware.

EDIT: Come to think of it, the error says 'bash', so maybe I'm wrong. But it's probably worth a shot anyway; it won't take you more than a few seconds and can't hurt if it doesn't work.

---

### Post by zero2xiii on 2011-07-31
> **cosmoshell said:**
> ~/Downloads$ sudo sh ./VMware-Workstation-Full-7.1.4-385536.x86_64.bundle
bash: syntax error near unexpected token `('

Seariously?

I think you got lost a looong way down the rabit hole.. Lets recap from the top.

*.bundel is NOT a *.sh file? So WHY are you trying to execute the file with SH?

Just do:

```

chmod +x ./VMware-Workstation-Full-7.1.4-385536.x86_64.bundle
sudo ./VMware-Workstation-Full-7.1.4-385536.x86_64.bundle

```

The sudo on the file shouldn't even be neccesary since the installer asks for the root password if it isn't run with sudo (mine did anyway). But don't just SH run random things, ubuntu does a perfectly good job of determaning what interpreter to use.


All those on virtual box:

Sure, virtual box is good, no doubt, but I have had better experiences on VMware, like emulating a 64bit CPU even though the OS the vmware server is being run on is a 32bit install. And its a little more stable that virtual box, well, atleast in my experience :)

---

### Post by cosmoshell on 2011-08-01
> **zero2xiii said:**
> Seariously?

I think you got lost a looong way down the rabit hole.. Lets recap from the top.

*.bundel is NOT a *.sh file? So WHY are you trying to execute the file with SH?

Just do:

```

chmod +x ./VMware-Workstation-Full-7.1.4-385536.x86_64.bundle
sudo ./VMware-Workstation-Full-7.1.4-385536.x86_64.bundle

```

The sudo on the file shouldn't even be neccesary since the installer asks for the root password if it isn't run with sudo (mine did anyway). But don't just SH run random things, ubuntu does a perfectly good job of determaning what interpreter to use.


All those on virtual box:

Sure, virtual box is good, no doubt, but I have had better experiences on VMware, like emulating a 64bit CPU even though the OS the vmware server is being run on is a 32bit install. And its a little more stable that virtual box, well, atleast in my experience :)

PC:~/Downloads$ chmod +x ./VMware-Workstation-Full-7.1.4-385536.x86_64(1).bundle
bash: syntax error near unexpected token `('

---

### Post by cosmoshell on 2011-08-01
turns out the problem was (1) in filename.

---

