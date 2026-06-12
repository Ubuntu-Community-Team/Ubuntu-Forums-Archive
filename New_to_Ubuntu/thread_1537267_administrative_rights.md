---
title: "administrative rights"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by H43N15 on 2010-07-23
so i ran the comand to get my nvidia glx legacy and it spat out this

katherine@katherine-desktop:~$ sudo apt-get install nvidia-glx-legacy
[sudo] password for katherine: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
katherine@katherine-desktop:~$ 

i gave the right pasword but it wont let me on even though thats the name under the administator account.....wats up? all i want to do is get my extras effects to get my compiz sphere but it wont let me download the driver

---

### Post by mikechant on 2010-07-23
I believe this message

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
```


usually means you have some other package manager running at the same time - e.g. add/remove programs, synaptic etc.
If so you need to close that first.

---

### Post by H43N15 on 2010-07-23
reooted, ran it again and got this
katherine@katherine-desktop:~$ sudo apt-get install nvidia-glx-legacy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-glx-legacy
katherine@katherine-desktop:~$

---

### Post by aust77 on 2010-07-23
Google search it. Sometimes refined google searches can solve your problems so you won't always need to use the forums. For example, I searched "nvidia glx legacy ubuntu" and found [this]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") nifty page. Remember to include keywords such as "ubuntu" and words related to the situation. You'll find this trick very helpful.

Cheers,



aust77

---

### Post by bodhi.zazen on 2010-07-23
> **H43N15 said:**
> reooted, ran it again and got this
katherine@katherine-desktop:~$ sudo apt-get install nvidia-glx-legacy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-glx-legacy
katherine@katherine-desktop:~$

May I ask, what version of Ubuntu are you running and what problem are you having ?

The wiki page helps 

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

nvidia-glx-legacy is old, see

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvidia&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvidia&searchon=name&subword=1&version=all&release=all)

So version depends on what version of Ubuntu you are using.

You can search for nvidia drivers with

```
apt-cache search nvidia
```

---

### Post by emoguitarist06 on 2010-07-23
> **H43N15 said:**
> reooted, ran it again and got this
katherine@katherine-desktop:~$ sudo apt-get install nvidia-glx-legacy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-glx-legacy
katherine@katherine-desktop:~$

Try seaching that package in Synaptic Package Manager

---

### Post by aust77 on 2010-07-23
> **bodhi.zazen said:**
> May I ask, what version of Ubuntu are you running and what problem are you having ?

The wiki page helps 

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

nvidia-glx-legacy is old, see

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvidia&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvidia&searchon=name&subword=1&version=all&release=all)

So version depends on what version of Ubuntu you are using.

You can search for nvidia drivers with

```
apt-cache search nvidia
```

Hehe, we both recommended the same help.ubuntu.com page.

---

