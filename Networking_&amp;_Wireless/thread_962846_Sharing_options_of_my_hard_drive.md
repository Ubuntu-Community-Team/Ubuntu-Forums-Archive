---
title: "Sharing options of my hard drive?"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by the lemming on 2008-10-29
Could somebody please tell me how I can share my ubuntu drive or Home partition with my Vista computer?

When I click on the home folder and choose Sharing Options and follow all the options I end up with the error message

Could not change the permissions of folder "home"

So far things are a oneway street where I can access my Vista box from my ubuntu puter but I can't do things the other way round.

Cheers

---

### Post by dmizer on 2008-10-29
The /home directory is owned by root, so you cannot share it. Leave it this way, it's necessary for correct system operation.

You should share your user directory from within the home directory, or (even better) specific folders inside that.

So, share /home/the-lemming, /home/the-lemming/Public, or /home/the-lemming/Videos

As a side note, it's not a good idea to share your entire user directory, as it contains a huge amount of hidden configuration files. It's preferable to share a specific folder inside your user's home directory.

---

### Post by the lemming on 2008-10-30
Thanks for the useful advice on where I was going wrong.  With that in mind I'm assuming that once I get to myuser directory then I simply click and follow the Sharing instructions?

I'm on a vista box at the moment so I can't test this theory.

Cheers

---

