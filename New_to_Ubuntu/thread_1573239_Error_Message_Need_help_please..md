---
title: "Error Message Need help please."
date: 2010-09-12
forum: New to Ubuntu
---

### Post by Joe_Ib on 2010-09-12
When I try to open up the Synaptic Package manager I keep getting this error message that pops up.

E: Type 'dep' is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Any help please and thank you.

---

### Post by cj13579 on 2010-09-12
Have you recently added a source to your /etc/apt/sources.list?

Check that on line 54. Bring up a text editor using:

```
gksudo gedit /etc/apt/sources.list
```

Check to make sure that you don't have any quotations or anything like that on the line.

---

### Post by Elfy on 2010-09-12
The sources list should nto contain any lines not starting with #, deb or deb-src.

Open the file for editing

```
kdesu kate /etc/ep/sources.list
```

Check and either remove the lines that don't.

If you have tried to add a 3rd party repo then edit the file, save and have another go.

---

### Post by Elfy on 2010-09-12
> **cj13579 said:**
> Have you recently added a source to your /etc/apt/sources.list?

Check that on line 54. Bring up a text editor using:

```
gksudo gedit /etc/apt/sources.list
```

Check to make sure that you don't have any quotations or anything like that on the line.

gksudo is for gnome - thread prefix is kubuntu :)

---

### Post by Joe_Ib on 2010-09-12
There was a line that was started with dep instead of deb that i changed everything seems to work now.  Thanks your for the help.

---

### Post by cj13579 on 2010-09-12
> gksudo is for gnome - thread prefix is kubuntu 

I realised that when I wrote it but felt too lazy to change it - aplogies.

@Joe_Ib Glad it is now all working for you! You should mark the thread as solved.

---

