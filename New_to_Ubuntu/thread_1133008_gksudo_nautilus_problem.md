---
title: "gksudo nautilus problem"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by dan1973 on 2009-04-22
Good evening all,

Could anyone out there help with this current brain-teaser?

When I load up 'gksudo nautilus' from the terminal i receive the following print out:

```
seahorse nautilus module initializedInitializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:10603): WARNING **: Unable to add monitor: Operation not supported

** (nautilus:10603): WARNING **: Unable to add monitor: Operation not supported
```

Nautilus does then open, however when I shut it down again, the following appears in terminal:

```
--- Hash table keys for warning below:
--> file:///root

(nautilus:10603): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:10603): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
Shutting down nautilus-share extension
seahorse nautilus module shutdown

```

What might be the cause and how may I correct it?

Thank you in advance,

---

### Post by LowSky on 2009-04-22
is it effecting your ability to use nautilus?
If no then dont worry about it, I get the same error.

BTW BE CAREFUL USING ROOT ACCESS IN NAUTILUS
Remember if you break you get to keep both pieces!

---

### Post by dan1973 on 2009-04-22
Doesn't seem to be having much effect, but would like to get to the bottom of the problem - i love a good mystery!

---

### Post by lovelyvik293 on 2009-04-22
@LowSky
please explain the error message if you get it.

---

### Post by brunogirin on 2009-04-22
I observe the same messages and, having apport enabled, it tells me that it crashes when closing.

Also note that, as identified in the logs, the directory /var/lib/samba/usershares doesn't exist on my system. It may be that Nautilus does something extra when started as root that makes it crash. Or it may be that it expects to find something in the user's home directory (in this case /root) that it can't find when run as root?

It's worth investigating anyway because something that crashes when you run it with root privileges is generally not good.

---

### Post by gn2 on 2009-04-22
Rather than run from a terminal, have you tried Alt+F2 then gksudo nautilus?

---

### Post by dan1973 on 2009-04-22
Seems to work fine with the alt-F2, however, get the feeling that underneath the same error messages may be present?

Thanks for the nice shortcut though.

---

### Post by dan1973 on 2009-04-22
I think i have found a working solution - well disposes of the error message:

1) Locate the samba configuration file and edit:

   sudo gedit /etc/samba/smb.conf

2) Find the [Global] section and add the following line of code below [global] heading:


usershare owner only = false

3) Save and exit

4) Try gksudo nautilus

Hope this works for you chaps out there as well as it seems to do for me.

---

### Post by dan1973 on 2009-04-22
Ignore above 'solution' bug is persistent on reebooting - sorry!

---

### Post by dan1973 on 2009-04-22
Can someone find a way round this.?

---

### Post by gn2 on 2009-04-22
Are you experiencing any loss of functionality or problem with Nautilus?

If you had only ever run gksudo nautilus from Alt+F2 you would never have seen the error messages in the first place.

Alt+F2 for GUI apps, terminal for CLI apps. Simples.
Out of curiosity, I just ran gksudo from terminal for the first time since I started using Ubuntu three years ago and for the first time on this laptop which has had Ubuntu 8.04 on it since it was released.
I got a similar error message.
But I know for a fact that Nautilus works fine, because it has done so for the last year.
I will be ignoring the error message.....

---

### Post by dan1973 on 2009-04-23
Your absolutely right, i should stop fussing over this 'problem', I guess that's the problem with being an obsessive!

---

