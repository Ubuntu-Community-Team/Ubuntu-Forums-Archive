---
title: "Wireless not working after last update"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by joatmon on 2008-08-14
Wireless has been working for me quite well for awhile now, but after updates that happened yesterday, it appears my wireless card is not detected.  When I run iwconfig I get the following:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   

```

Does anyone know what might have changed with the latest install?  Is there other information I can provide?  I'm not very well versed in this, so sorry for the lack of info.

Thanks for your help!

---

### Post by mrtomservo on 2008-08-14
I don't know if I can help you, but one thing that might help would be posting the contents of your **/etc/network/interfaces** file.  Also, do you remember what was in the update?  If you updated your kernel or something perhaps the old driver you were using needs to be reinstalled because it doesn't match the kernel.

---

### Post by joatmon on 2008-08-15
I'm not sure what it was before the updates, but here is the contents of my /etc/network/interfaces file:

scott@scott-laptop:/etc/network$ more interfaces
auto lo
iface lo inet loopback

I maybe should note that this is a Dell XPS M1530 with an internal wireless interface.  It has been working very well up until a couple of days ago.  I don't know exactly what was updated (I usually read through the list but for the most part it is all greek to me) but I know it wasn't the kernel if that helps at all.

Thanks for your help!

---

### Post by mrtomservo on 2008-08-15
I was looking around and was going to post a link to another topic that relates to your problem,  but I saw you posted on it already.  :)  Unfortunately since no one else who actually has that laptop can figure it out, I doubt i'll be much help.  But it seems to me that the noapic flag with the kernel might be what you'll have to settle with.  Do you dual boot?
I've heard of windows suspending a nic/wifi card when it shuts down, and sometimes linux can't bring it back up again.  Perhaps this is similar?  Sorry I can't be of more assistance!

---

### Post by un_polle on 2008-08-15
ho un problema simile!
appena installato ubuntu il wireless mi funzionava...ora non funziona + e non so perchè....
mi sto scervellando...

---

