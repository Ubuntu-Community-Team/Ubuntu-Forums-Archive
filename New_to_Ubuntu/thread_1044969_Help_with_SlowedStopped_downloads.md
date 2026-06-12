---
title: "Help with Slowed/Stopped downloads"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Rogue Yun on 2009-01-20
I Use Ubuntu 8.10
I have a wireless 5xxx Atheros 802.11 card that I recently got working.
If you need any other information please let me know and I'll do my best to provide it.

When I try to download updates, or something from "Add/Remove...", "Synaptic Package Manager" or even in terminal, I get about a 30% Success rate.  The other 70% my 60kb/s goes to 300B/s and/or stops.  This is a very frustrating problem.  Any help I can receive on this would be much appreciated as I have searched for a solution for a couple days in my spare time and have come up with nothing.  Thank you, in advance.

Craig

---

### Post by diablo75 on 2009-01-20
Probably has nothing to do with your wireless adapter or network, and more to do with the specific servers you're getting your updates from.

Try this:

Click System>Administration>Software Sources.

Enter your password.

Look for the "Download From: [some server name is here]" box.

Click on that box, and it will open up.  Click on Other...

The server I prefer to use (because it's almost always lightning fast) is the [http://ubuntu.osuosl.org/ubuntu](http://ubuntu.osuosl.org/ubuntu) within the United States listings.  But if you live somewhere else you should browse to try and find a server that's close to you.

Alternatively, at this point, you can click on a button that says Select Best Server.  This will ping them all and pick the one that replies quickest.  After you select a different server and click Close, you'll have to click the Reload button.  Once this is all done, try applying your updates again.

---

