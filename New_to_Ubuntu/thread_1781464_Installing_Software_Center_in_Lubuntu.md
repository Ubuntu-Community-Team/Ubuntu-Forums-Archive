---
title: "Installing Software Center in Lubuntu"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by philipscott on 2011-06-13
Hi there,
Just a quick question:
how do i install the software center in Lubuntu? i tried installing via the LXterminal and via Synaptic, but it still won't install.
any help would be appreciated!

---

### Post by kerry_s on 2011-06-13
whats the error?

---

### Post by TeoBigusGeekus on 2011-06-13
What did you try and what error message did you get?

---

### Post by philipscott on 2011-06-13
Here is the error from the LXTerminal.


philip@philip-desktop:~$ sudo apt-get install software-center
[sudo] password for philip: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package software-center is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'software-center' has no installation candidate
philip@philip-desktop:~$

---

### Post by VOT Productions on 2011-06-13
Are you sure the 4 sources in Software Sources are ticked?

---

### Post by kerry_s on 2011-06-13
run "sudo apt-get update" or click "reload" in synaptic.

---

### Post by philipscott on 2011-06-13
ok i'll try that!

---

