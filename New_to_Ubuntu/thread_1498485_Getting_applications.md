---
title: "Getting applications"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by foreverNewbie on 2010-05-31
Hello,

How do I get applications?  I know there is the Ubuntu Software Center but I have looking at other forums and they talk about command-line methods.  Something like:
sudo apt-get ....

Also, when I do install something on Ubuntu Software Center, USC, does it update the Application menu is it only through terminal.  Take for example gvim.  I just installed through USC but it isn't in the application menu.  It is installed because I was able to use it by typing gvim in the terminal and it came up.  

Final Question:
Is there an application or setting like Launchy in Windows?  

Yeah, I have a lot to learn!

---

### Post by Locke_99GS on 2010-05-31
Software Centre (and the other GUI methods of getting applications) are all front-ends for command-line tools such as apt-get or aptitude. They do the same thing that could be done on the command line, but in a graphical manner. It's prettier.

The command line is usually referenced in the forums and such because it is far more universal and easier to describe. Telling somebody to click here, then click here, then scroll down and search for this, then click this then that, is far mroe troublesome than just telling them to "sudo apt-get install this-cool-app". 

Most applications that have GUI's are installed into the menus for you, but some few are not. This is usually up to the developer (or a packager) to add XDG information to the program, so the menu entry can be created for it. There are, unfortunately, some applications which don't have XDG info yet, but you can add the program to the menu with the "alacarte" program. Run it from command line. There is a way to invoke it from the menu's, but I don't remember how. :)

I don't know what "Launchy" for windows is, but I'm assuming it is another way to manage or launch applications. There are a few different cool things available for Linux, such as AWN and Docky with are docks, similar to the Macintosh dock. There is also Gnome-do, which allows you to launch many programs (and perform other tasks) by typing just a few words.

---

### Post by frank002 on 2010-05-31
You can also try the Synaptic Package Manager.  Go to System>Administration>Synaptic Package  Manager and do a search for whatever application you are looking for.

---

### Post by NUboon2Age on 2010-05-31
I like Synaptic Package Manager because I can search for related packages, and see if I have a package installed, see which version is available, reinstall it, remove it, feel confident that it will be updated properly, etc., etc.

---

### Post by marty1011 on 2010-05-31
Learning is never a bad thing to do. Here is something to start with 

[https://help.ubuntu.com/8.04/serverguide/C/apt-get.html]("https://help.ubuntu.com/8.04/serverguide/C/apt-get.html")

[http://wiki.linuxhelp.net/index.php/Apt-get_Guide]("http://wiki.linuxhelp.net/index.php/Apt-get_Guide")

This should answer your questions (present & future).

---

### Post by ShadowMage on 2010-05-31
> **Locke_99GS said:**
> Most applications that have GUI's are installed into the menus for you, but some few are not. This is usually up to the developer (or a packager) to add XDG information to the program, so the menu entry can be created for it. There are, unfortunately, some applications which don't have XDG info yet, but you can add the program to the menu with the "alacarte" program. Run it from command line. There is a way to invoke it from the menu's, but I don't remember how. :)


In case this helps, here's how you can invoke it from the menus:
System > Preferences > Main Menu

Or, you can also right-click (when the menu is closed) and select "Edit Menus".

Btw thanks Locke_99GS, I actually never knew the command for this.

---

