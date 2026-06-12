---
title: "what is this and how can I fix it?"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2011-05-09
Hello,
I was trying to add a couple of indicator icons as specified in OMGUbuntu and something odd happened. Now,everytime I try opening the package manager or update my system I get a dialogue box with this error:

when I try to update:
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/lorenzo-carbonell-atareao-natty.list'


and when I try to open up the package manager:
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/lorenzo-carbonell-atareao-natty.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

how can I fix this?

---

### Post by matt_symes on 2011-05-09
Hi

Open a terminal and copy and paste this into it.

```
cat /etc/apt/sources.list.d/lorenzo-carbonell-atareao-natty.list
```

Post back the results back here using copy and paste into your new post.

Kind regards

---

### Post by satanselbow on 2011-05-09
There is a syntax error in one of the custom repos you have added which is causing the list not to load...

In a terminal:

```
sudo rm /etc/apt/sources.list.d/lorenzo-carbonell-atareao-natty.list
```

This will delete the custom list with the error.

You should be able to the fire up synaptic and reload your sources without error ;)

---

### Post by satanselbow on 2011-05-09
@skyzthelimit230 take which ever route you fancy ;) Mine just cuts to the chase instead of trying to debug the list :D

---

### Post by skyzthelimit230 on 2011-05-09
OK, here are the results

fil@ubuntu:~$ cat /etc/apt/sources.list.d/lorenzo-carbonell-atareao-natty.list
deb [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu) natty main
deb-src [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu) natty main
fil@ubuntu:~$

---

### Post by skyzthelimit230 on 2011-05-09
> **satanselbow said:**
> There is a syntax error in one of the custom repos you have added which is causing the list not to load...

In a terminal:

```
sudo rm /etc/apt/sources.list.d/lorenzo-carbonell-atareao-natty.list
```

This will delete the custom list with the error.

You should be able to the fire up synaptic and reload your sources without error ;)

Hey!
Thanks! whatever this command did, it worked! Everything isback to normal. Now, can someone explain to me what I did to break it in the first place? haha

---

### Post by satanselbow on 2011-05-09
Looks like that ppa has been deleted :( but that in itself should not have given such a catastrophic error :confused:

Might have been a simple typo when entering the ppa details in the 1st place :(

---

### Post by skyzthelimit230 on 2011-05-09
> **satanselbow said:**
> Looks like that ppa has been deleted :( but that in itself should not have given such a catastrophic error :confused:

Might have been a simple typo when entering the ppa details in the 1st place :(

Ah thank you.

And I agree with your signature, I want a Gnubuntu too! :D

---

