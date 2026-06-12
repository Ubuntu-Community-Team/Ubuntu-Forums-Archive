---
title: "Ubuntu reinstallation problem"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by docdob on 2008-12-06
Recently bought a Dell Inspiron Mini laptop with Ubuntu, rather than Windows - by mistake, to be honest, as we had never heard of Ubuntu before. It seemed very user friendly so we decided to stick with it.  However, after trying unsuccesfully to upgrade to 8.10 - which came out about a week after our laptop arrived -the update manager stopped working altogether. Having tried various fixes posted on the Ubuntu support site, none of which worked, we did a reinstall using the Ubuntu CD that came with the laptop.  The reinstall seemed to go fine and the update manager functionality was restored.  However, following a prompt to restart the (message said something like Firefox has been updated, restart), we have ended up with a black screen showing the following message:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

We tried doing a fresh reinstall, which started out fine but stopped about three quarters of the way through.  Tried again, same problem.  So we are stuck with the screen above and no idea where to go from here.  

Can anyone help?  Our only alternative is to return the laptop to Dell and buy the Windows version - Microsoft wins again.

Many thanks in advance.

---

### Post by oilchangeguy on 2008-12-06
"Our only alternative is to return the laptop to Dell and buy the Windows version - Microsoft wins again."

don't blame microsoft for your mistake. have you called dell to find out how to return the computer to the factory settings? have you read the owners mmanual, to find out how to return the computer to the factory settings? no, you tried to do something, when you had no idea what you were doing. call dell.

---

### Post by mapes12 on 2008-12-06
It sounds like some of your old (broken) installation remains on the machine after you have done the re installation. It may be worth running a [low level format utility]("http://hddguru.com/content/en/software/2006.04.12-HDD-Low-Level-Format-Tool/") across the entire HDD then try re installing afresh.

However, before doing the above you might want to speak to Dell to see if they have set up the partitions on the machine in a quirky way such as having a recovery partition somewhere. You can see for yourself what partitions you have by booting from a GParted Live CD. This may be on your current installation disk or you can download and burn one from [here]("http://gparted.sourceforge.net/").

EDIT - I would also suggest burning a fresh [installation disk]("http://www.ubuntu.com/getubuntu/download"). I would stay with version 8.04 to take advantage of the longer support. But it's your choice.

---

### Post by bwallum on 2008-12-06
Hi docdob, sorry to hear that you are having probs with a new machine. Firstly, I've been using Ubuntu for about a year now and will never go back to MS. You need to run Ubuntu for a while to appreciate it however.

I would strongly recommend downloading a Hardy Heron (8.04) 'live cd'. You need to copy the file to a cd, that is burn it, and then run the cd. I have to say that the Intrepid (8.10) install disc has given me problems on two set ups to date. Hardy Heron is solid.

When you install from the cd use all the harddrive, it will then obliterate anything proprietory that Dell may have put on.

Once you have Hardy up and running you could then upgrade to Intrepid. The online upgrade for Intrepid has worked well for me.

Hope that helps and I hope you stick with. Just to be virus threat free is a massive plus but wait until you start using some of the free open source packages, they are simply excellent. OpenOffice is better in my opinion than MS Office. Evolution is better than Outlook, gimp is the best image manipulator I have used (but tricky to learn). Specialist 3D modelling software like Gmsh is very quick for a pc application. I would bore you if I continued.

Good luck and I hope oilchangeguy recovers from his grump soon.
Regards, Bob

---

### Post by Badly Overdrawn Boy on 2008-12-06
I think the replies so far may be missing an important point. I think the OP has bought a Dell Mini 9 which does not have a CD drive or the standard version of ubuntu and so the restoration process will be a little different.

Docdob, I don't know how to solve your problem, but maybe if can edit your post to include 'Dell Mini 9' somewhere in the title you will get a better response. I am quite sure there are some on here who will know exactly how to solve your problem.

I suspect your original problem stemmed from trying to upgrade to 8.10. The Dell Mini 9 install is slightly different from the standard install, also there have as yet been only one or two updates released for it, possibly leading to you thinking that the updates were broken. Furthermore, 8.04 is a 'long term support' version so there's no harm in sticking with it for a good while until you get familiar with ubuntu.

I'd like to think you could stick with ubuntu, I'm sure you won't regret it in the long run.

EDIT: Mods- Maybe this thread would get more response if moved to the 'Dell Ubuntu Support' forum?

---

### Post by Tom Atkins on 2008-12-06
I do not know if you have tried this but there is a forum devoted to Dell Ubuntu installs. You could try posting your problem there.

Good luck.

---

### Post by bwallum on 2008-12-06
> **Badly Overdrawn Boy said:**
> I think the replies so far may be missing an important point. I think the OP has bought a Dell Mini 9 which does not have a CD drive or the standard version of ubuntu and so the restoration process will be a little different

Apologies for any mis-leads. I was not aware that you didn't have a cd drive. One thought, can you attach an external cd drive? They come with a usb 2.0 connection. 

Good luck

Bob

---

### Post by docdob on 2008-12-06
Thanks so much for the helfpul replies and sorry if the original message wasn't 100% clear.

Badly Overdrawn Boy is exactly right, I have a Dell mini 9, which doesn't have a CD drive.  I borrowed an external drive for the reinstall and went out today to buy one for myself. Turns out the guy in the computer shop is a self-confessed 'Ubuntu nerd' who was kind enough to offer his assistance, so I'm going back there tomorrow with the mini in tow.

The most encouraging thing was that this guy really wants me to persist with Ubuntu - which I am also keen to do. I love the idea of open source and of a community of users  helping each other. I was a little discouraged after the first response to my original posting but the subsequent responses (virtual and otherwise) have really encouraged me to keep going, so thanks, everyone. Looking forward to being part of the Ubuntu community once I get over this first hurdle!  I'll report back when things are sorted in case anyone else has the same problem.

Thanks again.

---

### Post by Duck2006 on 2008-12-06
You can also do a install from a usb stick. If you can boot from one.

[www.pendrivelinux.com](www.pendrivelinux.com)

---

### Post by bwallum on 2008-12-06
> **docdob said:**
> The most encouraging thing was that this guy really wants me to persist with Ubuntu - which I am also keen to do.

Bravo! I wish you well, it's great once you're in!

---

