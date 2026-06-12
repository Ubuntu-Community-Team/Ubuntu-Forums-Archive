---
title: "Transmission torrent restart problem"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by spai on 2010-10-17
Hello all,

I have a very jittery internet connection (that is it randomly fluctuates on and off). So I have the habit of switching my computer off for some time and then restarting it. When I restart my hard drives are not automatically mounted and often I forget to immediately mount my hard drives. Now, when I start Transmission (a bit torrent client) and the hard drives are not mounted, Transmission can't locate my files. So I mount my drives then. 

However the problem is that instead of resuming the download, Transmission restarts the download!! How do I make my transmission to resume downloads?


Thank you,
Spai

P.S: The internet connectivity problem seems to be OS related... Only in Ubuntu, I have to logout and login to get my connection back!Any help here is appreciated as well :)

---

### Post by TeoBigusGeekus on 2010-10-17
1)About the internet connection: is it wired or wireless?
2)You should make your partitions mount on startup, in order to avoid this sort of thing. Search for [fstab]("http://ubuntuforums.org/showthread.php?t=283131").

---

### Post by spai on 2010-10-17
> **TeoBigusGeekus said:**
> 1)About the internet connection: is it wired or wireless?

Wired.

> **TeoBigusGeekus said:**
> 2)You should make your partitions mount on startup, in order to avoid this sort of thing. Search for [fstab]("http://ubuntuforums.org/showthread.php?t=283131").

Yes I should and I shall do it now. However I dont want to redownload files that I have already downloaded. So is there a fix for it?

---

### Post by TeoBigusGeekus on 2010-10-17
Hmm...
Check whether you can import them with another torrent client (deluge, vuze,etc.)
Otherwise, I think they're lost... sorry.

---

### Post by mister_playboy on 2010-10-17
> **spai said:**
> However the problem is that instead of resuming the download, Transmission restarts the download!! How do I make my transmission to resume downloads?


You need to use Force Recheck so that Transmission will examine the file and pick up where it left off.

There is no way to automate this process that I know of, and other torrent programs have the same behavior in this situation (client is running but the file in progress cannot be found)

If you run torrents from an external drive, make sure it is mounted before starting the client to avoid headaches.

---

### Post by amjjawad on 2010-10-17
ALL my HDDs/Partitions are not auto-mounted and I have no problems with Transmission at this very moment. I'm not sure whether this problem will happen in case of restart or not because I don't turn my PC off (usually). Perhaps I should try that and see what will happen.

As for the internet connection, I always lose the connection ONLY when I use Hibernate in Ubuntu. When I turn the PC on, I can't connect to the wireless connection unless I restart my PC.

---

### Post by lazyworkhorse on 2010-10-17
> **mister_playboy said:**
> You need to use Force Recheck so that Transmission will examine the file and pick up where it left off.

There is no way to automate this process that I know of, and other torrent programs have the same behavior in this situation (client is running but the file in progress cannot be found)

If you run torrents from an external drive, make sure it is mounted before starting the client to avoid headaches.

I had an issue where Transmission would attempt to recreate lost torrents and create a drive volume almost identical to the original. The solution was to get rid of the duplicate "drive," and force recheck the correct volume.

---

### Post by spai on 2010-10-17
> **lazyworkhorse said:**
> I had an issue where Transmission would attempt to recreate lost torrents and create a drive volume almost identical to the original. The solution was to get rid of the duplicate "drive," and force recheck the correct volume.

Yes! I have the exact same problem. I actually got pretty irritated with Transmission and uninstalled it. I also deleted all the files I had semi-downloaded (just now :sob: ). I could have tried your method lazyworkhouse... shucks....

Currently trying Ktorrent and Deluge. But they have their own problems :mad:

---

### Post by DavidG24 on 2011-03-02
I'm sure you have probably already solved the issue, but I thought I would reply just in case.

The reason why Transmission restarts the download is that when it reloads the torrents it doesn't recognise the incomplete files as they are amended with a .part extension. This is something transmission does until the file is finished downloading, to stop it from doing this, (open transmission of course) go to Edit --> Preferences and in the 'Torrents' tab, until Downloads uncheck 'Append ".part" to incomplete files' names'

Now when transmission restarts, it will scan the file and see how much has been d/led and then resume from where it should...

or at least I hope, if this doesn't work, please let me know if you find a solution, as I've had this problem before, and this is how I fixed it.

Cheers,

David

---

