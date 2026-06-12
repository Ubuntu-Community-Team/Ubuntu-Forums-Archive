---
title: "Everything has gone bad... need remote desktop help"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by Scrufdog on 2008-02-28
Here we go...

I have a dual boot XP/Ubuntu computer. I had grub set up to default boot XP, since I travel alot and generally use XP at home, through VNC on my laptop.

Before the last time I left I flipped over to Ubuntu and upgraded to 7.10. I didnt even think about the fact that it adds lines into grub so you can still boot the old kernel. So now instead of booting into XP, which I need, it booted into Ubuntu when there was a power outage last week.

So now I need to ask some questions.

Are any remote desktop apps default 'turned on'? If so, do I log in with my user/pw, or with whatever the root account is? If its root, what is the root account? I havent logged into it in so damn long I dont remember. I know I need to be in it to edit grub though.

Thanks

---

### Post by HermanAB on 2008-02-29
No, Ubuntu is the only distribution that doesn't install the SSH daemon by default.  If you haven't installed SSH server manually yourself, then you are out of luck.

The Ubuntu team deserves seven lashes with a wet noodle for this stupidity.

Cheers,

Herman

---

