---
title: "How to disable USB storage"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by Guruprasad on 2011-07-30
I am using Ubuntu 10.10.

How to disable USB storage and continue to use USB mouse and other devices?

---

### Post by haqking on 2011-07-30
> **Guruprasad said:**
> I am using Ubuntu 10.10.

How to disable USB storage and continue to use USB mouse and other devices?


you mean for USB stroage devices that are already attached ?

then eject them ?

or do you mean you want to prevent USB storage devices from being attached and mounted ?

in which case you can do that with priveleges of the account.

---

### Post by Guruprasad on 2011-07-30
I want to prevent USB storage devices from being attached and mounted.

I removed it from priveleges of the account but still it mounts.

---

### Post by haqking on 2011-07-30
> **Guruprasad said:**
> I want to prevent USB storage devices from being attached and mounted.

I removed it from priveleges of the account but still it mounts.

is it your account or another account ?

if it is your account did you log out and back in after changing the priveleges ?

also if you are a adm user then that might change things.

try it on a more restrictive account ?

---

### Post by Guruprasad on 2011-07-30
I have created another account. It is not admin user.

---

### Post by haqking on 2011-07-30
> **Guruprasad said:**
> I have created another account. It is not admin user.

ok then well you probably want to diable automount.

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by Guruprasad on 2011-07-30
I tried the gconf-editor option already... still the usb drive is mounting...

---

### Post by haqking on 2011-07-30
> **Guruprasad said:**
> I tried the gconf-editor option already... still the usb drive is mounting...

so you set the key to false for automount ?

---

### Post by Guruprasad on 2011-07-30
I removed the tick mark for media_automout and media_automount_open.

---

### Post by Guruprasad on 2011-07-30
Haqking... Sorry to trouble you... The problem got solved. Dont know where I went wrong but the USB drive is not detecting now...

---

