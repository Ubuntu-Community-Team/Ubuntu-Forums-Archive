---
title: "Networking with UBUNTU/KUBUNTU Nightmare"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by Sigra on 2008-08-14
I love ubuntu. but when it comes to networking. It just fails. I have tried network tons of my unbuntu computers and it is a nightmare to say the lease.  In fedora networking is all in one spot and straightforward simple.

I have samba nfs and everthing under the roof installed on all systems..if i right click a folder and go share tab and click share..NOPE not happening...if i setup samba or nfs...Nadda...and if does..its periodically.  

Does anyone know stable 3rd party networking for home networking that works flawless and simple that i can run on ubuntu? or Kubuntu

also not 4.1 kde...networking is hit or miss.  either files not found..or errors.

---

### Post by wilbbe01 on 2008-08-14
I have no problems with ssh/scp/sftp or samba.  It seems weird you are having hit and miss issues.  I know samba has been crappier lately than it was previously.  I can't think of anything more simple or flawless than scp.  Samba configuration can also be a nuisance if you don't do it exactly right, you might try using the web configuration for that.  I'm not sure if that is installed with samba or not, but it is called SWAT and it is a web interface.  It is very easy using the web interface.  Does any of that help guide you?

---

### Post by Sigra on 2008-08-14
> **wilbbe01 said:**
> I have no problems with ssh/scp/sftp or samba.  It seems weird you are having hit and miss issues.  I know samba has been crappier lately than it was previously.  I can't think of anything more simple or flawless than scp.  Samba configuration can also be a nuisance if you don't do it exactly right, you might try using the web configuration for that.  I'm not sure if that is installed with samba or not, but it is called SWAT and it is a web interface.  It is very easy using the web interface.  Does any of that help guide you?

I will try.  anytime I have got networking to work on ubuntu or kubuntu it has taken hours or days.  I know about swat. I will give it a try as well.  Lasttime I just went back to fedora.  But overall ubuntu is way better for me then fedora. Only issue I have with ubuntu is networking. and down at office and friends..we all have hard time getting 2 ubuntu boxes network or ubuntu to xp.

---

### Post by wilbbe01 on 2008-08-14
I loved Fedora until 9 came out.  I was so pumped up for it, then it was a very sad release.  Red Hat 9 was crap in the day too, must just be an unlucky number.  Anyway, another thing of advice for SWAT, it sometimes does not change what you tell it to (or at least it seems to do weird things at times).  I would look in the samba config file after using swat to make sure it looks right.  Winscp works nicely for windows machines accessing your linux machines' files via, I don't know if you know about that or not, but I use it heavily to get stuff back and forth from the home to work and it works great.  At home samba is usually the thing in charge.  I would recommend samba on the local network and sftp/scp/ssh for off site stuff.  I know you said home network, but it's always nice to have access away from your home as well.  Good luck.

---

