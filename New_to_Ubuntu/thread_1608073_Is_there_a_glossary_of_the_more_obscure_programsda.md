---
title: "Is there a glossary of the more obscure programs/daemons that run under Ubuntu?"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by desconocido on 2010-10-28
I keep seeing references to these names in various posts, but I don't really know what they do. For example:

nautilus, seahorse, metacity, dbus, avahi, compiz, hald, getty, acpid, gdm, bonobo, gvfs, alsa

It would be nice if there was a glossary someplace where you could see them all at once. I tried googling but no luck.

Bye for now,

---

### Post by ArgusVision on 2010-10-28
I'd be interested in seeing something like that myself.
I'll get back to you if I find any.

---

### Post by ubunterooster on 2010-10-28
Do you have any idea how many *thousands* there are? ;)

---

### Post by mcduck on 2010-10-28
I doubt that there would be any single list of all these, but a Google or Wikipedia search for each individual application should tell you everything you want to know.

Anyway,

Nautilus - the file manager of Gnome. Also handles your desktop.

Seahorse - Gnome's keyring manager. Keyring stores passwords, encryption keys and stuff like that from all applications in a single place, keeping them safely encrypted when you are not logged in.

Metacity - Gnome's window manager. Gives you window borders & titlebars, allowing you to move our windows around and whatever you'd expect windows to do on a graphical OS.

Compiz - alternative for Metacity, providing compositing (read: transparency) and pretty effects in addition to normal window manager functions.

dbus - provides a way for programs to communicate with each other

hald - HAL Daemon (HAL is for Hardware Abstraction Layer), provides easier way for programs to access your computer's hardware

getty - handles the TTY's (the text temrinals you can access with Ctrl-Alt-F1 &#8211; Ctrl-Alt-f6)

acpid - ACPI is for Advanced Advanced Configuration and Power Interface, a standard for detection, configuration & power management of computer components.

GDM - Gnome Display Manager, handles user logins (for graphical desktops), user sessions, starting the desktop environment and stuff like that. If you use password login, GDM is the one that gives you the login screen.

gvfs - Gnome Virtual File System. I'm not sure how I could explain virtual file system in an easy way, but perhaps a wikipedia link helps here: [http://en.wikipedia.org/wiki/Virtual_file_system]("http://en.wikipedia.org/wiki/Virtual_file_system").

alsa - Advanced Linux Sound Architecture, provides automatic configuration (& drivers) for sound cards, and a low-latency professional level interface for your programs to use the soundcard. Think ASIO, if you've used decent soundcards on Windows.

Avahi - automatic detection of computers and services on a local network, without configuration. Much like Apple's Bonjour.

I'll definitely leave Bonobo for somebody else to explain. :D

---

### Post by Jetso on 2010-10-28
Well here are some you listed that *I* know:

Nautilus: A file browsing program... Same thing as Windows Explorer

Seahorse: Has something to do with passwords and keys, but I don't know much about it.

Compiz: A program that you can use to add cool effects for your desktop, such as Wobbly Windows, Animations, Desktop Cube, and Rotate desktop cube.

And thats all I know... Sorry :(

---

### Post by Jetso on 2010-10-28
Oh, sorry mcduck, your reply wasn't there when I saw this post and was replying.

---

### Post by mcduck on 2010-10-28
> **Jetso said:**
> Oh, sorry mcduck, your reply wasn't there when I saw this post and was replying.

no reason to be sorry about helping somebody on the forums. :)

Besides, it *did* take me a while to figure out how to explain all those in English.

---

### Post by ubunterooster on 2010-10-28
Bonobo is a set of language and system independent CORBA interfaces for  creating reusable components (controls) and creating compound  documents.

---

### Post by desconocido on 2010-10-29
Thanks everyone, that's great. A Glossary would still be a good idea.

While we are on the topic of bizarre names, anyone seen "futex_wait_queue_me" before?

---

### Post by ubunterooster on 2010-10-29
> **desconocido said:**
> Thanks everyone, that's great. A Glossary would still be a good idea.

While we are on the topic of bizarre names, anyone seen "futex_wait_queue_me" before?
Never heard of it.

Next time, try ```
apropos *command*
```

---

### Post by gordintoronto on 2010-10-29
There's also:
[http://en.wikipedia.org/wiki/List_of_GNOME_applications](http://en.wikipedia.org/wiki/List_of_GNOME_applications)

---

### Post by ubunterooster on 2010-10-29
That lists "common" ones; this thread is about the **"more obscure programs/daemons"**

---

### Post by Omnomnom on 2010-10-29
I'd like to know too, seeing as I'm a total "Noob" to this Ubuntu thing, and only know what the people said here and Nautilus.

---

### Post by ubunterooster on 2010-10-29
Run ```
apropos *command*
```
An example [COLOR=White](yes, my PC is named mountaindew)[/COLOR]
```
ubunterooster@mountaindew:~$ apropos nautilus
nautilus (1)         - the GNOME File Manager
nautilus-actions-config-tool (1) - configure programs to launch from the naut...
nautilus-actions-new (1) - create new nautilus actions
nautilus-actions-run (1) - execute an action on the specified target
nautilus-actions-schemas (1) - output the nautilus-actions GConf schema to ST...
nautilus-connect-server (1) - To Access a remote server
nautilus-file-management-properties (1) - File Management Preferences
nautilus-pastebin-configurator (1) - Nautilus Pastebin configuration panel
nautilus-scripts-manager (1) - easy tool for nautilus scripts management
nautilus-sendto (1)  - convenience application to send a file via email or in...
ubunterooster@mountaindew:~$ 
```

---

### Post by ArgusVision on 2010-10-30
While we're on that in addition to apropos, you can use ```
man *command*
```
(where you replace commmand with the name of the command you want to research) to view more details and options

---

### Post by ArgusVision on 2010-10-30
I'm not sure how well it fits the request but you could look here as well.
[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)
 It's useful, but I have to admit, it still has you searching. But the difference here is that [FONT="Fixedsys"]apropos[/FONT] and [FONT="Fixedsys"]man[/FONT] only display info on apps you have installed. This could give you info on the more obscure ones.

---

### Post by A_M_S on 2010-10-30
For a brief description of the applications on your system try in the command line:

 dpkg -l |less

---

### Post by desconocido on 2010-11-11
> **ubunterooster said:**
> 
Next time, try ```
apropos *command*
```

Yes, it seems to have something to say for most of those words. e.g.
> $ apropos getty
getty (8 )            - alternative Linux getty
$ apropos hald
hald (8 )             - HAL daemon
$ apropos compiz
compiz (1)           - OpenGL window and compositing manager
compiz.real (1)      - OpenGL window and compositing manager
gtk-window-decorator (1) - Compiz window decorator using the Gtk toolkit

A glossary (with a gui?) would still be nice.

---

### Post by mcduck on 2010-11-11
> **desconocido said:**
> Yes, it seems to have something to say for most of those words. e.g.


A glossary (with a gui?) would still be nice.

Apropos is only really useful when you *don't know* what command/tool to use for something and need to find out. (if you already know the name of the program/command, the man pages will tell you a lot more than simple apropos search would)

```
mcduck@Hyperion:~$ apropos "text editor"
ed (1)               - text editor
ex (1)               - Vi IMproved, a programmers text editor
gedit (1)            - text editor for the GNOME Desktop
gnome-text-editor (1) - text editor for the GNOME Desktop
red (1)              - text editor
rview (1)            - Vi IMproved, a programmers text editor
rvim (1)             - Vi IMproved, a programmers text editor
vi (1)               - Vi IMproved, a programmers text editor
view (1)             - Vi IMproved, a programmers text editor
vim (1)              - Vi IMproved, a programmers text editor
xedit (1)            - simple text editor for X
```


Anwyay, if you want more detailed descriptions, and a GUI, then Google really is the best tool. Also Gnome's Help viewer is able to read man & info pages (It's not as obvious as in older versions, but you can still use the search to access them)

---

### Post by cbemerine on 2010-11-15
> **desconocido said:**
> Thanks everyone, that's great. A Glossary would still be a good idea.

While we are on the topic of bizarre names, anyone seen "futex_wait_queue_me" before?


One post referenced Firefox, however this is happening to me with OpenOffice.org v3+ on Ubuntu 10.04.  I was planning to switch to LibreOffice anyway, but I seriously doubt that this wait queue state is specific to either OOo or FF.  

Basically OOo Writer just locked up and this is the state in the System Monitor, under the  Waiting Channel column.  FYI, I can still do anything I want with FF, including post this message.

---

