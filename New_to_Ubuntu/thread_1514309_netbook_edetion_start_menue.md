---
title: "netbook edetion start menue"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by sullivanj094 on 2010-06-20
so i just installed ubuntu netbook edetion on my gatway netbook and I do not like how the menu stays on the left open at all times and I have no desktop items. is their a way to get rid of the always open menu and get it running more like osx with a dock or is this just a netbook edetion thing 
thanks

---

### Post by KdotJ on 2010-06-20
Hello and welcome to the Ubuntu forums.
The interface you're describing is purely due to it being the Netbook Edition interface. If you wish to have the "normal" desktop then you can get it by doing the following:

- Open a terminal (Accessories > Terminal)
- Typing the following in:

```
sudo apt-get install ubuntu-desktop
```

you will then be prompted for your password (Note: when you are typing in your password, nothing will show up on the current line in the terminal (i.e. no characters or *'s))

It will then start doing it's thing and stop at a point where it explains that X amount of hard disk space will be used. Press "y" to accept.

Once it has finished, you can reboot (or log out). When you get to the login screen click on your username. Before you enter your password to log in or press the log in button, look in the bottom right hand corner and there will be a drop down menu (technically a drop-up menu) where you can select what environment to boot into. It should currently say something like "Ubuntu Netbook Edition", you will need to select "GNOME".

Hope this helps

---

### Post by Bradtek on 2010-06-21
Much easier to choose "Gnome Session" at the login screen

---

