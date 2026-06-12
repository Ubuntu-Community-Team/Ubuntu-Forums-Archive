---
title: "Black screen in Ubuntu 11.04, upgrade from 10.10"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by cosine352 on 2011-04-28
I have upgraded Ubuntu from 10.10 to 11.04 and now after I login I can only see my mouse cursor on a black screen. I can still login without  any problem in the "Ubuntu classic" desktop though.

How do I fix this problem? 
I have a Intel Integrated graphics card.

---

### Post by cosine352 on 2011-04-28
Unity is not working properly. I tried to start Unity while in "Ubuntu classic" mode in terminal and it shows lot of errors.

---

### Post by BertN45 on 2011-04-29
I have an Intel Integrated Graphics 8286SG and it does not work either. I filed a bug report during the Alpha phase as did many others, but the problem is not solved yet. Your are out of luck for the moment, but at least Gnome works now.

I switched to Xubuntu, but also there I see some small glitches.

---

### Post by aaron76 on 2011-04-29
I upgraded last night and my laptop wouldn't boot either. I just got the Ubuntu logo staring at me.
I downloaded the iso from a torrent site, burnt the cd and did a fresh install.
No problems now.

---

### Post by conradin on 2011-04-29
OMG Im updating now after several near lethal updates from Lucid. 
I hope sooooo mcuh I dont reget this!

---

### Post by faisalsadaf on 2011-04-29
Luckily I was working with a Virtualbox VM and I took a snapshot prior to upgrading to 11.04. I had the same issue:
- While logged into Ubuntu 10.10, I selected the upgrade option from Update Manager
- It informed me that several packages were no longer compatible with Canonical, and some others had to be removed.
- After install, system rebooted, and now all I  get is a black screen. 

At the bottom of the screen, I do see that there is occasional hard disk activity, but after about 10 minutes, nothing on the screen.

I would appreciate a response on how to fix this. Thanks.

---

### Post by Holden99ca on 2011-04-29
> **cosine352 said:**
> I have upgraded Ubuntu from 10.10 to 11.04 and now after I login I can only see my mouse cursor on a black screen. I can still login without  any problem in the "Ubuntu classic" desktop though.

How do I fix this problem? 
I have a Intel Integrated graphics card.

I have exactly this same problem. I'm running an Acer Aspire One D150. Would love to hear if anyone's found a solution.

---

### Post by raydar on 2011-05-01
Same problem here, except (1) with an nVidia graphics card and (2) I have the standard wallpaper instead of a black screen.

At one point, upon restarting, I got bizarre video behavior before I got to the gdm login screen: black-on-white gibberish text reporting something that was occurring, though after I tried typing a few commands and hitting Enter just to see what would happen, the normal gdm login screen appeared.

As with the others, this problem occurred immediately after a seemingly successful upgrade to 11.04 from a Gnome Ubuntu 10.10 installation.

---

### Post by lsolesen on 2011-05-02
Same problem on a Shuttle.

---

### Post by tattwood833 on 2011-05-02
Yes I have this same problem, blank screen after what appeared a successful upgrade....

what do I do?

help!

---

### Post by fahlenkp on 2011-05-04
Same problem here. Boot, ubuntu splash goes by, black screen appears with a white cursor that moves ok. I can get to a command prompt but I'm not sure what I'm looking for. Startx gets be back to the same place. Why is it that every upgrade seems to break ubuntu?

---

### Post by YanB on 2011-05-05
Same problem: after 1st splash page, screen goes black, with only mouse pointer. Using eee-pc 1005ha.
Only way to boot to reach the desktop is to add 'nomodeset' to grub, but then I only have the 'Classic Ubuntu' GUI, with my screen limited to 800x600 resolution, and no apparent way to change it.
Any help much appreciated. I curse the day I decided to upgrade... 10.10 was working fine.

EDIT : managed to solve the problem by reinstating the old xorg.conf file in /usr/X11/ folder (I reinstated the file by using the one ubuntu automatically made when updating; see the file with the date on which you made an update). Then I had to reconfigure the size of the monitor using the normal monitor app. Works now after rebooting, but with Ubuntu Classic desktop (which I prefer to Unity).

---

### Post by Holden99ca on 2011-05-06
I would prefer Unity but still something is better than nothing. Can you provide step-by-step instructions please? Thanks!

---

### Post by Holden99ca on 2011-05-09
Bump

---

### Post by Holden99ca on 2011-05-10
OK I've discovered something. At the login screen, if I login to Ubuntu Remix (what I was logging into up until now), I get the black screen as described above. It's almost like there's no display. I can cntrl-alt-del and I get the shutdown window but clicking anywhere on the screen does nothing.

However, what I discovered is if I login with Ubuntu rather than Ubuntu remix I get a perfectly normal boot. In fact, it looks like netbook remix to me-with Unity running as the sidebar.

I'd be very interested in comments.

Thanks!

---

### Post by Holden99ca on 2011-05-12
Sure is quiet in here.

---

### Post by macroshaft on 2011-05-12
My laptop (Nvidia graphics) has started doing this recently. Sometimes it loads, others I get a black screen. Loading in safe graphics mode always works though.

---

### Post by Gauge0123 on 2011-08-21
Just to give my 2 cents ...

I have a Toshiba Satellite A305-S6905 (which has an Intel GMA 4500MHD graphics card), and I have also been experiencing this problem. In particular, if I don't move the cursor around every now and then just after start up the screen will go black except for the cursor, which still moves and can click/manipulate items on the no longer visible desktop. Likewise with the keep board; I can type and such, but I cannot see it what is happening.

---

### Post by martialartist81 on 2011-09-05
This appears to continue to be a persistant issue.

There's several "fixes" out there, however, I haven't seem to find one that sticks.

Here's the sticky on this issue:
[http://ubuntuforums.org/showthread.php?t=1743535&highlight=intel+graphics+black+screen](http://ubuntuforums.org/showthread.php?t=1743535&highlight=intel+graphics+black+screen)

And one that I found that supposedly works for some:

[http://www.russsargeant.co.uk/post/7235981043/fix-for-ubuntu-11-04-black-screen-issue-affecting](http://www.russsargeant.co.uk/post/7235981043/fix-for-ubuntu-11-04-black-screen-issue-affecting)

I'm using an Acer Aspire 5734z-4512 w/ Intel 4500M GMA.

Hopefully, after some additional tweaking and tampering, I'll have something that'll work.  I'm loathing that I'm forced to using my Wind-blows boot instead of 11.04 for the time being.

---

