---
title: "Map &lt;super&gt;H to open a nautilus browser window."
date: 2009-08-28
forum: New to Ubuntu
---

### Post by quinnten83 on 2009-08-28
Can someone please tell me how to do this?
I have tried everything I can think of.
First, I went to System> preferences> keyboard shortcuts. But there it is virtually impossible to get the <Super> key to map to anything.
After some google-ing I found that if you open gconf-editor (<alt>+F2>, type gconf-editor)>applications>metacity>keybindings, I could use the super key to create bindings. This worked great for binding the Terminal <Super>t and the Desktop <Super>D, but for the life of me, I could not find the option to open a filebrowser window.
So I went to keybinding commands and added on command_1 /usr/bin/nautilus and then in keybindings binded it to <Super>H, but it just will not open up an instance of nautilus. I checked in terminal (which i called up using <super>t) if the command was right, and nautilus opens when I issue that command.
So, what is it that I am doing wrong, or is nautilus just not that versatile???
Please help, I have been trying to figure this out for two years now.

---

### Post by darthmob on 2009-08-28
I had that problem for a long time as well. The solution is actually quite simple - you just have to provide the path it should open!

Eg.
```

nautilus computer:///
or
nautilus ~/

```

And then it works. :)

PS: You don't have to write the full /usr/bin/ path as the executables in that directory get scanned automatically.

---

### Post by quinnten83 on 2009-08-28
> **darthmob said:**
> I had that problem for a long time as well. The solution is actually quite simple - you just have to provide the path it should open!

Eg.
```

nautilus computer:///
or
nautilus ~/

```

And then it works. :)

PS: You don't have to write the full /usr/bin/ path as the executables in that directory get scanned automatically.

No such luck I am afraid.
I don't understand what I could be doing wrong, as all other key-bindings work. I might be setting up the command wrong. This would be the only binding with a command. And when I tried doing it with Inkscape as well, I get the same effect which is nothing happens....
(see pic).

---

### Post by darthmob on 2009-08-28
Sorry I can't really help with the metacity bindings as I'm using openbox which has it's own shortcuts.

But you may follow the example [here]("https://help.ubuntu.com/community/Metacity#Keybinding_commands") step by step. And if that doesn't work something's seriously wrong. :)

---

### Post by kukibird1 on 2009-08-28
Try this.

[http://maketecheasier.com/making-full-use-of-the-super-windows-key-in-gnome/2009/03/31]("http://maketecheasier.com/making-full-use-of-the-super-windows-key-in-gnome/2009/03/31")

---

### Post by quinnten83 on 2009-09-01
Thanx guys and girls,
I will check these out during the weekend when I have a bit more time.

---

