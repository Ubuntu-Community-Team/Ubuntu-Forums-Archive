---
title: "want to use GPG-Agent instead of SSH-Agent"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by piso77 on 2008-04-23
Hi all,
I upgraded to Hardy and want to use my ssh-keys with the GPG-Agent (as I did before I did the upgrade). I deinstalled seahorse because it was not running with my GPG-Agent. My GPG-Agent was not running because SSH_AUTH_SOCK variable stuff as follows:

It seems that the SSH_AUTH_SOCK variable always points to a non-running SSH-Agent
```

heino@sora:~$ echo $SSH_AUTH_SOCK
/tmp/keyring-HUc
heino@sora:~$ ps ajx | grep ssh
    1  5720  5720  5720 ?           -1 Ss       0   0:00 /usr/sbin/sshd
10816 11539 11538 10816 pts/0    11538 R+    1000   0:00 grep ssh
2ZW/ssh


```

I don't know where SSH_AUTH_SOCK was set, because I already disabled the *use-ssh-agent* in */etc/X11/Xsession.options*.

I also deleted the */etc/X11/Xsession.d/XX...ssh-agent* script (I can't remember the correct name, because I deleted it), but after every restart of Xorg (and login) the SSH_AUTH_SOCK variable again points to the SSH-Agent (who is not running!)

I can use the GPG-Agent when I manually set the SSH_AUTH_SOCK with the *gpg-agent-info* File:

```

heino@sora:~$ eval `cat .gnupg/gpg-agent-info-sora`
heino@sora:~$ echo $SSH_AUTH_SOCK
/tmp/gpg-FmQDhx/S.gpg-agent.ssh

```

But this only works for the terminal I did this *eval ...*.
GPG-Agent is running and should be used, but it isn't, because SSH_AUTH_SOCK variable doesn't point to it.

Can anybody help me with some advice, so that I can use GPG-Agent as usual after login?

Thanks, piso.

---

### Post by jjs on 2008-09-11
> **piso77 said:**
> 
It seems that the SSH_AUTH_SOCK variable always points to a non-running SSH-Agent
```

heino@sora:~$ echo $SSH_AUTH_SOCK
/tmp/keyring-HUc
heino@sora:~$ ps ajx | grep ssh
    1  5720  5720  5720 ?           -1 Ss       0   0:00 /usr/sbin/sshd
10816 11539 11538 10816 pts/0    11538 R+    1000   0:00 grep ssh
2ZW/ssh


```

I don't know where SSH_AUTH_SOCK was set, because I already disabled the *use-ssh-agent* in */etc/X11/Xsession.options*.



I'm having similar problems. I want to use smartcards with ssh-agent. This was no problem in feisty, but in hardy i'm still having problems to get this working.
(in the original ubuntu debs smartcard support ist disabled in openssh)

This is what I've figured out so far:

SSH_AUTH_SOCK is a socket to the gnome-keyring-daemon not ssh-agent. It was startet by gnome-session and gnome-session is it which overwrites the old values for SSH_AUTH_SOCK (which were provided by ssh-agent)

---

### Post by jjs on 2008-09-11
When I disabled the start of gnome-keyring-daemon (by renameing it, it seems to be hardcoded in gnome-session), then SSH_AUTH_SOCK is set correct and I can use ssh-agent as it should be.

It seems that you can start gnome-keyring-daemon at any time later. And because nautilus doesn't even need the environment variables set by gnome-keyring-daemon (it registers and communicates via dbus), you can use it as usual.

---

### Post by jjs on 2008-09-11
This Link should help to understand the issue (and is a far better way than renameing gnome-keyring-daemon #-o)

[http://live.gnome.org/GnomeKeyring/Ssh](http://live.gnome.org/GnomeKeyring/Ssh)

---

