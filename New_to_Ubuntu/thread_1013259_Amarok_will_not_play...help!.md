---
title: "Amarok will not play...help!"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by Granny_Geek on 2008-12-16
The title says it all. Amarok says that it cannot read the disk but other media players can, so I am stumped. Please help. Granny

---

### Post by mc4man on 2008-12-16
> Amarok says that it cannot read the disk

What kind of disk? (audio cd or something else

Amarok defaults to /dev/cdrom for a device, run this to ck.
```

sudo lshw -C disk
```

---

### Post by Granny_Geek on 2008-12-17
Thanks for your reply mc4man:p Not sure if I am sending this reply in the right order because I am new here but anyway, yes it is the audio cd and I need to know if I do that check will it make my other players unresponsive because I don't want that to happen. Bare with me because Linux is pure greek to me, I am learning by trial and error and the likes of others that have the knowledge. Granny

---

### Post by mc4man on 2008-12-17
> if I do that check will it make my other players unresponsive

No, it's just a means to display information about your install and or hardware.
Many times solutions can be found in the terminal output.

---

