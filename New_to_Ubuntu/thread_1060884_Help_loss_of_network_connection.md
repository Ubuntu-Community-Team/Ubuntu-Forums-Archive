---
title: "Help loss of network connection"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by jboy012000 on 2009-02-05
Hi All,

I am using Ubuntu 8.10, when I run the latest set of updates I loose all my wireless networks, it's like network manager just packs up and goes home, has anyone else had this problem, has anyone found a fix?

If so can you let me know hot you fixed it.

I have read somewhere that using an older kernel will fix the problem however I don't know how to use an older kernel. Please help.

Thanks very much.

---

### Post by cmnorton on 2009-02-05
I believe Ubuntu's boot cache's away a few versions of the kernel. You have to select from the boot menu.

Is there anything tell-tale in your logs?

sudo tail /var/log/syslog
sudo tail /var/log/messages

You don't need to post the logs here, but just look to see if there are errors that might explain this.

Do you have a wireless hand-held phone running at the same frequency as your wireless router? I get knocked off off and on at home, because the two devices occasionally hit the same part of the frequency and collide.

---

### Post by jboy012000 on 2009-02-05
It may be possible that it got knocked off because I tried to set up my mobile broadband from my mobile phone whilst still connected to my wireless router.

I did re-install Ubuntu 8.10 but just left it as it is at the moment so I will re-try running all the updates tonight and see what happens.

Thanks for your help.

John

---

### Post by jboy012000 on 2009-02-06
Well don't know what is going on yet another night of messing around to come away clueless, I am very dissapointed that I have had to re install Windows so that I can continue my work, maybe when Ubuntu sorts itself out with all these bugs I will come back.

---

