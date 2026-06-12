---
title: "ubuntu to vista and xp samba works, as does ubuntu to ubuntu"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by frankelr on 2008-12-23
not a hardware issue can access 8,10 samba shares on vista, ubuntu to ubuntu both directions. But no shared folders on vista to ubuntu.

vista to vista also works for what is worth; any clues to point me in the right direction?

Bob

---

### Post by cmnorton on 2008-12-24
> **frankelr said:**
> not a hardware issue can access 8,10 samba shares on vista, ubuntu to ubuntu both directions. But no shared folders on vista to ubuntu.

vista to vista also works for what is worth; any clues to point me in the right direction?

Bob

Do you mean you cannot mount a samba drive from vista?

Have you run smbpasswd using your mountee's name and made sure the vista domain/user is entered in smbusers?

---

### Post by frankelr on 2008-12-24
Thanks for your response, I mean that shared drives on my vista machines do not appear when network places is selected.  Linux computers appear correctly and xp computers also work

Bob

---

### Post by cmnorton on 2008-12-24
You may need to put your Ubuntu computer in the same domain as the vista machine. smbpasswd involves after being able to see the drives and not being able to click on them and display. 

Here's a link I found:

[http://ubuntuforums.org/showthread.php?t=847709](http://ubuntuforums.org/showthread.php?t=847709)

---

