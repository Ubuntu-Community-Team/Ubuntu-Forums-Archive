---
title: "How to sync musik to Iphone"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by Lillegris on 2009-01-01
I am new to Ubuntu and i cant seem to find a program that can read my Iphone. I would be glad if I could get some help. :)

---

### Post by %hMa@?b&lt;C on 2009-01-01
the newer GTKpod should work well.  the iphone must be set up using itunes on windows and a song must be copied over.  
sudo aptitude install gtkpod
will install gtkpod
of course if you have been using the iphone and copied stuff before, you should have no trouble

---

### Post by Lillegris on 2009-01-01
It dont seem to work. it cant see the phone.

---

### Post by %hMa@?b&lt;C on 2009-01-01
> **Lillegris said:**
> It dont seem to work. it cant see the phone.

launch it from terminal.  post any errors that you get.

---

### Post by evilkastel on 2009-01-01
Excuse me if i am ignorant, but i read that the ipod touch and Iphone implement another way of writing to the device, As a trick from apple to keep non Itunes apps from sync. As far as i know there is no way to put files in an Ipod Touch or Iphone. Again, someone correct me if i am wrong.

---

### Post by stderr on 2009-01-01
[color="red"]**DON'T use gtkpod!!!!!!!!!!**[/color]

SERIOUSLY. DON'T.

Unless they've already released a new version to fix the problem, it will corrupt your music library and you'll have to re-copy everything.

I was desperately trying to get my iPhone 3G 2.2FW hooked up and working under Linux. I think the long and short of it at the moment is it's a no go. You can copy music via SSH (after your iPhone's jailbroken and you've installed OpenSSH) and play it on your iPhone with the likes of mplayer, VLC etc, but to get it added to the iPod application you need to use iTunes. It's a real pain in the ****.

Even though I'm a Linux nutter, I still have to reboot to Winblows to copy music. Unless anyone else has some suggestions?

evilkastel: You're right, they did change the implementation for the iPhone. It really isn't the same as an iPod.

---

### Post by Captain_tux on 2009-01-01
> **evilkastel said:**
> Excuse me if i am ignorant, but i read that the ipod touch and Iphone implement another way of writing to the device, As a trick from apple to keep non Itunes apps from sync. As far as i know there is no way to put files in an Ipod Touch or Iphone. Again, someone correct me if i am wrong.

You are correct and that's thanks to our friends at Apple.

To Linux/Ubuntu, the iPhone only appears as a camera.

---

### Post by kristopher.ives on 2009-01-01
Rhythmbox offers the iPhone plug-in, but I don't know if it lets you add media to the device. My friends have used GTKPod without issue for copying audio and video to their devices, but another user above did say he had issues.

---

### Post by stderr on 2009-01-01
> **kristopher.ives said:**
> Rhythmbox offers the iPhone plug-in, but I don't know if it lets you add media to the device. My friends have used GTKPod without issue for copying audio and video to their devices, but another user above did say he had issues.

Hmm, well I'll have a look at the gtkpod site and see if they've updated it for the 2.2 iPhones.

I don't want to be advising people not to use something that works ;) but yeah, my experience and the experiences of many other people I found online were not positive, to put it mildly.

edit: Their site doesn't mention any recent changes. So I would personally still **strongly** advise against using ANYTHING which uses the **libgpod** library to access the iPhone's music DB, including gtkpod.

@kristopher: Do you happen to know which iPhone firmware version your friends used with success? I'd be interested to hear how they achieved it

---

