---
title: "[SOLVED] Problem with Samba/Cifs from 8.06 to 8.10"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by Steve Ubu on 2008-11-04
Hi

I have a little problem with the new 8.10. All worked fine from 8.06, but my local network doesn't work best.
I have a Feisty server, running with Samba because my wife works with Win. Since yesterday all was ok, I had two folders where I've mounted via fstab the condivisions with Cifs.
Now I can't save with Gedit or OO, but I can with Gimp.
What's the matter?

Thanks
Stefano

Ps: I think it's a matter of kernel: if I use the "old" of 8.06 it all works

---

### Post by Leolik on 2008-11-04
> **Steve Ubu said:**
> Hi

I have a little problem with the new 8.10. All worked fine from 8.06, but my local network doesn't work best.
I have a Feisty server, running with Samba because my wife works with Win. Since yesterday all was ok, I had two folders where I've mounted via fstab the condivisions with Cifs.
Now I can't save with Gedit or OO, but I can with Gimp.
What's the matter?

Thanks
Stefano

Ps: I think it's a matter of kernel: if I use the "old" of 8.06 it all works

I reproduce that bug. How fix that bug?

---

### Post by Steve Ubu on 2008-11-06
Yesterday there was an upgrade also for the kernel. I hoped the problem was solved, but it wasn't.
I can't save only with Gedit and OpenOffice, other programs work right, like Gimp.

Stefano

---

### Post by Steve Ubu on 2008-11-07
I was able to made all work with kernel 2.6.27.7 adding the parameter "nounix" (I'm using a Samba server with Feisty, but my Intrepid client "thinks" it's a win one...) in my fstab. Beware: you must restart all to take effect, if you just try "mount -a" it doesn't work.

Now the "mount" command says:
//192.168.1.1/DocumentiRete on /home/steve/Scrivania/Rete type cifs (rw)

and not:

//192.168.1.1/DocumentiRete on /home/steve/Scrivania/Rete type cifs (rw, mand)

as it was before.

And all works, both with OO and Gedit

Stefano

---

### Post by punknroll on 2008-11-18
Hi there, could you please post your line from /etc/fstab? Just adding nounix didn't change a thing for me. There is the same problem with eclipse too. 

thanx.

---

