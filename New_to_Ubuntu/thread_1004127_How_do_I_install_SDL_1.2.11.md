---
title: "How do I install SDL 1.2.11?"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by masterofthemelee on 2008-12-06
Ubuntu says it has SDL 1.2, but I want to play Homeworld natively under linux and the install file say I need SDL 1.2.11.

I tried typing in "sudo apt-get install libsdl-sound1.2.11" but it gave me this error:

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

I have no idea what this means.  Help?

---

### Post by ugm6hr on 2008-12-06
It means that there is another version of apt running at the same time.

Make sure Update Manager, Synaptic and all other Terminals are closed, then try again.

---

### Post by Patrick793 on 2008-12-06
Do you have Synaptic open? Because if it is open you will not be able to use apt from the command line.

Usually a reboot fixes the problem.

---

### Post by masterofthemelee on 2008-12-06
Thanks guys, Synaptic only has SDL 1.2 and I left it open to check my spelling of the lib.

Now I have a new problem:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libsdl-sound1.2.11
```

---

### Post by Patrick793 on 2008-12-06
Why not do sudo apt-get install libsdl-sound1.2

That will give you the latest version in the repositories.

---

### Post by masterofthemelee on 2008-12-06
I'm not sure if it is or isn't.

The "installed version" field says "1.0.1-12build2" which as far as I can tell isn't what I'm supposed to have.

I do have the latest version that Synaptic offers, though.  I just don't know if its the version I need or not.

---

