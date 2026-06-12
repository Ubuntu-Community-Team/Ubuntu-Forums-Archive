---
title: "Flash refuses to work in firefox."
date: 2010-12-05
forum: New to Ubuntu
---

### Post by Jadrian on 2010-12-05
I'm about to pull my hair out! (well, what's there) Installing a ubuntu minimal install last night, and loaded up xfce4 onto it, I looked down upon my creation and it was good...  
However, flash works perfectly fine in Chromium but doesn't in firefox.

I'm tried installing it from xubuntu-extras... didn't work, tried installing from a tar.gz... didn't work, tried installing straight from the browser... didn't work and even from a PPA.

But none of them work, firefox just acts as if they were never installed, telling me I need to download flash... 

Could someone help me please?

---

### Post by migs73 on 2010-12-05
Firefox can get it's knickers in a twist with all the stuff trying to run flash content.

Try the Flashaid add-on for firefox, it sorts them all out and should get your flash going.

---

### Post by Jadrian on 2010-12-05
Tried that already, just did it again for good measure though, youtube still won't load however, it's telling me I need to upgrade my flash. Hmm...

---

### Post by migs73 on 2010-12-05
I am afraid Flashaid is my trump card when it comes to flash problems.:(

I hope someone else can help you out.

---

### Post by Jadrian on 2010-12-05
Got it working! :D
/usr/lib/mozilla permissions were all fudged and would only let my root account access it. Just fired up gksu thunar and changed it.

---

### Post by migs73 on 2010-12-05
Glad you got it working. Could you please mark the thread as solved.

(Hint; Goto the top of your first post, click on the Thread Tools and select 'Mark as Solved')

:)

Mike

---

