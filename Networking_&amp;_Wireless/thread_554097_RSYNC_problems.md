---
title: "RSYNC problems"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by revelation.now on 2007-09-18
Hi all. I hope someone can help on this. I've just been running into rsync problem after problem. I hope they all stem from the same issue, but heres the main bug I'm having problems with.

I've set up cygwin on a few wintel PCs which seems to be accepting incoming SSH requests, at least, on their IP. THeir host names don't seem to be wrapping to the service yet, but anyway.

I've started an rsync session with something like
```
rsync -rt --delete -verbose --compress --progress --rsh=ssh user@ip:/cygdrive/e/ISO/ /home/user/Backup/ISO/ >> rsync.log
```

Transfer seems to connect and asks for a password. Then it starts listing files, then problems begin. It seems to want to do one extra thing each time I launch it then hangs.

Before it hung on 
17451 files to consider

then it hung on 

17451 files to consider
./

after another ctrl+c I got

17451 files to consider
./
000c9959.key

now

17451 files to consider
./
000c9959.key
32bisx.exe

it has in fact now copied that key file and the exe across, and its built all of the directories, it just wants to have its hand held for the rest of the way and I kind of don't think this is how its meant to work.

I did manage to rsync a 2.64mb directory fine. its anything over 1gb that seems to kill it

(oh, also pauses during file transfers if the file is big)

I Should also point out that the network is only 100Mbit but is all wired up and typically doesn't experience packet loss or file transfer issues, so I dont want to consider that as an option just yet because I would be seeing bugs in more places

---

