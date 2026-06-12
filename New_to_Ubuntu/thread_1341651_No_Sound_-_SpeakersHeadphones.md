---
title: "No Sound - Speakers/Headphones"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by TwoUpWeb on 2009-11-29
Hello, I'm a new Ubuntu user!

My laptop is an Asus G50vt X-1
There seems to be no sound coming out, whether it's from the speakers or the headphones.

Typing alsamixer in terminal gives me :
alsamixer: function snd_ctl_open failed for default: No such file or directory

There are no things muted in "sound preferences".

**How can I enable sound?**
Thanks in advance!

And regardless of the results, I will still use Ubuntu over Windows any day. ;)

---

### Post by omnipotentperson on 2009-11-29
It sounds like you might not have the correct sound drivers.

---

### Post by TwoUpWeb on 2009-11-30
How can I download the correct drivers? Also, I do not know what my Sound card is..
I'm still new to this terminal stuff. 

Thank you.

---

### Post by TwoUpWeb on 2009-11-30
(bump)

---

### Post by DougieFresh4U on 2009-11-30
Did you install 'alsamixer' and maybe try installing 'gnome alsa mixer' and see if something is muted.

---

### Post by TwoUpWeb on 2009-11-30
alsamixer: function snd_ctl_open failed for default: No such file or directory

I've downloaded alsa-utils and compiled it.
No go.

Synaptics P.M. = Reinstall
Still no go.
----------------------------------------------------------------------------------------------------------------

lspci = 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
-----------------------------------------------------------------------------------------------------------------
On Sound Preferences --> Hardware There's nothing listed.
Output says :  Dummy Output

Getting kind of desperate. Wasted m whole day on this, I might just do a Format then Reinstall, but I'd lose all my files. :S

---

### Post by k()()zmi4 on 2009-11-30
> **TwoUpWeb said:**
> 
Getting kind of desperate. Wasted m whole day on this, I might just do a Format then Reinstall, but I'd lose all my files. :S

[_Here's_]("http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/") a good tip on installing alsa - it helped me;)

---

