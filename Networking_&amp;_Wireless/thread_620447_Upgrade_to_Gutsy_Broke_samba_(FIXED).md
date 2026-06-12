---
title: "Upgrade to Gutsy Broke samba (FIXED)"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by ebutton on 2007-11-22
First, a warm holiday "Hello!" to my Ubuntu family.

My upgrade from Feisty to Gutsy caused my Windows XP machines to lose access to my networked data storage drives on my Ubuntu machine.

I got so very very many hits with a Search of these forums for samba problems!  I was bewildered, so I decided to take a very conservative approach.  I read many of the threads and ignored most of the advice (respectfully).  I noticed, however, several references to "smbpasswd -a smbuser".

Deciding that an attempt to reset the smbusers passwords would be the least intrusive thing that I could try, I did so and then restarted samba.  It worked!

Just these two commands:
sudo smbpasswd -a <smbusername> (as shown in the file /etc/samba/smbusers)
sudo /etc/init.d/samba restart

I apologize if this is extremely redundant information for some of you, but I wanted to get this simple fix information at the top of a forum Search with the "FIXED" key word.

Warm Regards,
Ed Button

---

