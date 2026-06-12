---
title: "Ethernet turns off with hibernation"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by upstoprail on 2010-08-14
It's my first week with ubuntu folks. Here's the main issue with Lucid Lynx:

When the comp wakes up from hibernating it doesn't recognize it's Ethernet connection (to a dsl modem).

I found that I can make it work by opening network Manager and rechecking the Enable Networking box (it always comes unchecked while the machine is shut down). Then I get a message that no network is connected (which it is of course). If I restart the comp at this point everything works.

If I restart without first checking the Enable Networking box it doesn't work

Also, I don't seem to have the option to sleep instead of hibernation. Anybody know why?

---

### Post by Iowan on 2010-08-14
From Code of Conduct:> Please use color and font properties for highlighting portions of your text, and not for all of the text in your post. The small font you chose made the post hard to read. Perhaps the person with the answer to your problem is vision-impaired. Good luck!

---

### Post by NCLI on 2010-08-14
> **upstoprail said:**
> It's my first week with ubuntu folks. Here's the main issue with Lucid Lynx:

When the comp wakes up from hibernating it doesn't recognize it's Ethernet connection (to a dsl modem).

I found that I can make it work by opening network Manager and rechecking the Enable Networking box (it always comes unchecked while the machine is shut down). Then I get a message that no network is connected (which it is of course). If I restart the comp at this point everything works.

If I restart without first checking the Enable Networking box it doesn't work

Also, I don't seem to have the option to sleep instead of hibernation. Anybody know why?
Sounds like a bug particular to your hardware. First press alt+F2, then enter "ubuntu-bug network-manager", then press enter. You will now be guided through submitting the problem to Canonicals database, Launchpad. After that, you should probably run the System Testing utility and report any irregularities found with it as well.

This won't solve your problem immediately, but at least the developers will now be aware of it. Remember to keep an eye on the bug, as you may be asked for additional information.

---

