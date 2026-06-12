---
title: "Another boot/grub/something issue."
date: 2010-02-28
forum: New to Ubuntu
---

### Post by lockalidiot on 2010-02-28
Hi again.

On the agenda today we have my girlfriends netbook with Ubuntu 9.10 Karmic (not the netbook-remix). It successfully boots on the average every other time. On those times it won't boot it just flashes the little white line in the upper left corner against black screen. Is there any fix for this?

Thanks once again.

---

### Post by lockalidiot on 2010-02-28
Kicking UP! :P

---

### Post by ububiginner on 2010-02-28
Hi I put ubuntu 9.10 netbook remix on my acer aspire one and I have the same problem, only difference is that this happens every time!!! I have not been able to boot ubuntu since its installation.  I have re-installed many times; I have re-created bootable USB using the universal usb installer many times.  I can boot ubuntu using the USB.   I appreciate some help.  Thanks

---

### Post by lockalidiot on 2010-03-01
This machine is a HP netbook, not sure which model... Does anyone know any solution to this? Reinstall GRUB?

---

### Post by undecim on 2010-03-01
When grub is loading (just after you see your BIOS manufacturer's logo), hold down shift and you get the grub menu.

Choose your first Ubuntu option and press "e" to edit it. On the line that starts "linux" remove "quiet splash" from the end, and press Ctrl+X to boot.

Now when you are booting, you should be given messages that can help diagnose the problem. If your system hangs, post any interesting messages here. (Or a picture helps, if it's quicker and easier to use your digital/cellphone camera that to type it all).

---

### Post by anaconda on 2010-03-01
9.10 has a beta version of grub2, and it doesnt work in every machine.. (ok, well. 99% of machines it works, but....)

I also have a machine that grub2 doesnt boot so well...

Luckily you can install older grub, or use [http://www.supergrubdisk.org/superboot](http://www.supergrubdisk.org/superboot)

---

### Post by philinux on 2010-03-01
> **lockalidiot said:**
> Hi again.

On the agenda today we have my girlfriends netbook with Ubuntu 9.10 Karmic (not the netbook-remix). It successfully boots on the average every other time. On those times it won't boot it just flashes the little white line in the upper left corner against black screen. Is there any fix for this?

Thanks once again.

I would also advise checking the disk status. System>admin>disk utility.

Click the [COLOR="Blue"]_more information_[/COLOR] link.

---

### Post by lockalidiot on 2010-03-01
Thank you for the input. I will do this as soon as I can and report(?) back.

---

### Post by lockalidiot on 2010-03-02
Ok, I finally have the mini before me. Disk seems to be healthy. So it's not a HD issue. Any further suggestions?

EDIT: Ok, I have removed the "quiet splash". no Errors to report so far. three boots successful in a row. That is weird.

---

### Post by lockalidiot on 2010-03-02
bumbs!

---

### Post by lockalidiot on 2010-04-10
The issue is still around...

---

### Post by undecim on 2010-04-10
> **lockalidiot said:**
> Ok, I finally have the mini before me. Disk seems to be healthy. So it's not a HD issue. Any further suggestions?

EDIT: Ok, I have removed the "quiet splash". no Errors to report so far. three boots successful in a row. That is weird.

Perhaps it's just usplash causing the problems?

Try removing the "quite splash" options from /etc/default/grub and then go to a terminal and run "sudo update-grub"

---

### Post by lockalidiot on 2010-04-12
> **undecim said:**
> Perhaps it's just usplash causing the problems?

Try removing the "quite splash" options from /etc/default/grub and then go to a terminal and run "sudo update-grub"

As you can see from the part you quoted, that's done already...:)

---

### Post by undecim on 2010-04-12
> **lockalidiot said:**
> As you can see from the part you quoted, that's done already...:)

Ah. I misunderstood.

Well, if it boots fine without the splash option, looks like that's about all you can do.

---

### Post by j4k3y34g3r on 2010-04-15
Hey yall, got the same issue with my Acer One d250. Wubi worked like a champ while i had XP on it. Had issues with bootable USB sticks holding me to this point. Finally got an old CD copy K 9.10 to stick through an install. After updating the packages i get to this point [deleting the 'quite splash' option in the GRUB parameters].

Sounds like a Grub issue and will pursue suggestions made above about changing/updating.

Am including a pic and would love more input:



Thank you

---

### Post by j4k3y34g3r on 2010-04-15
Never mind... Gave it a hard look and it booted just fine.

---

### Post by lockalidiot on 2010-04-28
Well, actually my original issue is back on the table. Still freezes in mid boot.

---

### Post by lockalidiot on 2010-04-29
bumb

---

### Post by cuberts on 2010-04-29
> **lockalidiot said:**
> Hi again.

On the agenda today we have my girlfriends netbook with Ubuntu 9.10 Karmic (not the netbook-remix). It successfully boots on the average every other time. On those times it won't boot it just flashes the little white line in the upper left corner against black screen. Is there any fix for this?

Thanks once again.Are you sure that the netbook actually holds the whole operating system? And it might be that youre netbook is overloaded of memory.

---

### Post by lockalidiot on 2010-04-29
Thank you for your response!

For the first question, yes, the netbook holds the whole OS. After the issue was first noticed I did a new clean install. When it resumed I burned a new Live-CD and did a clean install again. Still no go.
For the second part, what exactly you mean with "overloaded of memory"?

---

### Post by lockalidiot on 2010-05-14
Bump!

---

