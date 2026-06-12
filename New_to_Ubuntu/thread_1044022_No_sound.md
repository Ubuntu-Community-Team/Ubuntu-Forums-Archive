---
title: "No sound"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by FiskFisk33 on 2009-01-19
when i click the speaker icon it says 

'No volume control GStreamer plugins and/or devices found.'

and i dont know where to start.


i am running ubuntu server 8.10 on which i installed ubuntu-desktop

it worked without tweaking when i installed 8.10 desktop earlier.

---

### Post by gettinoriginal on 2009-01-19
Try this:  :P

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by FiskFisk33 on 2009-01-19
interesting

when i let X start up at boot the sound works like a charm.

when i dont, and run it with startx the sound wont work


the document you link doesnt help me, nothing made any difference.


any ideas?

---

### Post by linux_tech on 2009-01-19
so sound does work when you do a normal boot?

---

### Post by FiskFisk33 on 2009-01-19
yes when i add the gdm things so it boots into the desktop it works like a charm yes

but when i remove the gdm and boot into terminal, and run desktop with startx the sound wont work

---

### Post by FiskFisk33 on 2009-01-19
okay, update:

Now i log in as root in terminal when i start X, now the sound works.

should this be filed as a bug?

---

### Post by FiskFisk33 on 2009-01-20
it wont accept root :(

i used proftpd btw

is there a way to make it accept the root user?

---

