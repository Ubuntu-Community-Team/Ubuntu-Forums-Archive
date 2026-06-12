---
title: "What does &quot;need a repository as argument&quot; mean"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by Andavane on 2010-07-22
I'm trying to install java runtime on Lucid using this guide:
[http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html]("http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html")

I get this line shown in attachment and in title line.

How to proceed?

---

### Post by RiceMonster on 2010-07-22
Try typing it all as one line

---

### Post by wojox on 2010-07-22
Try mine. It's easier. [URL="http://wojox.homelinux.org/?p=78"]
Install Java 10.04
[/URL]

---

### Post by k3lt01 on 2010-07-22
The problem appears to be you have the repository line broken part way through the word canonical.

You can do the exact same thing in System > Administration >Software Sources > Other Software. Just put a tick in the Canonical line,click close, let it refresh and your done.

---

### Post by new__buntu on 2010-07-22
I'm not familiar with the add-apt-repository command, but your quotation marks might be causing issues. If that's not the problem you could edit your repository list via System > administration > software sources. Or failing that you could edit /etc/apt/sources.list yourself. More info on that [here]("https://help.ubuntu.com/community/Repositories/CommandLine").

---

### Post by k3lt01 on 2010-07-22
> **wojox said:**
> Try mine. It's easier. [URL="http://wojox.homelinux.org/?p=78"]
Install Java 10.04
[/URL]Only partly, the OP has already tried to add a line to his software sources list and failed. I'm seeing more and more noobs having problems trying to manually add lines via gedit or a terminal when it is easier and faster for many to do it via a GUI.

If you give people both options they can choose what is easiest for them. With the GUI option like I just gave him all he has to do is put a tick in a box for the repository because it is already there anyway.

---

### Post by Andavane on 2010-07-22
Thanks all ~
Everything going great guns now :D

---

### Post by jmstern on 2010-09-15
Although i did see this message at one point in the wee hours last night (after one successful install of SuSe (with Java), a crashed HD, etc..) I got past that by using Synaptic Package Manager to install sun-java6-bin & sun-java6-jre.  

Now my issue appears to be - How / where to do the link to Firefox?  

Thanks in advance
Sleeping as i await reply,

---

