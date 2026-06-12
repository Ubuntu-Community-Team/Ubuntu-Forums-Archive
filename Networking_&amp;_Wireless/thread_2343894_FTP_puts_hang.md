---
title: "FTP puts hang?"
date: 2016-11-20
forum: Networking &amp; Wireless
---

### Post by w9wi on 2016-11-20
I'm having trouble with outgoing FTP transfers hanging...

For my website, I compile a few directories (nine) of static HTML files (roughly 100 per directory).  Files are of modest size; the smallest is a bit more than 100 bytes, the largest around 400k.  I'd say about 30k on average.  Overnight, a script triggered by cron uploads those files to my hosting provider.

After transferring some random number of files -- between ten and maybe 80 -- the transfer will hang.  Nothing will happen for 2-5 *minutes*.  

I'd been using YAFC as my FTP client.  (mainly because I couldn't immediately figure out how to login from a script when using the plain old FTP client that comes with Ubuntu)  YAFC has a 42-second timeout which (best I can tell) cannot be extended - so random parts of my site weren't getting updated.  When I switched back to the "plain old FTP client" it does resume the transfer once the several minutes' delay finishes -- and it DOES successfully transfer the file it was transferring when it hung.

It's not related to network traffic.  (I've been watching it occasionally hang in the other window while I navigate ubuntuforums.org, Facebook, cbc.ca, and the National Weather Service -- all of which are behaving just fine)  I see no correlation between the size of the file being transferred and the chances of it stalling.  If I had to wild-guess I'd say I'm filling a buffer on the other end.  Would like to insert a second or so pause between files but I don't see a way to do that?

I suppose it's not the end of the world if I can't fix it -- the script runs overnight & if it takes an extra hour to complete due to hangs, I'll sleep right through it:)  But it might be nice to be able to use YAFC again -- or at least to know what's going on.

Thanks!

---

### Post by TheFu on 2016-11-20
Plain FTP is so, so, so ... 1995. 
Should be using rsync over ssh these days.

$ rsync -avz /path/to/source/ id@remote-server:/path/to/website/

rsync uses ssh by default.  If your provider doesn't support ssh, fire them. They clearly don't care about security OR your business.

---

