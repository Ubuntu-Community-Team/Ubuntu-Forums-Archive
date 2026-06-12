---
title: "Connecting Linux to a Windows Network?"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by tomplast on 2007-03-13
Hello everyone.

I have this little problem that at my work (which is also my previous gymnasium (sort of High School I guess) ) I have this Xubuntu Linux machine that I want to be able to access my home catalog (and other shares on the network).

I have used pyNeighborhood to help me mount my home catalog (and other shares) from the server without a problem, though I would like to automatically do it (I know about /etc/fstab). So with /etc/fstab I think I could make it a little bit automatic but how am I supposed to send my username and password for the connection to succeed?

And finally, there is a chance that I won't be the only one who uses this computer. Therefore it would be nice if the right home catalog from the server was mounted just after the user had logged in.  So the user Eric should get his home catalog, and Helena should get hers. And I wan't XDM to be able to only let users existing in the domain to be able to login (I don't want to manually add each user who is going to be able to login to that computer).


So help here is greatly appreciated. If this succeeds then maybe my school will see more of Linux in the future.


Thank you.

/Tomas Gustavsson

---

### Post by tomplast on 2007-03-13
This is quite important so if you could help me I would be very grateful.

Please help me. This is of most importance for me (and others).

---

### Post by tomplast on 2007-03-14
*bump*

---

### Post by daengbo on 2007-03-14
Well, there's not a really good solution for this using Xubuntu, because XFCE doesn't have a network browser (one's due soon, though, I hear).

In your fstab, you'll use a line like:

//192.168.0.3/Photos   /media/Photos   cifs   uid=1000,,credentials=/home/chiraporn/.smbcreds    0       0

where "chiraporn" is replaced by your username. Then, create the file /home/USERNAME/.smbcreds with this content:

username=USERNAME
password=PASSWORD

Of course, this doesn't solve your problem of multiple users. For that, you'll probably need to use Gnome (Ubuntu), which has user-mountable shares.

Good luck!

---

### Post by tomplast on 2007-03-14
> **daengbo said:**
> Well, there's not a really good solution for this using Xubuntu, because XFCE doesn't have a network browser (one's due soon, though, I hear).

In your fstab, you'll use a line like:

//192.168.0.3/Photos   /media/Photos   cifs   uid=1000,,credentials=/home/chiraporn/.smbcreds    0       0

where "chiraporn" is replaced by your username. Then, create the file /home/USERNAME/.smbcreds with this content:

username=USERNAME
password=PASSWORD

Of course, this doesn't solve your problem of multiple users. For that, you'll probably need to use Gnome (Ubuntu), which has user-mountable shares.

Good luck!

I have heard something about something called pam (related to the login I believe), is that something that I could have use for?

---

