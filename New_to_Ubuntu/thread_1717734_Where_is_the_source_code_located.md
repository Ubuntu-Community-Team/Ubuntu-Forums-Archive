---
title: "Where is the source code located ?"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by josephmills on 2011-03-30
Hi there again I was just wondering where some if not all of the source code is located? So say I wanted to look at the source code  for compiz where would I find that? Thank you so much for your time.

---

### Post by andrewthomas on 2011-03-30
You need to enable the source repos and specifically download it.

---

### Post by donkyhotay on 2011-03-30
Source code is generally not downloaded by default since it takes up space and most people don't need the source code. If you really want it you can get it from the repo's as mentioned previously but personally I usually go to the website and get it directly from there so I know exactly where it is and I can just delete it all when I'm done.

---

### Post by josephmills on 2011-03-30
> **andrewthomas said:**
> You need to enable the source repos and specifically download it.
ok I went to System-->admin--> synaptic pack manager then  
I went to the setting--> respiratory's and made sure that all of the tick marks where checked (see pic) Could you please tell me a good link to get the source  say compiz or anything as a test run thanks

---

### Post by stmiller on 2011-03-30
You can search for it on packages.ubuntu.com . Source files are on the right.

Ex:

[http://packages.ubuntu.com/maverick/compiz](http://packages.ubuntu.com/maverick/compiz)


Download Source Package compiz:
[compiz_0.8.6-0ubuntu9.dsc]
[compiz_0.8.6.orig.tar.gz]
[compiz_0.8.6-0ubuntu9.diff.gz]

---

### Post by tgm4883 on 2011-03-30
or via apt-get

```
apt-get source compiz
```

You may get a messaging telling you where the source is, in order to get more up to date source packages

:EDIT:

Note, you do not need sudo to use apt-get to download source as it sticks it in the same dir you are in

---

### Post by josephmills on 2011-03-30
Hi there again and sorry about the delay I had to work :( after trying ```
sudo apt-get source 
``` I get this ```
Could not open file /var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_maverick_contrib_source_Sources - open (2: No such file or directory)
```I am not sure what it means maybe that vbox is mucking up things with something or may be it has something to do with my repository. well could some one help me with this thanks

---

### Post by tgm4883 on 2011-03-30
> **josephmills said:**
> Hi there again and sorry about the delay I had to work :( after trying ```
sudo apt-get source 
``` I get this ```
Could not open file /var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_maverick_contrib_source_Sources - open (2: No such file or directory)
```I am not sure what it means maybe that vbox is mucking up things with something or may be it has something to do with my repository. well could some one help me with this thanks

That would be the closed source version of virtualbox. Closed source meaning that you can't download the source for it.

---

### Post by josephmills on 2011-03-30
> **tgm4883 said:**
> That would be the closed source version of virtualbox. Closed source meaning that you can't download the source for it.
I am so sorry ,I forgot to put the compiz in the code tag. I have attached a screen shot. Thanks for looking :)

---

### Post by Locke_99GS on 2011-03-30
Go to software sources and disable the source repository for virtualbox, since it doesn't exist and is mucking up apt.

---

### Post by josephmills on 2011-03-31
Thank you all for all of you input today. In school today I  learned how to find source codes and how to play with respiratory's.  I failed at port forwarding but that is another thread thank you all for your input \\:D/

---

