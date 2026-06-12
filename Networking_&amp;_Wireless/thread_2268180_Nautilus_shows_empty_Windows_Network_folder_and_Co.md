---
title: "Nautilus shows empty Windows Network folder and Connect to Server problem"
date: 2015-03-06
forum: Networking &amp; Wireless
---

### Post by oldefoxx on 2015-03-06
Under Nautilus/Network, see nothing but empty Windows Network folder, and if I try to connect to a server, I get a little X-box at the rnd of the Server Address entry line if I try to type anything in it.  It lists Network Network:/// as a recent server, but if I click on that, it also gets rejected with the X-box signature.  It Seems so basic an idea that you should recognize other pcs that are physically attached to the same network, and I've found no posts about not seeing anything.  So what is likely wrong here?

---

### Post by DennisFolsom on 2015-03-08
I'm trying to solve a similar problem.  I'll check back to this thread if I get mine solved.

---

### Post by DennisFolsom on 2015-03-08
oldefoxx -

I probably have a few tweaks left to do, but I now have my Ubuntu 14.04 machine sharing files to my wife's Windows 7 laptop and to my Windows XP setup on my older dual-boot machine.  Here are some resources that helped me get mine sorted out.  I followed the procedures in each of these, in the order listed:

[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)
[http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7](http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7)

Actually, I had looked at several other websites as well, but chose these as being the most applicable to my case.  Getting everything on the same workgroup is one of the keys.

I also am having partial success in browsing the shares from my Android tablet.  I have more trouble-shooting to do there.

Good luck in getting your sharing sorted out.

---

### Post by DennisFolsom on 2015-03-08
I can't replicate what happened with the Android Tablet, but it seems to be working OK with the Samba shares now.  Apparently, the things I did to get the PC access sorted out also worked for the Android.

---

