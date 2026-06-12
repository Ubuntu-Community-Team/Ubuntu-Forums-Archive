---
title: "deleting user-directory"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by lemured on 2011-07-08
ubuntu karmic

hello.

again a question to which the answer is probably too close to grasp...

i had a 2nd user, who now shan't have any access any longer.
i went to admin --> users & groups and deleted this user

unfortunately when trying to delete the directory [filesystem --> home --> username] i found that i wasn't able, as i'm not authorized to read it. i don't want to read, just delete.
to my overrated logic this means that i probably should have erased the directory before deleting the user.

anything i can do to convince the little orange workers in there to let me delete those directories?

thanks a lot and very much if anyone can tell me :)

---

### Post by TeoBigusGeekus on 2011-07-08
Tru from command line
```
sudo rm -rf /home/username
```

---

### Post by lemured on 2011-07-08
> **TeoBigusGeekus said:**
> Tru from command line
```
sudo rm -rf /home/username
```

thanks, TeoBigusGeekus, but either my wits already end before 
my nose or i'm not on the absolute beginner talk any more?

threw this in, the result being a few lines of the -

' usage: sudo -1[1] [-AhS] [- g groupname.....'

- sort, which i don't at all know what to do with. an effect did it not have, so what am i missing?

[i did replace 'username' with the username ;)]

---

### Post by TeoBigusGeekus on 2011-07-08
Can you please post the exact command you used?

---

### Post by lemured on 2011-07-08
> **TeoBigusGeekus said:**
> Can you please post the exact command you used?


'sudo rm -rf /home/username '
as you suggested, the 'username' replaced by the deleted user's username.

i hope i don't appear too stupid...

---

### Post by TeoBigusGeekus on 2011-07-08
The only thing I can suggest is booting from a live cd/usb and deleting it from there.
It could be a permissions thing...

---

### Post by lemured on 2011-07-08
> **TeoBigusGeekus said:**
> The only thing I can suggest is booting from a live cd/usb and deleting it from there.
It could be a permissions thing...

yes. it is. a permissions thing. which it states when i try. unfortunately the usb-idea won't result either.
but thank's in any case for your help :)

---

### Post by TeoBigusGeekus on 2011-07-08
> **lemured said:**
> unfortunately the usb-idea won't result either.

Why not?

---

### Post by wojox on 2011-07-08
```
sudo userdel -rf username
```

---

### Post by grahammechanical on 2011-07-08
Go back to Users and Groups and this time check that sudo is listed as one of the Groups available on the system. It is under Manage Groups.

This is just a crazy though that I have had.

Regards.

---

### Post by wildmanne39 on 2011-07-08
> **lemured said:**
> 'sudo rm -rf /home/username '
as you suggested, the 'username' replaced by the deleted user's username.

i hope i don't appear too stupid...
Hi, it looks like to me that /home needs to have a space between it and rf. Also please note that you need to be very careful using this command if used wrong you could delete your system.

---

### Post by westie457 on 2011-07-08
Hi another way is in a terminal running ```
gksudo nautilus
```
This will open nautilus with root privileges.

_[COLOR="Red"]WARNING[/COLOR]_ Be very careful on what you delete here as there is no recovery option if you choose the wrong file. Also there is a security risk as your system is wide open, as soon as you have finished exit the terminal, log off and back in again to minimise any chance of interference from outside. If you are feeling paranoid about this the best thing to do then is shutdown and then restart not a plain reboot.

---

### Post by jerome1232 on 2011-07-08
> **westie457 said:**
> Hi another way is in a terminal running ```
gksudo nautilus
```
This will open nautilus with root privileges.

_[COLOR="Red"]WARNING[/COLOR]_ Be very careful on what you delete here as there is no recovery option if you choose the wrong file. Also there is a security risk as your system is wide open, as soon as you have finished exit the terminal, log off and back in again to minimise any chance of interference from outside. If you are feeling paranoid about this the best thing to do then is shutdown and then restart not a plain reboot.

If you use this method, be sure to shift+del, otherwise it goes to your root users trash and hogs space secretly.

---

### Post by bodhi.zazen on 2011-07-08
I suggest you use find, you will need to run it as root.

```
sudo -i

find / -user old_user
```

After reviewing those files, remove them with find again

```
find / -user old_user -exec rm -f '{}' \;
```

See man find for details ;)

---

### Post by lemured on 2011-07-13
> **grahammechanical said:**
> Go back to Users and Groups and this time check that sudo is listed as one of the Groups available on the system. It is under Manage Groups.

This is just a crazy though that I have had.

Regards.

Hello.
Yes, it is. 
How to proceed from there?

---

### Post by lemured on 2011-07-13
> **westie457 said:**
> Hi another way is in a terminal running ```
gksudo nautilus
```
This will open nautilus with root privileges.

_[COLOR="Red"]WARNING[/COLOR]_ Be very careful on what you delete here as there is no recovery option if you choose the wrong file. Also there is a security risk as your system is wide open, as soon as you have finished exit the terminal, log off and back in again to minimise any chance of interference from outside. If you are feeling paranoid about this the best thing to do then is shutdown and then restart not a plain reboot.

Hi
thank you, also jerome1232

i'll try later and let you know how it went

---

