---
title: "Is there a way to make the &quot;find file&quot; search actually work?"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-06-20
and not take over an hour to find a file? Is there something I can get from the repos to build a search index kind of like how synaptic builds one for the quick search?

---

### Post by Pollox on 2010-06-20
You could try "locate" in terminal.

---

### Post by themusicalduck on 2010-06-20
I use Tracker for search. It keeps an index of files so it gives a near instant result.

---

### Post by Legendary_Bibo on 2010-06-20
> **themusicalduck said:**
> I use Tracker for search. It keeps an index of files so it gives a near instant result.
I got it but it doesn't do anything, it doesn't seem to be building an index, or do I have to do it?

---

### Post by Zip247 on 2010-06-20
> **Pollox said:**
> You could try "locate" in terminal.


As Pollox states use locate.  locate uses a db(updatedb) and is usually scheduled as a cron job every so often.

you can find more in the locate man page.

---

### Post by Legendary_Bibo on 2010-06-20
> **wdecker said:**
> As Pollox states use locate.  locate uses a db(updatedb) and is usually scheduled as a cron job every so often.

you can find more in the locate man page.

uhhhh...just tried locate in the terminal. I do not like it, I just searched a file I knew the location of and it gave me a bunch of weird things unrelated to it.

---

### Post by themusicalduck on 2010-06-20
> **Legendary_Bibo said:**
> I got it but it doesn't do anything, it doesn't seem to be building an index, or do I have to do it?

I do remember having to set it up, but it was a while ago and I just can't remember what I did..

There should be an icon in the notification area that you can right click on and change settings.

Just to check, did you install it from the Software Centre or synaptic? If you just installed the package named tracker, that doesn't install the actual search tool, just the indexer. You need to install Tracker Search Tool in the Software Centre.

---

### Post by Legendary_Bibo on 2010-06-20
> **themusicalduck said:**
> I do remember having to set it up, but it was a while ago and I just can't remember what I did..

There should be an icon in the notification area that you can right click on and change settings.

Just to check, did you install it from the Software Centre or synaptic? If you just installed the package named tracker, that doesn't install the actual search tool, just the indexer. You need to install Tracker Search Tool in the Software Centre.
Ah the website explains it very well. When you can't find the button use the terminal I always say :D.
I found the preferences, and chosed a bunch of file directories to index (I'm not sure if I could just select my home directory and have it index everything). Pretty much every folder I had except for system folders. I thought it didn't work right, but I didn't realize it was indexing, whoops silly me :D
I definitely like this better than gnome do already from using it with some of the files already indexed, thanks!

---

