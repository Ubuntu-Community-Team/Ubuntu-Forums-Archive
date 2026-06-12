---
title: "Wifi won't say connected"
date: 2014-12-18
forum: Networking &amp; Wireless
---

### Post by frequark on 2014-12-18
Hello. Just migrated from Windows and hit my first problem. I got a USB wifi adapter that works splendid, has great connectivity. How ever on Ubuntu it will stop working every 5 minutes or so. It's not an exact amount of time, sometimes longer, sometimes shorther.

When internet stops working it doesn't say "disconnected" or anything. It simply no-longer works, and I have to click "disconnect" and then connect again. 

Here's some sort of a log file made by some script I found in another thread with similar issue, but didn't find a solution. 

[http://pastebin.com/raw.php?i=S8LvXkYL](http://pastebin.com/raw.php?i=S8LvXkYL)

Nothing in the router log files.

---

### Post by frequark on 2014-12-18
Well I went to Edit Connections, deleted the Wifi connection that was automatically created, then manually made the exact same one and looks like it's staying up. Odd stuff.

And after my brand new install came to a freezing halt (very heavy cpu usage, mouse barely moving) I had to restart and it's broken again.

---

### Post by Bucky Ball on 2014-12-18
Welcome. In the connection you setup manually in Network Manager, do you have IPv6 set to 'ignore'? Check that tab.

Under the General tab, do you have 'Automatically connect to this network' and 'All users may connect to this network' ticked?

---

### Post by frequark on 2014-12-18
IPv6 has been on automatic. I did switch it to ignore on the default setup, but the issue persisted, so I switched it back.

After I restarted I tried to create a new connection again and delete the old one, but this time it didn't fix it. 

Yes both of the things you mentioned are ticked.

---

