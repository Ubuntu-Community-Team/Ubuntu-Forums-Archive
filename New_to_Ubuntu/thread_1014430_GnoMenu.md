---
title: "GnoMenu"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by metallicamike on 2008-12-17
I really want to get a start button but there is a problem. I don't even know what gnomenu is. is it the panel or is it something else? Also when i try to install it to usr/share/gnomenu/whatever there isn't even a gnomenu folder. any help on what to do to get it?

---

### Post by jimmy the saint on 2008-12-17
It looks like a .deb file to me.  double-click it and let it install.  I assume you just need to right-click on the taskbar and add it as an item once it is installed.

---

### Post by metallicamike on 2008-12-17
it is tar.gz wen i try to iextract it, it says (null)

---

### Post by EmgpJt on 2009-05-08
I am also having this problem, I am not very use to compiling and "sudo make install".

---

### Post by Uzi304 on 2009-05-08
[https://launchpad.net/gnomenu/trunk/1.6](https://launchpad.net/gnomenu/trunk/1.6)

There's a deb here.

---

### Post by upptown on 2009-05-31
> **Uzi304 said:**
> [https://launchpad.net/gnomenu/trunk/1.6](https://launchpad.net/gnomenu/trunk/1.6)

There's a deb here.

That is an old version and there have been significant improvements since it was released.  I was not able to download the latest (1.9.8 ) from launchpad directly.  Instead do a google for "gnomenu 1.9.8 softpedia".  Once you've downloaded the tar file extract it to your desktop.  To install launch your terminal and type: > sudo ~/Desktop/gnomenu/
then
> make install

first make sure you have the following dependencies by typing this in terminal:
> sudo apt-get install python python-xdg python-cairo python-gconf python-xlib deskbar-applet

Install for me was the easiest "make install" I've ever done.

---

### Post by Norm24 on 2009-05-31
```
sudo ~/Desktop/gnomenu/
```

After extracting to desktop and typing the above in terminal I get this:
```
sudo: /home/norm/Desktop/gnomenu/: command not found

```

Any ideas?I wouldn't mind trying this type of menu.

---

### Post by skompier on 2009-05-31
> **Norm24 said:**
> ```
sudo ~/Desktop/gnomenu/
```

After extracting to desktop and typing the above in terminal I get this:
```
sudo: /home/norm/Desktop/gnomenu/: command not found

```

Any ideas?I wouldn't mind trying this type of menu.

The command is wrong. Do...

```
cd /Desktop/gnomenu
```

Assuming that's where you extracted the file to.

Then..

```
sudo make install
```

---

### Post by mrebanza on 2009-11-22
ok???

Makefile: GnoMenu installed.

 now what??????

---

### Post by colin-m on 2009-12-02
The latest version is Gnomenu 2.1, and I recommend  installing it, since it incorporates a fairly major bugfix.
The simplest way to install it, is to use this link, [https://launchpad.net/~gnomenu-team/+archive/ppa]("https://launchpad.net/~gnomenu-team/+archive/ppa").

For those using Karmic, the procedure is fairly simple

Open a terminal and enter 'sudo add-apt-repository ppa:gnomenu-team/ppa' (without the ')
Then enter 'sudo apt-get update'
Then enter 'sudo apt-get install gnomenu'
Then close the terminal.

Right click on the top panel and click 'Add to Panel' and select gnomenu.

If anyone wants to know the Launchhpad procedure for installing gnomenu in Jaunty, or anyone wants to install the gnomenu tar file, please let me know.

---

### Post by colin-m on 2009-12-02
Please ignore my previous how-to, there is a problem with the Launchpad gnomenu repository.

---

