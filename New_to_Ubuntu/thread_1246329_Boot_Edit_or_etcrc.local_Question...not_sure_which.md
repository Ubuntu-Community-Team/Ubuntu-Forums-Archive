---
title: "Boot Edit or /etc/rc.local Question...not sure which..."
date: 2009-08-21
forum: New to Ubuntu
---

### Post by Wataru8675 on 2009-08-21
I'm trying to install and set up the Cisco VPN client so I can access the internet from my college campus, but I've run into a question.

Thankfully, they have a handy how-to guide to install/set-up vpnc on the school website ([found here]("http://dragon.mnstate.edu/vpnc/")).  I'm to step 4, and I'm not sure what I need to do...  I Google searched and forum searched "boot edit" and found its primary use is for dual booting, so I can't figure out how to use it in this scenario.

Also, I tried searching for my /etc/rc.local file manually, but I don't see anything like it...  I have rc0.d through rc6.d and rcS.d, but I see no rc.local...unless it's somewhere in one of those folders (but they all look like executable programs).

Maybe I'm just missign something...but any help would be grand.  Thanks in advance!

---

### Post by enli on 2009-08-21
I am hoping that you want to enter that command "/usr/local/vpnc &" into /etc/rc.local. Type in terminal

```

sudo su
echo '/usr/local/vpnc &' >> /etc/rc.local
echo 'exit 0' >> /etc/rc.local
chmod +x /etc/rc.local
exit

```

---

### Post by Wataru8675 on 2009-08-21
So then...is that all that needs to be done?  Is there a way that I can check that all these settings are correct?  If I type ```
sudo vpnc
``` it directs me to input all the information that I've already done...

---

