---
title: "cannot find installed application"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by mustard greens on 2009-07-06
I installed wordpress through the synaptic package manager, but cannot find it in the app menu.  ive tried several terminal commands from a previous post on the subject of finding lost apps.  synaptic says it was installed, but it doesnt show up with Xfce 4 appfinder, or through the terminal with locate or which.

---

### Post by nhasian on 2009-07-06
before you try to find something with *locate* did you run

```
sudo updatedb
```

---

### Post by dfreer on 2009-07-06
[http://packages.ubuntu.com/jaunty/all/wordpress/filelist](http://packages.ubuntu.com/jaunty/all/wordpress/filelist)

(1). It doesn't come with a *.desktop file, so it won't be in the "Applications" menu.
(2). Wordpress isn't really a program to open up anyways (like Notepad), it's basically just a set of web pages. If anything there would be a bookmark in firefox, rather than a shortcut in your menu.

I'd imagine it would've been easier to install it manually (e.g. navigating to [http://wordpress.org/](http://wordpress.org/) and following the install instructions) rather than installing a package, but to each their own.

---

### Post by mustard greens on 2009-07-06
tried sudo updateb, was told command not found.

---

### Post by mustard greens on 2009-07-06
why would it be easier when downloaded from wordpress site?

---

### Post by wojox on 2009-07-06
Now, browse to "http://localhost/wordpress" in your browser and click on the "install.php" link.

---

### Post by nhasian on 2009-07-06
you typed it wrong.  try copy and pasting the command:

```
sudo updatedb
```

then try to find the app with locate.

```
locate wordpress
```

> **mustard greens said:**
> tried sudo updateb, was told command not found.

---

### Post by mustard greens on 2009-07-06
navigating to localhost wordpress got me a 404 not found

---

### Post by mustard greens on 2009-07-06
ok after sudo updatedb (new spelling) was able to get the locate command to produce results.  what is the next step?

---

### Post by wojox on 2009-07-06
You have LAMP installed correct?

---

### Post by mustard greens on 2009-07-06
I believe LAMP is a set of server tools right?  I dont believe I have them installed as I am not running a server.

---

### Post by dfreer on 2009-07-06
> **mustard greens said:**
> I believe LAMP is a set of server tools right?  I dont believe I have them installed as I am not running a server.

LAMP generally means you have apache (web server), mysql (database), and php (programming language). All of which will be needed in order to use wordpress. As I said earlier, wordpress isn't an application it's basically a collection of pre-made web pages. You'll need to have a working web server in order to use it, and most of it's configuration and use will be done with your web browser.

I recommended installing wordpress manually, simply so that you would know where the files are located (because you would install them yourself), and to get the latest version. It's mainly involves downloading the archive, unpacking it in your web root, and pointing a browser to it's config page.

EDIT: If you installed wordpress via synaptic, it should have installed the LAMP stack now that I think about it. But it doesn't seem to actually place wordpress in the web root, it wants you to point apache toward /usr/share/wordpress/ (which is where it is installed BTW, the link I provided earlier should've shown that).

If you are still wanting to use the wordpress debian package, try reading the DOC's located in /usr/share/doc/wordpress/, specifically README.debian and readme.html

---

### Post by mustard greens on 2009-07-06
thank you dfreer.  it seems I may have jumped in over my head on starting with wordpress.  I just thought I could open it and poke around (thats how Ive gotten this far in ubunutu), and now in my reading I realize there is a lot more that I need to comprehend about the blogging process before I will be ready to even play with it.  maybe Ill try their quickblog service first until Ive got a better understanding of the basics.

---

### Post by wojox on 2009-07-06
Here's a good link to LAMP

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

