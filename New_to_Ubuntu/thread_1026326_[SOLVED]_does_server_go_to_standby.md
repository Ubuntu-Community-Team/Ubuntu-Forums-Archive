---
title: "[SOLVED] does server go to standby?"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by anewguy on 2008-12-31
I just last week got a basic Ubuntu server install done with samba and have it for now just sharing a hard drive.  One thing I've noticed - after several hours, the server is no longer seen on the network.  My netowrk currently consists of Comcast broadband coming in through one of their RCA modems, then to a Vonage box for phone service, and then to my wireless router.  A Windows XP Pro machine is directly wired to one of the ports on the back of the wireless router.  The server connects via wireless to the router and uses a static IP address - the way I understand it is that the server is only visible on "this side" of the wireless router - not to the world.  I have anohter box coming (was supposed to be here already) to use as my Ubuntu-only desktop box.  What happens, and it seems rather random, is that the server will disapear from the network.  Not visible on the XP box, doesn't show in the router.  I have to reboot the box for it to become visible again for several hours.

Does a server ever "sleep"?  If so, is there a way to disable that?  

Has anyone else run into this before?  BTW - it's a Netgear wireless router.  The server uses a Belkin USB network adapter that just works out of the box (at least when you install Ubuntu with it plugged in).

Thanks for any help!

dave :)

---

### Post by fatbotgw on 2008-12-31
It sounds like it's lost the wireless connection...

Can you connect it with a network cable and see if it still disappears?

---

### Post by anewguy on 2008-12-31
Well, I would, except...... I don't have a second network cable (blushing!).  So, if I move the cable to server I have no way to know if it's visible on the network.  I'd also have to re-do the config so the NIC was getting the static IP instead of the USB adapter, and I think that would end up doing an end-around and clearing any problem.  Right now I wish I had a hub or something and a couple of extra cables!

Thanks for the reply - and it's a good one - I just lack what I need to test that way!

Dave :)

---

### Post by Dr Small on 2008-12-31
Definitely sounds like the wireless network is dropping out. I had about the same thing happen to mine at odd various times, and once I hooked it up to ethernet, I don't have anymore problems out of it.

---

### Post by lazyart on 2008-12-31
It's possible that the wireless NIC is doing some power saving thing.  When the server disappears go to it and try to ping something to wake up the wireless, then see if it's visible once again.

A server with a wireless connection?  Odd indeed...

---

### Post by anewguy on 2008-12-31
Thanks everyone!  I'll give all of those a try.  I may end up getting my old switch back from a friend - if so, I think I'll run the cable I currently have to it, then find cables to hook up the Windows box and the server to it.  I have another box coming that will be my Ubuntu desktop box, so I guess that would make sense - a cable to the room where I keep the computers, connected to a switch, and the 3 boxes wired to the switch.  Does that sound like that would work?

Thanks!
dave :)

---

### Post by anewguy on 2009-01-08
Well, I can't seem to get around it.  Sometimes it runs okay for days, other times a few hours, then no internet via the wireless on the server.  Moving the wireless USB connection to another USB port doesn't help.  Oh well, guess I'll mark this as solved.

Thanks for the input!

Dave :)

---

### Post by b0b138 on 2009-01-08
Check if theres any type of bios enabled power saving something that turns off usb after a period of inactivity

---

