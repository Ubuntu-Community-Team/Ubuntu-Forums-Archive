---
title: "what is the terminal code for downloading and installing deluge?"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-19
I'm using hardy heron.  Do I need to add any repositories to get this to happen?

---

### Post by SuperSonic4 on 2010-02-19
Depends how up to date you want it

I'd suggest adding the deluge PPA: [https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

---

### Post by hortstu on 2010-02-19
> **SuperSonic4 said:**
> Depends how up to date you want it

I'd suggest adding the deluge PPA: [https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)


Thanks I'm a little new to this... what should the aptline lookl like for that?

---

### Post by rolnics on 2010-02-19
If you want the install from hardy repos then open a terminal and enter the following code:- 
```
sudo apt-get install deluge
```

---

### Post by hortstu on 2010-02-19
> **rolnics said:**
> If you want the install from hardy repos then open a terminal and enter the following code:- 
```
sudo apt-get install deluge
```

I tried that before my post.

```
mike@mike-laptop:~$ sudo apt-get install deluge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package deluge
mike@mike-laptop:~$ 


```

---

### Post by tom.swartz07 on 2010-02-19
> **hortstu said:**
> I tried that before my post.

```
mike@mike-laptop:~$ sudo apt-get install deluge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package deluge
mike@mike-laptop:~$ 


```

its ```
sudo apt-get install deluge-torrent
```

or try ```
sudo apt-get install deluge*
```

It seems that they changed the name to a shorter version after hardy. 
[https://launchpad.net/ubuntu/hardy/lpia/deluge-torrent](https://launchpad.net/ubuntu/hardy/lpia/deluge-torrent)

---

### Post by hortstu on 2010-02-19
> **tom.swartz07 said:**
> its ```
sudo apt-get install deluge-torrent
```

or try ```
sudo apt-get install deluge*
```

It seems that they changed the name to a shorter version after hardy. 
[https://launchpad.net/ubuntu/hardy/lpia/deluge-torrent](https://launchpad.net/ubuntu/hardy/lpia/deluge-torrent)

Thanks tom the first one worked...

can anyone help me update the repositories?

---

### Post by Sector11 on 2010-02-19
> **hortstu said:**
> Thanks tom the first one worked...

can anyone help me update the repositories?

```
man apt-get
```

tells me that:
```
sudo apt-get update
```
is what you are looking for.

>        update

           update is used to resynchronize the package index files from their
           sources. The indexes of available packages are fetched from the
           location(s) specified in /etc/apt/sources.list. For example, when
           using a Debian archive, this command retrieves and scans the
           Packages.gz files, so that information about new and updated
           packages is available. An update should always be performed before
           an upgrade or dist-upgrade. Please be aware that the overall
           progress meter will be incorrect as the size of the package files
           cannot be known in advance.

s11

---

### Post by hortstu on 2010-02-19
thanks sector

---

