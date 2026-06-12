---
title: "Upgrading to 9.10 Fails, Freezes after login: compatability issue"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by cheph on 2009-12-16
Hello All,


 So I tried to upgrade from Ubuntu 9.04 to 9.10 but when I did the computer froze, I tried restarting but it started freezing before the login screen. I figured that it was my fault so I tried a fresh install of Ubuntu 9.10 (I should mention I'm using 64 bit), but I ran into a similar problem which made me suspect that it was not a bad upgrade but a compatibility issue. After the fresh install Ubuntu would boot fine the first time but freeze before the login screen every time I try to boot after that. To be sure I checked the integrity of the install CD but it was fine and was burned at x4 speed. One last thing, if I choose the log in automatically option on the install I get the following error message at the login screen:


 Sudo Passwd Root Could Not Update ICEauthority File /Home/Cheph/.ICEathority


 and


 Their is a problem with The Configuration server /usr/lib/libgconf2-4/gconf-sanity-check-2 excited with status 256


 I'm currently back on 9.04, any help would be much appreciate.


P.S. I have filed a bug report a while ago but I have got no response, you can find that here: [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/494420](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/494420)

---

### Post by lrcaballero on 2009-12-16
when you tried up-grading did it frozed when it was downloading packages??? is this a laptop or pc?? make sure you are connected to internet (wired) NOT wireless for faster and prompt upgrade. This happend to me also when upgrading to Karmic like 3 times and just last week I upgraded to karmic but this time I was connected directly to my modem rather than wireless. Try this and see if this works.

Good Luck

Luis

---

### Post by cheph on 2009-12-16
You know how when you do an upgrade it has to restart to finish the job, that is when it froze for me (after the login screen before the desktop loaded).

Attached is the result of sudo lshw -html > cheph.html for my hardware specs if that helps.

---

### Post by cheph on 2009-12-17
Opps here's that attachment.

---

### Post by kansasnoob on 2009-12-17
Not what you want to hear I'm sure but Karmic is still incredibly unstable on my hardware, so I just use Jaunty which is super stable for me!

That said I'm using Karmic right now to post this because X seems better for me with this;

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

**Note however that it can be risky:**

> Packages for those who think development versions, experimental and unstable are for old ladies. We want our crack straight from upstream git! Well, straight, we want it built and packaged so we don't need to know what we're doing, except that we will break our X and put our computers on fire.

If you cook it, you own it!

---

