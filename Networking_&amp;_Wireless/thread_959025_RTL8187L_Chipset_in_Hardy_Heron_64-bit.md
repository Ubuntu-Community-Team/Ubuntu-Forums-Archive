---
title: "RTL8187L Chipset in Hardy Heron 64-bit"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by sunkssss on 2008-10-26
I'm a noob when it comes to linux and am currently using Ubuntu 8.04.1 64-bit and am attempting to use my RTL8187L wireless chipset adapter by using xp 64-bit drivers through ndiswrapper, but it's just not working. In fact when I attempt to use the 64-bit driver the system gets real buggy and the screen gets nasty upon booting up (talk about layman's terms). I was able to get this adapter working in Ubuntu 32-bit but my system was having severe performance issues (would prevent me from using Ubuntu almost entirely) and I was hoping the 64-bit version would solve this.

Anybody have any ideas for working towards a solution? I've been trying to get Ubuntu working on one of my computers for three years now, but have had absolutely no success in all that time. Some little thing always puts me up against a wall, and it's a shame because I just love everything else about its design. I'd really appreciate any help.

---

### Post by sunkssss on 2008-10-26
Here's a weirder question:

Is it possible to setup Wine without an internet connection (but being able to import files via flash drive) and then run the a wireless utility in the Windows environment into Ubuntu to get a connection? I've never used Wine, so perhaps I'm misunderstanding its potential.

---

### Post by panhandle on 2008-10-26
I think the latest kernel release has support for this chipset.

It worked "out of the box" on my Intrepid Ibex machine.

---

### Post by sunkssss on 2008-10-26
In Hardy Heron there is a severe issue, see:

[http://ph.ubuntuforums.com/showthread.php?t=911581](http://ph.ubuntuforums.com/showthread.php?t=911581)

and 

[http://ge.ubuntuforums.com/showthread.php?t=888120](http://ge.ubuntuforums.com/showthread.php?t=888120)

I'm hoping the 8.10 release fixes this, but until then I'll keep my fingers crossed and will be testing out Mandriva, and if that doesn't work then I'll go with Kubuntu or PC-BSD or FreeBSD

---

### Post by panhandle on 2008-10-26
As I mentioned in my last post, 8.10 does indeed support this chipset. I'm already using it in beta.

---

### Post by sunkssss on 2008-10-26
I'm sorry, I misread your post. That's awesome news.

---

### Post by sunkssss on 2008-10-27
Are you using the amd64 version? I've got 8.10 installed now, and am still experiencing the same problem. Perhaps it's only working in in the 32-bit version. The adapter works for a short time, but then drops to zero throughput. Any ideas how to get ndiswrapper working? I've installed ndiswrapper, but when I go to install both the xp and x64 driver it says "invalid driver!"

Scratch that, I'm just going to wait until something more stable comes out. In the mean time, if I limit the throughput it should keep the adapter from stopping on me. As you can probably tell, I'm very new to Linux and don't know how everything works. Could anybody direct me to a tutorial for limiting throughput in 8.10?

Scratch that too, I'm just going to go back to using Gutsy Gibbon.

---

### Post by panhandle on 2008-10-27
Now it's my turn to have misread *your* post. :)

64-bit 8.10 works with the RTL 8187B, and apparently not the RTL 8187L.

However, I found this thread that might help you:

[http://ubuntuforums.org/showthread.php?t=808101](http://ubuntuforums.org/showthread.php?t=808101)


Seems that the RTL8187L will work (according to one of the posters near the bottom of the first page) with 32-bit Hardy.

Also, for you ndiswrapper woes, a pretty good howto:

[http://ubuntuforums.org/showthread.php?t=885847&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=885847&highlight=ndiswrapper)

---

### Post by sunkssss on 2008-10-27
I had very poor performance with my system in 32-bit Hardy, so that isn't an option for now. I'll try installing ndisgtk like that last poster suggested in 64-bit Hardy, but I'm not too optimistic. Like I said, I'll probably give Gutsy 64-bit a try since it supposedly works flawlessly or give FreeBSD or Kubuntu a try, though honestly I like Ubuntu much more. Patience pays in the Linux world I suppose, and I need to be more patient. Thanks for the pointers though.

---

### Post by panhandle on 2008-10-27
I had a machine with the RTL 8187B, and although it was torture to get the thing working in Hardy, I remember it worked well with FreeBSD. Perhaps the same with the "L".

Also, I think Fedora 9 worked as well.

Good luck.

---

### Post by sunkssss on 2008-10-28
In case anybody is interested I found that using WICD in hardy works fine for connecting to an unsecured network. This is acceptable for me, since I feel Ubuntu is already pretty secure. Thanks folks, though I'm not sure why anybody posted this solution earlier (save for one minor post I saw somewhere among hours of reading, kudos to you sir).

---

### Post by sunkssss on 2008-10-28
So using WICD I was able to get a stable connection. However after running the update manager and letting ENVY automatically install my video drivers WICD just got worse and worse. It now does not pick up a single network and meekly refreshes every 5 or 10 seconds. Any suggestions? Should I bother trying to use ndiswrapper? Or should I just reinstall Hardy and not let it update, and then give ENVY another go, or just stick to the almost worthless restricted drivers (at least as the noob I am I'm unable to get them to work without crippling my system, though that's been my experience thus far, and reinstalling after each failed attempt is really becoming frustrating)?

---

