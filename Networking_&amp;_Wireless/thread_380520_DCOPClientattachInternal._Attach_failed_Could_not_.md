---
title: "DCOPClient::attachInternal. Attach failed Could not open network socket"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by asg33 on 2007-03-09
hey, new to ubuntu and linux just got started on edgy eft last week. everything seem to be going good, and i've solved a lot of problems searching the forums, very helpful. i ran into a new problem today though. when i start up firefox, i can browser for about 5 min, and then i get the not responding fade to gray, where i can't do anything in firefox, then it comes back for about 30 seconds then back to not responding, this happens infinitely until i open the system manager and kill the firefox process. i really don't know what the problem is and i've searched the forums for something along those lines, and can't really find an answer. not sure where to start with this. any help would be greatly appreciated.

ubuntu edgy eft (6.10)
p4 2.4 ghz, 1gb ram
cable modem, w/linksys wtrg54 router.
ati radeon 9200se

ok been using firefox for a good 4 hours, everything seemed ok then it went into the "not responding" thing again. here's what my terminal said:

"DCOPClient::attachInternal. Attach failed Could not open network socket"

that just kept repeating. after i killed firefox, it still kept repeating. i rebooted and am using it now, but i'm positive it will happen again. any ideas? thanks in advance.
Edit/Delete Message
---------------------------------------

posted this in the begginer forum few days ago, didn't get anywhere. can anyone help?

---

### Post by tmcmack on 2007-07-03
I'm seeing the same thing in Feisty. Seems connected to Flash, because Firefox responds normally (despite giving those DCOPClient messages to the terminal) until I visit a page with Flash on it. Then, a few minutes later, I see the slowdown you're talking about, where it freezes for a few minutes and then frees up for 10-20 seconds before freezing again. Is your problem connected to Flash as well?

I've run FF from the console and watched the RAM and processor usage with TOP, and it indicates no strain on either. Linux guys, what else can we do to diagnose the problem? I've tried disabling all my extensions, too, with no effect.

I'm considering removing and installing Flash, but as I'm new to linux too, I'm not 100% sure how to do this, because flash doesn't appear to be installed according to Synaptic.

---

### Post by GtzGtz on 2007-08-27
Hi,
I'm also having the error, in the same circunstances detailed by asg33, I don't check if the problems is trigger by Flash, but in my case the problem was resolved (aparently) by the following command in console:
$ dcopserver
I'm also a newbie trying to use Linux as my first desktop operating system, so I don't know why the above worked for me, but I imagine the error its because some client component cannot reach the server component so I tried executing the server component manually and it works.

---

### Post by jms1989 on 2007-08-30
I'm having the same problem except it doesn't fade to gray or black. It just freezes then I have to shut down the process. It will even lockup on pages with no flash at all. I can't uninstall flash because I need it for my favorite websites. The has got be be something else causing it.

---

### Post by loki99 on 2007-12-02
Thanks! Running dcopserver fixed the issue temporarily. I auto run it after login now which is nothing but a dirty fix though! 

Does anyone know why this happens?

---

