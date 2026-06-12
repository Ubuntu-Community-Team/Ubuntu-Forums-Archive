---
title: "synaptic touchpad driver compatibility under wine?"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by 11010110 on 2008-12-19
I have recently been posting about my troubles configuring the virtual buttons tap zones on my synaptic touchpad that came with my Toshiba laptop. I have just found the actual driver that came with my windows for download. My question is would this possibly work thru wine or would i be wasting my time? also if installed thru wine would it possibly mess up my computer?

Thanks alot in advance everyone!

---

### Post by Kareeser on 2008-12-19
I don't believe so.

Windows and Linux handles drivers differently. As far as I know (and I could be wrong):

Windows references driver files to learn how to use devices.
Linux modifies the kernel to learn how to use devices.

Quite different...

As for the synaptic problem, you may have to go command-line diving.

Off-hand, there is a config file somewhere with values you can adjust. I, for the life of me, cannot remember what that is, however.

---

### Post by 11010110 on 2008-12-19
thanks for the reply. Thats disappointing though i sure would like to get these corner tap buttons working lol.

---

### Post by Paqman on 2008-12-19
Wine doesn't work for drivers, it's really just for apps.

---

### Post by adasilva on 2008-12-19
I had a problem with my touchpad as well. You need to do some configuring to your xorg.conf file. Make sure you do a backup first!!!! Have a look here:
[http://ubuntuforums.org/showthread.php?t=1003623](http://ubuntuforums.org/showthread.php?t=1003623)
and at the website I link to there, which has more complete instructions.

---

### Post by 11010110 on 2008-12-19
thanks for the reply,

My touchpad functions fine (aside from the fact that i pretty much have to smack my computer to get it to click on tap lol)i was just wondering if there was a way to get the virtual corner tap buttons working. 

Thanks though!

---

### Post by Kareeser on 2008-12-19
Off-hand, I believe there are variables for the corner-tap.

After all, the Windows drivers just modify the same variables... Google is your friend :)

---

