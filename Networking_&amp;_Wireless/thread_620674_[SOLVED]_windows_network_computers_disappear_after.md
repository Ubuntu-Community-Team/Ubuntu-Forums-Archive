---
title: "[SOLVED] windows network computers disappear after network dying and then coming back"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by djrobthaman on 2007-11-22
Hi,

Normally I can see all the windows computers on my network and I'm sure if I restart my problem will be solved.  But I was wondering if anyone knew how to fix it without a full system restart.

So, what happened was, everything was fine.  I could see everyone on my network and it was all great.  Then maybe somebody knocked over some coffee in the wrong place over at my ISP and the internet went down.  Ever since then I noticed I can't see anyone on my network.  The internet has since come back and still I can't see them and they can't see me.

Has anybody had this problem... hopefully even fixed it?

Thanks

---

### Post by jetsam on 2007-11-23
```
sudo /etc/init.d/networking restart
```
and maybe
```
sudo /etc/init.d/samba restart
```
might be worth a shot.  Not sure if it will work or not, though.

---

### Post by djrobthaman on 2007-11-23
It didn't work :(

Thanks for the help though.  Any more suggestions by any chance?

---

### Post by jetsam on 2007-11-23
Not any very good ones, but there's always something different to poke at...  :)

Nautilus doesn't seem to have a very good way to force a rescan of the windows network.  I wish it did, because it might help with troubleshooting.  I assume you've tried hitting reload while browsing the network.

```
smbtree
```
...in a terminal might show your network in the terminal.  Doesn't really solve the problem, but it would narrow it down to Nautilus.  

Other than that, logging out of gnome and back in again through the shut down window might work.  It's sort of half a restart.

---

### Post by jetsam on 2007-11-23
Got it!  (I hope.)
In a terminal:
```
nautilus -q
nautilus
```
...quits nautilus and then restarts it.  This reinitializes something called the gnome-mount extension.  This worked for me after I intentionally borked nautilus network browsing by restarting my Samba server.  

That was a lot of effort searching for a small problem, but this command is useful for general troubleshooting purposes.  

Let me know if it works for you... (if you haven't just restarted your computer yet.)

---

### Post by djrobthaman on 2007-11-23
Ok, so I haven't restarted out of stubbornness.  I'm going to fix this!!!!

I tried both your suggestions.  First I restarted nautilus from the terminal using the commands you posted to no avail.  Then I typed in smbtree and the terminal spat back a listing of every user on my network and exactly what they were sharing.  So, it must be something up with nautilus (????) because it's obvious that something somewhere in linux at least registers the existence of other people on the network.

What else do you think I can do?????

---

### Post by jetsam on 2007-11-23
Well...  penguin poop.  :-?

The problem isn't samba, it's something in the way nautilus or gnome-vfs or some other gnomish thing interacts with samba.  

A workaround: type "smb:///" into the location bar in Nautilus (control-l to bring it up if you can't see it.)  This let me see my network once when I had it broken.  

Now I can't even seem to break it in the same way again.  It has to do with which computer is the designated master browser according to the SMB network.  It's all very unpredictable.

---

### Post by djrobthaman on 2007-11-23
Tried the "smb:///" trick already.  As far as nautilus is concerned, it's an empty folder  :(

arrghhh

---

### Post by djrobthaman on 2007-11-23
Remember the whole stubbornness thing.  Will that went out the window when I needed something on a network share.  So I logged out using CTRL+ALT+BACKSPACE, logged back in  and everything's fine now.

Hopefully it doesn't happen again.  I really wanted to get it to work without such a drastic measure though :(

Anyway, thanks for all the help

---

### Post by jetsam on 2007-11-23
Sure, no problem.  

Restarting was probably best, as going much deeper into the gnome services stuff could maybe destabilize your computer.  It's a missing feature; Nautilus should handle this better.  Maybe Hardy Heron...

---

