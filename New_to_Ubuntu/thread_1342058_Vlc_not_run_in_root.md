---
title: "Vlc not run in root"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by navaneethan on 2009-11-30
In my ubuntu9.10 I have installed vlc ,so i want to use to play that in root account but it shows 

> root@baskar-laptop:~# vlc
VLC is not supposed to be run as root. Sorry.
If you need to use real-time priorities and/or privileged TCP ports
you can use vlc-wrapper (make sure it is Set-UID root and
cannot be run by non-trusted users first).
root@baskar-laptop:~#                    

I want to know the reason?

---

### Post by doas777 on 2009-11-30
part of it is probably because much of vlc runs out of the user profile, and redirection via gksu/sudo may confuse it.

a video player is a perfect example of somthing you should never need to run as root, so...

have you actually enabled your root account? mabey that would work for what you are trying, but is generally considered a bad idea.

---

### Post by ukripper on 2009-11-30
> **navaneethan said:**
> 
                

I want to know the reason?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mc4man on 2009-11-30
Because "run as root" isn't enabled (nor probably shouldn't

To use see here in terminal
```
man vlc-wrapper
```

---

### Post by NoaHall on 2009-11-30
It's best to run as little things as possible as root. As you should not use a root account for doing anything other than installing/user management.

---

