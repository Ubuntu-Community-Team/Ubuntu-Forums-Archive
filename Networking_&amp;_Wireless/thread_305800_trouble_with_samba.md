---
title: "trouble with samba"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by JoeC21 on 2006-11-23
I am having some trouble on my network with samba.  I have a windows xp machine, mepis 6.0, and an ubuntu computer all connected.  From my ubuntu computer I am unable to transfer files to either the mepis comptuer or the windows computer.  I get a message saying "Error, Access Denied while copying /home/joe/picture.png"  I am able to copy files from those computers though to my ubuntu computer.

What do I need to change so I can move files from ubuntu to the other computers?  I should point out that I have no problems copying files to and from between the mepis and windows xp machine

Thanks,

Joe

---

### Post by dmizer on 2006-11-24
try mounting your share with cifs (sambas smbfs replacement) instead of using nautilus.  it's a far superior method of mounting samba/windows network shares.  you can use the howto posted in my sig for cifs.

---

### Post by JoeC21 on 2006-11-24
Ok, I will give that a shot.  Also, not sure if this changes anything but I guess I will mention it.

As in my initial post, I am unable to move files from ubuntu to mepis/windows from ubuntu.  I can however access the ubuntu files from either of the other computers and copy them from ubuntu to the mepis/windows computer like that. (Hopefully that makes sense)

Is using cifs still the best way to go?

Thanks again,
Joe

---

### Post by dmizer on 2006-11-25
yes cifs is the way to go.

samba server allows other computers to connect to your ubuntu box (configuring smb.conf for example)

cifs will allow your ubuntu box to connect to other computers in a windows based network.

---

