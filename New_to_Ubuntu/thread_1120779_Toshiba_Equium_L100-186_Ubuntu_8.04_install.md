---
title: "Toshiba Equium L100-186 Ubuntu 8.04 install"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by tiggsy on 2009-04-09
Hi I'm having exactly the same problem as mentioned in this archived thread: [http://ubuntuforums.org/showthread.php?t=613987](http://ubuntuforums.org/showthread.php?t=613987)

to which no fix seems to have been given

The main problem is that I can't get my friend's Tosh to boot from the CD. Then if you select any installation type, the Ram available is only 222mb, presumably because the Tosh is using 34mb for something else. 

We did one install, it keeps coming up with 

```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```


- and you end up with a desktop with no panels, no menus, nothing but the heron.

Any ideas?

PLEASE!?

---

### Post by Hospadar on 2009-04-09
Have you tried installing kubuntu or xubuntu?

I don't know offhand why gnome wouldn't be able to start up panels, but the first thing I would want to try is to see if it's just a gnome problem, or if there's something more seriously wrong (which would probably cause errors in other desktop environments as well)

You also might want to try getting the latest jaunty CD.  There might be some bug which has since been fixed in jaunty.

---

### Post by tiggsy on 2009-04-09
But as I don't have a working copy of ubuntu on the laptop, i can't apt-get anything. I can't even run terminal. None of the panels is there, nor any of the Applications/Places/System menus

What I have done is to talk him into getting a memory upgrade. A 1gb stick should arrive by Saturday. Then I will try a fresh install - and we will have enough RAM. Hopefully that will work, because every way round I've tried up to now has NOT worked at all. And in Windoze the laptop is so slow you could run to Sydney and back while it boots up.

---

### Post by tiggsy on 2009-04-10
Right. The extra 1gb of ram has done the trick, and I used F12 on the brief Tosh startup screen to force boot from CD. We now have a working copy of Ubuntu, but it's not connecting to the network wirelessly. I got a message about proprietary stuff, but it didn't say how to get them...

---

