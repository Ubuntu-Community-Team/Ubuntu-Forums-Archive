---
title: "Option &quot;AIGLX&quot; &quot;off&quot; - Ubuntu loads blank page!"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by joey_breizh on 2009-01-14
Hi everyone,

My VLC has been giving me really poor quality video under Ubuntu so I've been trying to fix the problem. I was following instructions on a page on improving video quality for ATI graphic cards, as I have by modifying my xorg.conf. I ended up with much better video quality but a flickering VLC window...

Long story short, I was trying to revert back the changes that the post had made me do to find out which one was creating the flickering.

I got to Option "AIGLX" "on", turned it off, went into the terminal to make the aticonfig validate the change in the xorg.conf, and logged out to log back in...

And now Ubuntu won't load! All I get is a white screen... sometimes it'll show me my wallpaper but then either it stays stuck there or it becomes a white screen.

As I am new to Ubuntu I'm lost as to what to do. I know that aticonfig created backups of my xorg.conf every time I changed it, and I know where I would need to make the change (set the Option "AIGLX" back to the value "on") but I don't know how I can access my terminal if Ubuntu won't load. I tried running the recovery mode but I ended up with the same log-on page as usual and the same problem once I entered my l/p.

Can someone please tell me how I can go about changing that value in my xorg.conf? I'm freaking out a little at not being able to access Ubuntu.

Thank you!

---

