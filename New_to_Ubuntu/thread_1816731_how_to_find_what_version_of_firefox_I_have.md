---
title: "how to find what version of firefox I have"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by primal woman on 2011-08-02
Could not find this already posted, so thought I'd ask. 

I have seen firefox in 11.04 and have firefox in 10.04. I like the latter much better. Tried to find which firefox I have and could not find it. Thought it would be inUbuntu Software Center under 'installed software', but there is no mozilla or firefox in that list of all installed software. Skype is in there as well as evolution and office etc, etc. Really thought that this is where I would find firefox as well. Does it go by another name?

Where can I go to find what version of firefox I have?

---

### Post by skatinjj on 2011-08-02
You should be able to open firefox, click the Help menu and than About.

---

### Post by skatinjj on 2011-08-02
or you can search synaptic and see what is installed.

or you could run this:

```
dpkg --get-selections > programs.txt
```

to create a text file with everything installed.

---

### Post by primal woman on 2011-08-02
> **skatinjj said:**
> You should be able to open firefox, click the Help menu and than About.

That was easy enough. Found it. Weird it would not be in 'installed software' like windows does. Thanks.

---

### Post by lovinglinux on 2011-08-03
Also, if you type **about:support** in the address bar, it gives you the version among other information.

I would recommend getting Firefox 5 or Firefox 6 beta. See [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")

---

### Post by Guruprasad on 2011-08-03
> **primal woman said:**
> That was easy enough. Found it. Weird it would not be in 'installed software' like windows does. Thanks.

Synaptic Package Manager shows the list of softwares that are installed as well as softwares that are not installed, similar to the Windows Installed Software. In Synaptic you can sort by status i.e. the first column. You will get the list of installed softwares. In that you find firefox or any other software and its version.

Linux can do much more than Windows does. Just we need to understand the difference.

---

