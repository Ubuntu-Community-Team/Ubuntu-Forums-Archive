---
title: "VLC for Linux"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by Dr Heelhook on 2010-10-08
Hi, I just installed Ubuntu 10.10 and registered to the forum and I am trying to install VLC media player, but I can't get it to work. I tried the search function, but I couldn't find a good answer in any other thread. I went to the software center and found VLC there. I clicked on install, but when I was halfway through the installing process, it just said: 

"Failed to download package files

Check your Internet connection."

I checked my Internet connection, but my Firefox was working fine, so I guess the connection was OK. I've tried a couple of times since then and it still doesn't work. What do I need to do? 
Thanks.

/Oskar

---

### Post by Locke_99GS on 2010-10-08
Try changing the mirror used in software sources.

---

### Post by andymorton on 2010-10-08
From the VLC website :

Open Synaptic application
Click on System -> Administration -> Synaptic Package Manager.
In Settings -> Repositories, make sure you have an universe repository activated.

Search for vlc and install it. You should install vlc-plugin-pulse and mozilla-plugin-vlc as well.

If you are interested in streaming or transcoding, you should additionally install libavcodec-extra-52 from a multiverse repository.


andy

---

### Post by beew on 2010-10-08
You are using a beta or a daily build version of Maverick so it is not surprising that some things don't work. I have been getting 404 packages not found when I tried to check updates. Just wait for it to sort itself out. :)

For me, update didn't work last night (it worked again this morning) Compiz still doesn't work and open office still doesn't open.

---

### Post by Dr Heelhook on 2010-10-08
> **beew said:**
> You are using a beta or a daily build version of Maverick so it is not surprising that some things don't work. I have been getting 404 packages not found when I tried to check updates. Just wait for it to sort itself out. :)

For me, update didn't work last night (it worked again this morning) Compiz still doesn't work and open office still doesn't open.
Ok, so will I be offered to update to update to a more complete version later when that one is ready then?

---

### Post by coffeecat on 2010-10-08
> **beew said:**
> You are using a beta or a daily build version of Maverick so it is not surprising that some things don't work. I have been getting 404 packages not found when I tried to check updates.

> **Dr Heelhook said:**
> Ok, so will I be offered to update to update  to a more complete version later when that one is ready then?

I don't think that using a pre-release is the reason at all. I've been  using Maverick for some weeks now and I have not yet had a 404 problem with the main UK mirror.

As Locke_99GS implied, this is more likely to do with the repository server  your system is accessing. Open System > Administration >  Synaptic. Then Settings > Repositories > Ubuntu Software Tab.  Click on the button next to "Download from" and you can change your  mirror. Choose 'Other' and you can click on 'Select Best Server'.

---

### Post by Dr Heelhook on 2010-10-08
Aah, you're a lifesaver coffeecat. I changed the download server and I got it. Thanks. :)

---

### Post by Dr Heelhook on 2010-10-08
How do I mark a thread as solved BTW?

---

### Post by coffeecat on 2010-10-08
> **Dr Heelhook said:**
> How do I mark a thread as solved BTW?

At the top of the thread, on the right, 'Thread Tools'. In the drop-down list. Only the OP can mark it (and perhaps a member of staff.).

Good luck with Ubuntu!

---

### Post by Locke_99GS on 2010-10-08
Immediately above your first post, and on the right side are three links. one of them sais "Thread Tools" or something of the sort. Clicking that will drop a menu, one of the entries is mark as solved.

---

### Post by beew on 2010-10-08
Thread tools on the top menu.

Glad that you got it working. :)

---

