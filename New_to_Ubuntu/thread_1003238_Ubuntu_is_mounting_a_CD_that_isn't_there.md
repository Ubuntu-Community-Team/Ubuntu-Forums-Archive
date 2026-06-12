---
title: "Ubuntu is mounting a CD that isn't there"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by dannytatom on 2008-12-05
First off, my CD drive is broke, has been for a while.  But for some reason, starting about 2 hours ago, it's showing that there's a CD in there.  I was shocked, thinking maybe my CD drive started working, but there was no CD in it.

The file contents are:
Autorun.inf
Launchpad.zip
LaunchU3.exe

When I try to unmount it, I get:

> 
**Unable to mount cdrom1**
mount: No media found


---

### Post by taurus on 2008-12-05
What's the output of this command from a terminal?

```
df -h
```

---

### Post by dannytatom on 2008-12-05
Well son of a gun, as soon as I post this it disappears.

---

### Post by bwang on 2008-12-06
U3 makes USB Flash drives behave like a CD drive. Did you have a flash drive plugged in?

---

### Post by dannytatom on 2008-12-06
I did, but the files listed weren't on there.  It's just a Ubuntu install and a couple movies.  ;o

What is U3?

---

### Post by adobrakic on 2008-12-06
Yeah, that's showing your flash drive. I have a U3 USB flash drive, which contains the stuff you listed.

U3 explained:
[http://www.youtube.com/watch?v=fnRIlv8-z9o](http://www.youtube.com/watch?v=fnRIlv8-z9o)

Basically allows you to run software off of your flash drive.

---

### Post by ash_nug on 2008-12-06
> **dannytatom said:**
> I did, but the files listed weren't on there.  It's just a Ubuntu install and a couple movies.  ;o

What is U3?

[http://www.tomshardware.com/forum/243608-32-remove-smart-software-sandisk-flash-drive](http://www.tomshardware.com/forum/243608-32-remove-smart-software-sandisk-flash-drive)

---

### Post by dannytatom on 2008-12-06
Ah, I just bought this thing and had no idea.  

While this thread is open, I had another (unrelated) question.  I used Ubuntu's built-in USB creator to install ubuntu on it so I could reinstall it on my laptop.  If I'm running it from the USB, and I save files, does it save to the USB stick?

I'm thinking I read that it does, but can't seem to find out for sure. ;o

**Edit:** Thanks for the link, ash_nug, I was just about to look that up.

---

### Post by adobrakic on 2008-12-06
> **dannytatom said:**
> Ah, I just bought this thing and had no idea.  

While this thread is open, I had another (unrelated) question.  I used Ubuntu's built-in USB creator to install ubuntu on it so I could reinstall it on my laptop.  If I'm running it from the USB, and I save files, does it save to the USB stick?


I'd imagine so.
I think this is what most people who install it on the USB for do that. I can't imagine why it wouldn't save the files, but I'm not completely sure.

---

