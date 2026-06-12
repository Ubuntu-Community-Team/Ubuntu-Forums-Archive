---
title: "Hidden Users"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by adamjkok on 2010-08-28
How do I give a friend access to my computer over SSH and local access on the rare occasion that he happens to be at my house without displaying his name on the login screen (in other words, click OTHER to login)?

NOTE: I don't need help with SSH, just with the login screen.

---

### Post by uRock on 2010-08-28
I have recently played with the settings for accounts and I do not think it is possible to not have them listed in the log in menu.

---

### Post by adamjkok on 2010-08-28
> **uRock said:**
> I have recently played with the settings for accounts and I do not think it is possible to not have them listed in the log in menu.
So how are all of the system accounts (including, but not limited to, root) hidden?

Also, in theory, you can make open-source software do anything that the hardware is capable of.

---

### Post by uRock on 2010-08-28
I have tried creating accounts via **Users and Groups** and via the **newuser** command and neither will create a hidden account nor allow you to hide an account. There may be a server application that will allow this, but I haven't looked.

---

### Post by adamjkok on 2010-08-28
> **uRock said:**
> I have tried creating accounts via **Users and Groups** and via the **newuser** command and neither will create a hidden account nor allow you to hide an account. There may be a server application that will allow this, but I haven't looked.
What about **adduser** and **useradd**? Or **usermod**?

---

### Post by jtarin on 2010-08-28
> **adamjkok said:**
> So how are all of the system accounts (including, but not limited to, root) hidden?

Also, in theory, you can make open-source software do anything that the hardware is capable of.What system accounts are you aware of that are hidden?

If you try
```
cat /etc/passwd | cut -d ":" -f1
```
you will get all the names of the users in the system.
This also includes daemons/special accounts.

---

### Post by ibuclaw on 2010-08-28
GDM hides all users who's PID is below the minimal UID value. Which by default is less than 1000.

This can be tweaked in /etc/login.defs


Alternately you can remove the user selection screen altogether.
```
sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/disable_user_list --type bool true
```
As you can probably guess, 'false' reverses it.

You can lookup more settings you can tweak [here]("http://library.gnome.org/admin/gdm/2.30/configuration.html.en#greeterconfiguration").

Regards.

---

### Post by uRock on 2010-08-29
> **adamjkok said:**
> What about **adduser** and **useradd**? Or **usermod**?
Give them a try.

---

### Post by The Cog on 2010-08-29
> **ibuclaw said:**
> GDM hides all users who's PID is below the minimal UID value. Which by default is less than 1000.
Nice one. 
So make his user ID smaller than 1000 when you create his account.

---

### Post by v0idblackb0x on 2011-09-25
```
sudo gedit /etc/gdm/custom.conf
```

Look for the [greeter] section, add if it doesn't exist...

```
[greeter]
Exclude=nobody,USERNAME
```

Obviously replcate username with the user to hide.  Make sure "nobody" is there as well, Ubuntu seems to have a hidden/system user with that name.  Adding only USERNAME will leave nobody visible.

Restart GDM(reboot).

I don't recall the URL but I found the answer somewhere else on the ubuntu forums.

---

