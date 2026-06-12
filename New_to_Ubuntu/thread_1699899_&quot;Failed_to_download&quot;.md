---
title: "&quot;Failed to download&quot;"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by abnordude on 2011-03-04
When I start downloading from the ubuntu software center [any software], it starts installing. But when it reaches a part where it says "Applying Changes", it suddenly stops and a message is displayed
"Failed to download packages. Check your internet connection"
But my internet connection is alright.
Please help me.



P.S: It only happens for certain downloads. Not all.

---

### Post by turtle153 on 2011-03-04
What are you trying to install? Can you post the output of```
sudo apt-get install [softwarename]
``` (replacing the bit in [brackets] of course :p)

---

### Post by janpol on 2011-03-04
Try changing the server where you are getting your software from. Open the software center and go to Edit>Software Sources. Over there choose to download from the Main Server, close that window and wait for the cache to be reloaded. Now try again.

Good Luck!

---

### Post by abnordude on 2011-03-04
> **janpol said:**
> Try changing the server where you are getting your software from. Open the software center and go to Edit>Software Sources. Over there choose to download from the Main Server, close that window and wait for the cache to be reloaded. Now try again.

Good Luck!

I think that was the problem, now it's installing.
Thank you guys.

---

