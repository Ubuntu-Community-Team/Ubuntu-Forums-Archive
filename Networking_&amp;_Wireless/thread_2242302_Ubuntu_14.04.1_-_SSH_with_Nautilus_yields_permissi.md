---
title: "Ubuntu 14.04.1 - SSH with Nautilus yields permission erorr"
date: 2014-09-01
forum: Networking &amp; Wireless
---

### Post by d.vanheeckeren on 2014-09-01
Hi everyone!

Been using Linux for years now, and I know this has got to be something stupid... probably a result of not having slept in 30 hours.

Anyway, here's my problem:  Was using 12.04 on my laptop and desktop.  Saw 14.04 LTS was released, so ran the upgrade on both.  Ended up with a memory leak error, so decided to reinstall from scratch.  So I moved all my personal data from the laptop to the desktop via ssh.  Well, sftp I suppose.  Reinstalled fresh on the laptop, then moved all it's data back.  Using the laptop, moved my data from the desktop to the laptop because trying to connect from desktop to laptop produced, "Oops! Something went wrong.  Don't have permission to access the requested location".  Figured that was an issue with version differences, so I ignored it.  Now have installed fresh on desktop and can't move my data back.  Now I get the same permission error on both ends... from laptop to desktop or desktop to laptop.

I've searched all over these forums and google and can't seem to find anyone else with the issue.

On a side note, I seriously thought there was something wrong with me, simply because of what I thought was my typing.  I first experienced it on the laptop (which is what I use most), since I type around 80 words per minute, I thought it was me.  But as I would type on the laptop, keys I pressed would get swapped around randomly.  I thought I was the first known case of acquired dyslexia.  But my wife pointed out to me that I was typing fine on my desktop.  After upgrading the desktop, though, it's doing the same thing.... so at least I'm not dyslexic.  I can handle typing slower to avoid that for now, but I really do need to get this ssh/sftp thing fixed.

Now granted, I'm no expert, but I've been using Linux for 4 years now, specifically Ubuntu... so I'm thinking it has to be something simple I'm missing, but nothing I try seems to do any good.

Any thoughts?

---

### Post by clalian on 2014-09-21
I am getting the same problem over here.

> Oops! Something went wrong.  Don't have permission to access the requested location
While using Nautilus, I try to connect to a server, and do   sftp://ip.add.ress  and it tells me that error message.

Any insights on what could be going on here?

---

### Post by d.vanheeckeren on 2014-09-21
I'm so sorry, I forgot to update this once I found the answer.  And it was ridiculously easy once I figured out the problem. As it turns out, the ssh required isn't installed by default.  Just type this into terminal and you'll be good to go:

```
sudo apt-get install openssh-server
```
NOTE:  You'll need to do this on each machine you'd like to connect to.  I've installed it on all my machines, and since then, have had no problems.

Note 2:  If you find you want to access other parts of the filesystem other than the home directory, connect first using the ssh://ip.add.re.ss, and then after Nautilus opens it, hit CTRL-L to open the location bar.  Once that's open, simply delete everything after the ip address and slash and hit enter.  For example, if it shows sftp://192.168.1.1/home/myusername, simply delete the extra to make it look like so:  sftp://192.168.1.1/

---

