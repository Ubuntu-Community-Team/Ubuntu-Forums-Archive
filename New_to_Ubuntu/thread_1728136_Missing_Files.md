---
title: "Missing Files?"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by labsdex on 2011-04-13
I've recently installed Ubuntu Notebook Remix on my laptop...
Which means I'm new to the software...
So, does anybody know where the files in Local Disk (C: ) are now?

Oh and please move this topic if I'm on the wrong section. Sorry.

---

### Post by sanderd17 on 2011-04-13
you can open the filemanager: search it somewhere or press ALT+F2 and type
```

nautilus

```

there you should have "computer" on the left side and there you should see your windows drives. Names like C, D ... aren't known by Ubuntu

If you don't find it, can you install gparted: search it in the software center of open a terminal with CTRL+ALT+T and type
```

sudo apt-get install gparted

```

then open gparted from the menu and post a screenshot here.

---

### Post by labsdex on 2011-04-13
First of all, thanks for trying to help me.

Anyway, I don't have a gparted installer, where can I get one?

And when I entered nautilius, only a window that showed 'Desktop','Documents','Downloads', etc.

---

### Post by sanderd17 on 2011-04-13
You're no native English speaker are you?

So you don't find your files in nautilus? I'll give you the steps to install gparted:

**Graphical:**
[LIST=1]
[*]press ALT+F2
[*]type
```

gksu synaptic

```
and press enter
[*]search for "gparted"
[*]right click to select it to install
[*]apply the changes
[/LIST]
**Comand line:**
[LIST=1]
[*]Press CTRL+ALT+T to get the terminal
[*]type
```

sudo apt-get install gparted

```
to install it
[/LIST]

Then search gparted in your applications and post a screenshot of it.

---

### Post by labsdex on 2011-04-13
I already searched but there's no gparted file anywhere... :(

---

### Post by sanderd17 on 2011-04-13
So you installed gparted? That worked?

Well, if you don't find it in the menu, open it by pressing ALT+F2 and type
```

gksudo gparted

```

---

### Post by grahammechanical on 2011-04-13
You may be unfamiliar with the way Linux and Ubuntu present information about files. In windows you see Drive C: and Drive D:   In Ubuntu and Linux we see partitions. Even a second hard disc will be shown as a partition.

When I open the Nautilus file manager I do not see Drive C: or any of that stuff. I see a folder with my name on it. Inside that folder are all my files and documents, each in their own folder. They are in fact in a partition that the operating system knows as /home. Windows would call this Drive D: 

In the panel on the left I see File System. This is actually the partition where the operating system exists. In Windows this would be Drive C: The file manager has blended two drives/partitions so that I do not see them a separate entities.

You may not have your data and documents files on a separate partition but the file manager would present the information in much the same way as I have described. The folder called Home and the one with your name is where your documents are. File System is where the operating system is stored.

If you want to view the hard disc open a utility call Disk Utility. I think that you will find it as an accessory. I may be wrong. At the moment I am trying out Ubuntu 11.04 Beta and I am using the Unity interface and things are displayed differently. So, I cannot give you precise directions.

I hope that this helps.

Regards.

---

### Post by sanderd17 on 2011-04-13
> **grahammechanical said:**
>  At the moment I am trying out Ubuntu 11.04 Beta and I am using the Unity interface and things are displayed differently. So, I cannot give you precise directions.


The OP is using unity too (netbook edition) so I think you can give more precise instructions than I can.

I just wanted him to open gparted so that I know he still has the windows partitions (and he didn't erase them on the install)

---

### Post by mikewhatever on 2011-04-13
Wait a minute! Gparted? Why? Are you going to edit partitions?

labsdex, have you installed Ubuntu inside Windows or side by side?

---

### Post by labsdex on 2011-04-14
@grahammechanical: Thanks for the help!

@mikewhatever: Side by side

---

