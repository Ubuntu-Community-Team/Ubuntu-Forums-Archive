---
title: "Old dog just learned new trick - Don't use &quot;sudo&quot; for graphic apps!"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by emarkay on 2009-10-12
"You should **never** use normal sudo to start graphical applications as root. You should use gksudo (kdesudo on *Kubuntu*) to run such programs.  gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by root. (AFAICT, this is all that's special about the environment of the started process with gksudo vs. sudo)."

[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)
:)

---

### Post by HarrisonNapper on 2009-10-12
Thanks for the post. I learned this the hard way, so hopefully others will see this before they follow the path of security destruction.

Edit: gksudo is do as graphical super user, so, functionally, is gksu the UI app equivalent to su?

---

### Post by Penguin Guy on 2009-10-12
I knew that you were supposed to use [COLOR="Green"]gksudo[/COLOR] for graphical applications, but never knew why, thanks for taking the time to explain this. You also just made me realize that [COLOR="Green"]gksudo[/COLOR] is actually completely different to [COLOR="Green"]gksu[/COLOR] - lucky I haven't caused any harm yet.

> **HarrisonNapper said:**
> Edit: gksudo is do as graphical super user, so, functionally, is gksu the UI app equivalent to su?
Yes, it is.

---

### Post by sisco311 on 2009-10-12
> **HarrisonNapper said:**
> 
Edit: gksudo is do as graphical super user, so, functionally, is gksu the UI app equivalent to su?

> **Penguin Guy said:**
> You also just made me realize that gksudo is actually completely different to gksu - lucky I haven't caused any harm yet.


Yes, it is.

GKSu is a library that provides a Gtk+ frontend to su and sudo.

gksudo is just a symbolic link to gksu. 

You can set the *Authentication mode *to in *gksu-properties*.

---

### Post by Penguin Guy on 2009-10-12
> **sisco311 said:**
> gksudo is just a symbolic link to gksu.
That's what I though 'till I took a look in the man page:

```

GKSU(1)                          User Commands                         GKSU(1)

NAME
       gksu - GTK+ frontend for su and sudo

SYNOPSIS
       gksu

       gksu [-u <user>] [options] <command>

       gksudo [-u <user>] [options] <command>

DESCRIPTION
       This manual page documents briefly gksu and gksudo

       **gksu  is a frontend to su and gksudo is a frontend to sudo**.  Their pri&#8208;
       mary purpose is to run graphical commands that need  root  without  the
       need to run an X terminal emulator and using su directly.

       . . .


```

---

### Post by sisco311 on 2009-10-12
> **Penguin Guy said:**
> That's what I though 'till I took a look in the man page:



bah, man pages... :)

```
sisco@acme:~$ ls -al /usr/bin/gksu*
-rwxr-xr-x 1 root root 28176 2009-05-06 19:46 /usr/bin/gksu
-rwxr-xr-x 1 root root 14736 2009-07-30 20:15 /usr/bin/gksu-properties
**l**rwxrwxrwx 1 root root     4 2009-07-21 10:36 **/usr/bin/gksudo -> gksu**

```

---

### Post by CharlesA on 2009-10-12
Does that mean you don't need to use gksudo unless you aren't running an X-server?

I've been trying to use gksudo instead of sudo, but I don't notice any difference.

Thanks for the explanation.

---

### Post by HarrisonNapper on 2009-10-12
> **CharlesA said:**
> Does that mean you don't need to use gksudo unless you aren't running an X-server?

I've been trying to use gksudo instead of sudo, but I don't notice any difference.

Thanks for the explanation.

Well, you really can sudo just about anything, but if you're running an app with a UI (especially if it is only the UI like grsync or clamtk), you want to use gksudo or gksu.

---

### Post by Hated On Mostly on 2009-10-12
To add to the confusion there is also a gnomesu command which is another GTK+ frontend to su, but thankfully if you are using Ubuntu you don't have that one, so no need to think about it too much.

In openSUSE for example instead of using gksudo to launch a GUI program with root privileges you would use gnomesu.

---

### Post by Penguin Guy on 2009-10-12
> **CharlesA said:**
> Does that mean you don't need to use gksudo unless you aren't running an X-server?

I've been trying to use gksudo instead of sudo, but I don't notice any difference.

Thanks for the explanation.
For one thing, [COLOR="Green"]sudo[/COLOR] asks for a password in the terminal, whereas [COLOR="Green"]gksudo[/COLOR] asks for a password in a popup.

---

