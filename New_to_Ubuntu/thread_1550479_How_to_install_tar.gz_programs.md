---
title: "How to install tar.gz programs?"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by Attack3 on 2010-08-11
Specifically install_flash_player_10_linux.tar.gz

---

### Post by da burger on 2010-08-11
Hi, .tar.gz can be installed in a million different ways depending on what it contains, but you probably don't need it. There are lots of ways to install software in ubuntu so just so you know, here are the things you should look out for:

1)A piece of software in the repositories (in software center or synaptic)
2)A .deb file.
3)Failing those two you may need to look into tar.gz and other install methods but these are not ideal.

---

### Post by Attack3 on 2010-08-11
> 1)A piece of software in the repositories (in software center or synaptic)
What is that?

---

### Post by S.R on 2010-08-11
Hopefully this will answer your question a little better and I am guessing you have version 9 of flash player. Be sure to close Firefox and the in the terminal.

```
sudo apt-get remove flashplugin-nonfree
```

Then...

```
sudo dpkg -i install_flash_player_10_linux.deb
```

That should just about do it.

---

### Post by Perfect Storm on 2010-08-11
You don't need to hunt down software in Ubuntu. You use 'Ubuntu Software Center' or Synapatic Package Manager to install software.
If you click Applications tab you'll see Ubuntu Software Center.

[[img]http://www.imageviper.com/displayimage/157637/0/Flash-pre.png[/img]](http://www.imageviper.com/displayimage/157636/0/Flash.png)

---

### Post by Attack3 on 2010-08-11
> **S.R said:**
> Hopefully this will answer your question a little  better and I am guessing you have version 9 of flash player. Be sure to  close Firefox and the in the terminal.

```
sudo apt-get remove flashplugin-nonfree
```Then...

```
sudo dpkg -i install_flash_player_10_linux.deb
```That should just about do it.

> **Artificial Intelligence said:**
> You don't need to hunt down  software in Ubuntu. You use 'Ubuntu Software Center' or Synapatic  Package Manager to install software.
If you click Applications tab you'll see Ubuntu Software Center.

[[IMG]http://www.imageviper.com/displayimage/157637/0/Flash-pre.png[/IMG]]("http://www.imageviper.com/displayimage/157636/0/Flash.png")

okay. I understand :P

How about Sun java? I search it in software centre but it has no install option and when double clicked it says "To show information about this item, software catologue needs updating"

---

### Post by jtarin on 2010-08-11
[Sun Java]("http://www.raymond.cc/blog/archives/2010/05/21/installing-sun-java-in-buntu-10-04-long-term-support/")

---

### Post by 3rdalbum on 2010-08-11
Sun   Java   is   in   the   Partner   repository.   You   need   to   go   to   System,   Administration,   Software   Sources   and   then   the   Other   Software   tab   to   enable   Partner.

---

