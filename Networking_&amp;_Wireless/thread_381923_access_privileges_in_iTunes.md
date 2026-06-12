---
title: "access privileges in iTunes"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by Sturm on 2007-03-11
Now that Samba is fully working, I have moved all of my music from the old NTFS partition to the native ext3 partition so that I can share it on the network.  I've set it to share, gave it full read, write, & execute privileges (as far as I can tell), and I can now see it on my Windows systems.

On those Windows boxes, I've deleted the old mapped drive (since it's no longer connected, anyway), and mapped the new Ubuntu-shared music folder to the same old drive letter.  That way, I don't have to change iTunes' setup.

However, it seems like iTunes refuses to download podcasts now.  When I try, I get an exclamation mark beside the episodes that, when clicked on, gives me the message:

> There was a problem downloading "x".  You do not have enough access privileges for this operation.  Please check that the URL is correct and the connection to the network is active and try again.

It sounds as though the shared folder on Ubuntu is not allowing me write to it, even though I set it that way, I thought.  Or maybe it has something to do with downloading.  I don't know.  I'm just a newb.  Please help?  Thanks.

---

### Post by Sturm on 2007-03-12
Eureka!

Turns out that, although I had permissions set correctly on the /home/<myname>/mp3 folder, I had not set permissions on the parent /home/<myname> folder.  Thus, I guess it was overriding the permissions on the mp3 folder inside it.

Ran it through after changing that and it worked!

I'll be adding a 500GB hard drive soon and mount it as /media, after which I'll move all my music and such over there.  Is there anything I should know in advance before I add this new HDD?  Would it be advisable to just do a clean install of Ubuntu?  Thanks, and take care!

---

### Post by Sturm on 2007-03-21
*sigh*  Back to the drawing board

Okay, I got my new 500GB hard drive working wonderfully on the Ubuntu system.  I split it up into several partitions and mounted each one to a separate folder under /media.  One of them is /media/music, where I have all of my MP3s.

This is also where iTunes on my Windows systems plays music.  I've set the permissions on both /media and /media/music to be drwxrwxrwx, yet I still cannot download new podcasts.

The strange thing is that it was downloading them fine yesterday!  After I restarted the Samba daemon, I was able to download new podcasts to that shared folder on my Ubuntu box.  Today, however, I am suddenly unable to do so, getting that same "You do not have enough access privileges for this operation" message.  And restarting Samba doesn't help this time.

Let me know if I need to post my smb.conf file or any other information if it will help in troubleshooting this odd problem.  Thanks!

---

### Post by Sturm on 2007-03-22
Guess I should create a blog, eh?  "The trials and tribulations of Ubuntu."

Kept on tinkering with permissions and restarting Samba each time.  Nothing seemed to work.  Last ditch effort--change "writable = ok" in the /etc/samba/smb.conf file to "writeable = ok".  Bingo!

Always seems like it's the last ditch efforts that do the trick, doesn't it?  Well, things are back on schedule now with iTunes, so let's just hope it STAYS that way this time and won't revert back to its evil roots.

If it does, I'll throw it out and just use Rhythmbox to manage my library and sync with my iPod.  Then I'll just need to find a way to sync podcasts to it as well.  Take care, all!

---

