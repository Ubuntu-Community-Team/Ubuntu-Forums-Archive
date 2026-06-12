---
title: "Need to add &quot;pool&quot; repository to install bcmwl-kernel-source"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by sbryant31 on 2010-11-26
Im trying to install the bcmwl driver on ubuntu netbook remix. I installed it but the driver doesnt appear to be installed. So I obviously need to install it, but last time I tried to install it I got a lot of errors, thus causing me to re-install the whole OS

So, in my flash drive there is a folder called "pool" which I assume contains the packages I need. I am trying to add this as a repository to my "Ubuntu Software Center."

So I add the repository in this way:
Software Sources -> Other software -> Add
Type: Binary
URL: file:///media/PENDRIVE/pool
Distribution: maverick
Components: restricted main

So I tried to add this repository, but when I search for "bcmwl" (which I need to install , specifically bcmwl-kernel-source) I get nothing.

Should I not be able to add the pool directory as a repository?

---

### Post by kerry_s on 2010-11-27
have you tried just going there in the file manager & double clicking the deb ?

pool-> restricted-> b-> bcmwl

---

### Post by sbryant31 on 2010-11-27
Yes, when I try to install the deb, I first get dependency errors for Dkms. Why wasnt DKMS installed with the distro though? So I need to install dkms. But in order to install that i need GCC installed. Why isnt GCC installed?

So I went down that route last time and I installed every dependency, but I ended up getting errors when I finally went to install bcmwl. And it just doesn't make sense.

What am I supposed to do here!? Do I just download every possible maverick repository so I can install all of the packages in the "pool" folder correctly? Is there no automatic way to do this?

---

