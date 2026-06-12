---
title: "[SOLVED] Rhythmbox Library Won't Stick After Exit!"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-12-06
When I open Rhythmbox all my music has vanished

Any ideas on why it is doing this? 

It's a bit frustrating because it takes ages to load my music in to the library.

I am using fully up to date Ubuntu 8.04.

Thanks in advanced!

---

### Post by chrisod on 2008-12-06
Is your music stored on a network drive? If the network doesn't respond quickly when you first open Rhythmbox it will drop the database and rebuild it when the network comes back. I used to have this happen somewhat frequently, but now that I think about it I haven't had it happen in a while. I'm not sure if my network is more stable or maybe an update to Rhythmbox made it fail more gracefully on a network drop. 

So I would start making sure Rhythmbox is at the most recent revision, in case that helps.

---

### Post by pluckypigeon on 2008-12-06
> **chrisod said:**
> Is your music stored on a network drive? If the network doesn't respond quickly when you first open Rhythmbox it will drop the database and rebuild it when the network comes back. I used to have this happen somewhat frequently, but now that I think about it I haven't had it happen in a while. I'm not sure if my network is more stable or maybe an update to Rhythmbox made it fail more gracefully on a network drop. 

So I would start making sure Rhythmbox is at the most recent revision, in case that helps.

Hey, thanks for your reply but it's stored in my home partition "~/music" (ext3) and, of course, the drive is always mounted and ready.

When I open Rhythmbox the music doesn't disappear in front of my eyes, like it would on a drive that's not mounted, I open it and it's already gone!!         

I have had Rhythmbox detect my music from the same place on previous installs without problem.

I'm going to have to use Banshee for now which is a shame because I've always liked Rhythmbox.

If anyone has any other ideas please help!

Thanks again!

---

### Post by pluckypigeon on 2008-12-08
I think it was to do with hard disk space.

I freed up about 30GB of space and now Rhythmbox seems to be fine!

---

