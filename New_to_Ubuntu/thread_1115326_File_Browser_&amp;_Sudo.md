---
title: "File Browser &amp; Sudo"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by dimitriv on 2009-04-03
hi

I frequently need to transfer files between account home directories. I've done this through the terminal using sudo. Is there a way to do this through the UI e.g. file browser but admin rights are required. Perhaps there's a way to run File Browser in Sudo mode? I'd prefer to use a UI method. 

Thanks

---

### Post by binbash on 2009-04-03
Install dropbox (getdropbox.com) to your pc and use same dropbox accounts : ) Or if you don't want to do it via dropbox you can also use Grsync

---

### Post by stchman on 2009-04-03
> **dimitriv said:**
> hi

I frequently need to transfer files between account home directories. I've done this through the terminal using sudo. Is there a way to do this through the UI e.g. file browser but admin rights are required. I'd prefer to use a UI method. 

Thanks

You can bring up Nautilus with root privelages via the following command:

```
gksu nautilus
```

Only thing is be VERY careful as you will be able to delete whatever you want.

I recommend CLI to do administrative tasks.

---

### Post by dtoronto on 2009-04-03
i had the same issue a while back:

gksudo nautilus
allows transfer with sudo privileges on the GUI

---

### Post by IsmailBhai on 2009-04-03
or 

sudo nautilus 

will also work

---

### Post by halitech on 2009-04-03
> **IsmailBhai said:**
> or 

sudo nautilus 

will also work

it may work but it is not recommended as it will break things. the proper way to run a GUI app as sudo is gksu or gksudo as stchman has already stated.

---

### Post by tjwoosta on 2009-04-03
nautilus controls your entire desktop, including desktop icons and such, not just the file browser

if you do gksu nautilus it will run nautilus as root, but that will change your desktop wallpaper and everything because your settings are for the normal user not root


to open nautilus as root without chnaging the desktop you can do

```
gksu nautilus --no-desktop
```

or if you prefer the browser view

```
gksu nautilus --browser --no-desktop
```

---

### Post by apmcd47 on 2009-04-03
Stupid question, but is this on the same machine? Must be if you use sudo. How about putting both users into the same group and setting the group read permission on the two directory structures? Or alternatively use ACLs with the *getacl/setacl* commands. Security? Must be safer than using *gksudo nautilus*.

Alternatively, konqueror understands the fish protocol which allows you to view a filestore on a remote system using ssh. It'll work just as easily on the same machine. With usernames fred and george on the same machine and sshd running, type the following into the address bar while logged in as fred:
```
fish://george@localhost/
```
konqueror will prompt you for george's password.

Andrew

---

### Post by dimitriv on 2009-04-03
excellent, thank you for all the replies

gksudo nautilus sounds like what i was looking for

more newbie questions

if gksu is root, is gksudo less risky?
i thought sudo was like running as root

is gksudo nautilus any more risky than equivalent running as an Admin in Windows Explorer, and if so, how?

many thanks

---

### Post by halitech on 2009-04-03
gksu=gksudo, no real difference. sudo and gksu/gksudo still have you running as root but sudo is designed for terminal apps and gksu/gksudo is designed for graphical apps.

---

### Post by BoogeyOfTheMan on 2009-04-04
> **halitech said:**
> gksu=gksudo, no real difference. sudo and gksu/gksudo still have you running as root but sudo is designed for terminal apps and gksu/gksudo is designed for graphical apps.

In my limited experience, I noticed the sudo only works in the CLI, while gksudo works with the GUI. 

(On my system, if i type sudo in the CLI, it prompts for a password, if I create a shortcut like "sudo naulilus", it does nothing since there is no CLI window open to display the password prompt. Whereas "gksudo nautilus" pops up a window prompting me for the root password, then I type it in, nautilus opens as root, and I go about my business)

I find working in the GUI to be easier for most tasks for me, so I have a shortcut to open nautilus as root. Yes I know that technically the CLI is faster, safer, better, etc, but thats only if you are really familiar with the commands. I do find myself using it more and more as I get familiar. 

OP: It sounds like creating a shortcut that opens nautilus as root might be what you are looking for.

---

