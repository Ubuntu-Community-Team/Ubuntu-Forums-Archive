---
title: "apt-get error could not open lock file"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by olddavd on 2009-06-01
Help. I was trying to use apt-get update and got the following error:

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

I'm using Hardy Heron 8.04.1 64 bit version.

---

### Post by albinootje on 2009-06-01
> **olddavd said:**
> Help. I was trying to use apt-get update and got the following error:

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Do you have Add/Remove or Synaptic package manager open ?
It's also possible that the update manager was just doing an apt-get update in the background.

---

### Post by Hospadar on 2009-06-01
You need to add "sudo" to the beginning of the command
i.e. ```
sudo apt-get update
```apt-get needs root (administrator) privilege, and when you prepend a command with sudo it gives the command root privilege.

(it stands for "Super-User DO")

---

### Post by olddavd on 2009-06-01
Many thanks for the help. I feel a bit foolish not using "sudo". 

sudo apt-get update

Works okay. How do I list this issue solved?

---

