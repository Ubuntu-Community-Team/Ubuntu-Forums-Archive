---
title: "NetworkManager help"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Old Jimma on 2008-12-30
Hi Ubuntu Community:

I wanted to have static ip addresses on my computers so I looked on the web for advice. 

I found some at: [http://www.php-architect.com/blog/2008/11/04/ubuntu-810-interpid-fix-static-ip-network-manager-problem/]("http://www.php-architect.com/blog/2008/11/04/ubuntu-810-interpid-fix-static-ip-network-manager-problem/")

Also, I searched the forums and the advice there looked pretty similar so I proceeded with the advice provided by the URL above.

The first step was to remove NetworkManager using

sudo update-rc.d -f NetworkManager remove

After going adding all of the recommended code, I found that NetworkManager no longer worked and none of my machines have access to the internet!

!%@#!!

Can someone please tell me how to restore NetworkManager?? 

I don't think that I have internet access anymore because it was removed.

Thanks,
Phil Smith
Duluth, GA

---

### Post by adult swim on 2008-12-30
try from a terminal ```
sudo /etc/init.d/networking restart
``` and then press alt+f2 and enter in ```
nm-applet
```

---

### Post by Old Jimma on 2009-01-01
Hi:

Thanks for your suggestion. It did not work, however. I reloaded 8.10.

Phil Smith
Duluth, GA

---

### Post by zika on 2009-01-01
_[http://ubuntuforums.org/showpost.php?p=6461701&postcount=5](http://ubuntuforums.org/showpost.php?p=6461701&postcount=5)_

---

### Post by gn2 on 2009-01-01
Or just use [Wicd]("http://wicd.sourceforge.net/") instead.

---

### Post by superprash2003 on 2009-01-01
> however. I reloaded 8.10.
does this mean that your problem is solved now?? if so please mark this thread as SOLVED under thread tools

---

