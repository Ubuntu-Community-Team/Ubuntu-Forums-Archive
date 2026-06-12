---
title: "Apps do not display on &quot;desktop&quot;"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by alevenso on 2010-04-07
I loaded Ubuntu 9.04 into a Windows 7 Virtual PC , installed with safe graphics - it installs and boots up into the console - but when I try to launch any application I see the app starting to come up on the the taskbar , but then disappears and never opens - sometimes this cause the image to reboot - I am guessing its some display issue - but dont know where to start because I cant even start a command line

---

### Post by Psumi on 2010-04-08
> **alevenso said:**
> I loaded Ubuntu 9.04 into a Windows 7 Virtual PC , installed with safe graphics - it installs and boots up into the console - but when I try to launch any application I see the app starting to come up on the the taskbar , but then disappears and never opens - sometimes this cause the image to reboot - I am guessing its some display issue - but dont know where to start because I cant even start a command line

Are the apps not going to the taskbar and starting minimized? Try Alt+tab.

Are the apps going to another workspace? Try going to another workspace by either clicking on the other workspaces, or CRTL+ALT+Left/Right Arrow.

It might not even be a display issue, the apps may just be crashing. try dmesg | tail in terminal.

if you cannot get terminal to come up, go into TTY1: CRTL+ALT+F1. Login with your username and password.

When it asks for your password, the cursor will not move nor show asterisks, THIS IS NORMAL, just type your password, and hit enter.

---

### Post by aeiah on 2010-04-08
once on the command line do
```

dmesg
```

and it should give you some info about what's happening to your apps after you start them

---

### Post by Psumi on 2010-04-08
> **aeiah said:**
> once on the command line do
```

dmesg
```

and it should give you some info about what's happening to your apps after you start them

That gives too much log. dmesg | tail should be sufficient.

---

### Post by aeiah on 2010-04-08
> **Psumi said:**
> That gives too much log. dmesg | tail should be sufficient.

what does it matter? he's doing it from TTY1 so he will only be able to see what, 20 lines? why bother tailing so you only see the last 10 lines?

---

### Post by Psumi on 2010-04-08
> **aeiah said:**
> what does it matter? he's doing it from TTY1 so he will only be able to see what, 20 lines? why bother tailing so you only see the last 10 lines?

Because you can't scroll up in TTY.

---

### Post by mcduck on 2010-04-08
> **Psumi said:**
> Because you can't scroll up in TTY.

Of course you can. Shift+PgUp. :)

---

### Post by Psumi on 2010-04-08
> **mcduck said:**
> Of course you can. Shift+PgUp. :)

How should a newbie like me know that?

---

### Post by mcduck on 2010-04-08
> **Psumi said:**
> How should a newbie like me know that?

Now you do. :)

Same thing as with anything else in life, you learn it from somewhere. In this case probably from any tutorial about using the CLI in Linux, the manuals, other people, or whatever way you prefer to learn things. 

You can find a pretty good (although not complete) list of some of the most common Bash shortcuts here: [http://beerpla.net/2008/12/22/mastering-the-linux-shell-bash-shortcuts-explained/]("http://beerpla.net/2008/12/22/mastering-the-linux-shell-bash-shortcuts-explained/"). there's even a downloadable PDF cheatsheet available. Check Bash manual & docs for a complete list, if you want one.

---

### Post by 3rdalbum on 2010-04-08
Virtual PC is not a good environment for trying out Linux distros, basically because it's only built with the bare minimum necessary to run Windows virtually. Microsoft doesn't test Virtual PC with Linux... I mean, it's not like they want anyone to have a good Linux experience in Virtual PC :-)

Virtualbox is much better for virtualisation of non-Microsoft operating systems, and from what I hear it's pretty much on par with Virtual PC when you're running Windows virtually.

---

