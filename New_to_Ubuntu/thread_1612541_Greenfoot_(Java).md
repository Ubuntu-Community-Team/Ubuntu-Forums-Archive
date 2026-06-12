---
title: "Greenfoot (Java)"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by noo 2 ubun2 on 2010-11-03
*I'm using 64-bit Maverick Meerkat (Ubuntu 10.10)*

[http://www.greenfoot.org/download/index.html](http://www.greenfoot.org/download/index.html)
I click the one that says "For **Debian**, **Ubuntu** and other Debian-based systems"
(the filename is [greenfoot-200.deb]("http://www.greenfoot.org/download/files/greenfoot-200.deb"))

Opening greenfoot-200.deb box pops up saying What should Firefox do with this file? and gives the option to _O_pen with or _S_ave File
it's automatically set on _O_pen with and Ubuntu Software Center (default) from the drop-down
all I do is click the button OK (without changing/clicking anything else)

brings up the Downloads box

when it finishes downloading, the Ubuntu Software Center opens with:
[INDENT]**Internal Error**
The file "/tmp/greenfoot-200.deb" could not be opened.
[/INDENT]and there is a big ? in a circle to the right of the Internal Error message, kinda like the *Post Icon* that I just selected (because it looks kinda like what I'm talking about)

anyone know what I have to do to be able to get Greenfoot

---

### Post by bioterror on 2010-11-03
You could try this command in terminal:

```

sudo dpkg -i /tmp/greenfoot-200.deb

```

If that doesnt work, could you please paste the error message.

Edit:

Hope you noticed this on the page

> 
Debian, Ubuntu and other Debian-based systems:

Check your distribution's instructions on how to install "deb" packages. In many cases it will be as simple as double-clicking the downloaded file from within a file manager, and then providing an administrator password to allow the installation to proceed.

Note the "deb" package requires one of the following packages to be installed:

sun-java6-jdk

Please note, the example scenarios will be installed under /usr/share/doc/Greenfoot/

On Ubuntu "Lucid Lynx" (10.04), the Sun JDK is no longer part of the multiverse section of the Ubuntu archive. To install it, you should open the Synaptic package manager, go to "Settings", "Repositories", "Other Software" tab, and enable the "lucid partner" repository, then close the dialog and press "Reload" in the main window; after completing these steps, it should be possible to install the "sun-java6-jdk" package.


---

### Post by noo 2 ubun2 on 2012-08-03
solved nearly 2 years later lol

---

### Post by overdrank on 2012-08-03
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

