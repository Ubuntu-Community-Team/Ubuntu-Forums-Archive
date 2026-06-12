---
title: "Possible to Mirror Local Directory to Networked Drive?"
date: 2022-09-12
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2022-09-12
I run Lightburn in a wine VM on my laptop. I have another laptop (running windows) that also runs Lightburn to control the laser. I have a folder on my networked drive that I share with laptops so that I can create the projects on one and burn them with the other. If I set both instances of Lightburn to use the same shared directory, not only does it slow things down, sometimes Lightburn doesn't want to read/write files correctly directly from/to the networked drive. To avoid that, I have a directory on my main laptop in which I work and then copy the files to the networked drive for the laser's laptop to access. This gets old. 

My question is... is there any way that I can mirror the local directory (under Ubuntu) to the networked drive automatically? It doesn't have to be in real time, but every so often would be good. 

Thanks.

---

### Post by Tadaen_Sylvermane on 2022-09-12
rsync would be good for this. something like this would work over ssh.

```
rsync -auv --progress /source/folder user@target:/target/folder
```

no need for the -v or --progress if it's run from cron I guess.

---

### Post by rebeltaz on 2022-09-12
I'll give that a try. I guess if no changes have been made, nothing will be done?  Thanks.

---

### Post by Tadaen_Sylvermane on 2022-09-13
exactly. the -u flag will only sync the changed files. otherwise it will just check for differences then exit till next run.

---

### Post by rebeltaz on 2022-09-13
Oh. OK... awesome! Thank you!

---

### Post by Tadaen_Sylvermane on 2022-09-14
I know you marked as solved. You could pipe the script through inotify. It would watch for changes in the directory and only execute the rsync if it finds changes. I'm not sure how efficient one is trying to be but I think just watching for changes is less cpu cycles involved than running a full check every so often. Probably not much to be worth it, just an idea.

---

### Post by rebeltaz on 2022-09-14
> **Tadaen_Sylvermane said:**
> I know you marked as solved. You could pipe the script through inotify. It would watch for changes in the directory and only execute the rsync if it finds changes. I'm not sure how efficient one is trying to be but I think just watching for changes is less cpu cycles involved than running a full check every so often. Probably not much to be worth it, just an idea.

Yeah... I would like it to only do something if/when changes are made. How would I go about using ... inotify?

---

### Post by Tadaen_Sylvermane on 2022-09-15
[https://www.baeldung.com/linux/monitor-changes-directory-tree](https://www.baeldung.com/linux/monitor-changes-directory-tree)

That + man page should lay it out. I'd stick a sleep in the script before firing the rsync though because it may take a few seconds for whatever write or change to finish. Something along these lines. It won't try to rsync unless the ping is successful. Run on startup and away it goes.

```
while true ; do
  inotifywait -m "$SOURCEDIR" | while read line ; do
    sleep 5
    ping -c 1 "$TARGETIP" && rsync -au "$SOURCEDIR" "$TARGETDIR"
  done
done
```

---

### Post by rebeltaz on 2022-09-15
I will definitely look deeper at that. I really appreciate it!

---

### Post by rebeltaz on 2022-09-28
> **Tadaen_Sylvermane said:**
> [https://www.baeldung.com/linux/monitor-changes-directory-tree](https://www.baeldung.com/linux/monitor-changes-directory-tree)

That + man page should lay it out. I'd stick a sleep in the script before firing the rsync though because it may take a few seconds for whatever write or change to finish. Something along these lines. It won't try to rsync unless the ping is successful. Run on startup and away it goes.

```
while true ; do
  inotifywait -m "$SOURCEDIR" | while read line ; do
    sleep 5
    ping -c 1 "$TARGETIP" && rsync -au "$SOURCEDIR" "$TARGETDIR"
  done
done
```

Hey there... I finally got around to trying this tonight. I wanted to see what it would do, so I set it up temporarily as a script I could run. I made a couple of modifications and I may have been wrong? It seems to work ok, until it sees a change, then it runs rysnc, updates the target directory and then seems to be stuck in a loop. 

This is the script as I am using it:
```

SOURCEDIR=/home/rebeltaz/Desktop/Lightburn/
TARGETDIR=/mnt/multimedia/Lightburn_remote/
TARGETIP=192.168.1.15


while true ; do
  inotifywait -mr "$SOURCEDIR" | while read line ; do
    sleep 5
    ping -c 1 "$TARGETIP" && rsync -auv "$SOURCEDIR" "$TARGETDIR"
  done
done

```

I added 'r' to the inotify command because there are subdirectories under that main directory that need to be mirrored as well. I only added 'v' to the rsync command as a debug tool to find out what it was doing while it was stuck in a loop.

This is the output:
```

rebeltaz@laptop:~$ ./monitorLightburn.sh 
Setting up watches.  Beware: since -r was given, this may take a while!
Watches established.
PING 192.168.1.15 (192.168.1.15) 56(84) bytes of data.
64 bytes from 192.168.1.15: icmp_seq=1 ttl=64 time=2.11 ms

--- 192.168.1.15 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 2.111/2.111/2.111/0.000 ms
sending incremental file list
./
artwork/
control.software/
control.software/LaserGRBL/
control.software/Lightburn/
fonts/
libraries/
projects/
projects/3D Wooden Letter Box with living hinge/
projects/R2D2/
projects/RebelDesigns/
projects/vintage_borders/

sent 22,681 bytes  received 494 bytes  3,565.38 bytes/sec
total size is 1,053,349,199  speedup is 45,451.96
PING 192.168.1.15 (192.168.1.15) 56(84) bytes of data.
64 bytes from 192.168.1.15: icmp_seq=1 ttl=64 time=2.05 ms

--- 192.168.1.15 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 2.052/2.052/2.052/0.000 ms
sending incremental file list
./
artwork/
control.software/
control.software/LaserGRBL/
control.software/Lightburn/
fonts/
libraries/
projects/
projects/3D Wooden Letter Box with living hinge/
projects/R2D2/
projects/RebelDesigns/
projects/vintage_borders/

sent 22,681 bytes  received 494 bytes  2,726.47 bytes/sec
total size is 1,053,349,199  speedup is 45,451.96
PING 192.168.1.15 (192.168.1.15) 56(84) bytes of data.
64 bytes from 192.168.1.15: icmp_seq=1 ttl=64 time=1.87 ms

--- 192.168.1.15 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.878/1.878/1.878/0.000 ms
sending incremental file list
./
artwork/
control.software/
control.software/LaserGRBL/
control.software/Lightburn/
fonts/
libraries/
projects/
projects/3D Wooden Letter Box with living hinge/
projects/R2D2/
projects/RebelDesigns/
projects/vintage_borders/

sent 22,681 bytes  received 494 bytes  3,565.38 bytes/sec
total size is 1,053,349,199  speedup is 45,451.96
PING 192.168.1.15 (192.168.1.15) 56(84) bytes of data.
64 bytes from 192.168.1.15: icmp_seq=1 ttl=64 time=1.68 ms

--- 192.168.1.15 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.688/1.688/1.688/0.000 ms
sending incremental file list
./
^C^Crsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(644) [sender=3.1.2]

```

Any idea?

---

### Post by Tadaen_Sylvermane on 2022-09-29
I screwed up I think. I don't think it's supposed to be nested in a while loop. Sorry about that. I missed that the inotify pipes directly into a while loop. Haven't used it in awhile. Apologies. This should be what's required. Notice missing the while true loop

```
[COLOR=#000000][FONT=&amp]inotifywait -mr "$SOURCEDIR" | while read line ; do
[/FONT][/COLOR]  sleep 5
  ping -c 1 "$TARGETIP" && rsync -auv "$SOURCEDIR" "$TARGETDIR"
done
```

---

### Post by rebeltaz on 2022-09-29
lol... I gotcha. That makes sense. I appreciate it. It works great, though, so I do appreciate that!

---

### Post by rebeltaz on 2022-09-30
Don't mean to be a bother, but I took that while loop out and it still seems to be stuck in a loop once it's triggered.

---

### Post by Tadaen_Sylvermane on 2022-09-30
It is. Inotify is a perpetual process. It keeps going. As things happen in the target directory it will spit out a line for each change, that is what fires the rsync. it will then wait for the next line to fly by.

---

### Post by rebeltaz on 2022-09-30
What I meant was that when I run the script, it sits there minding it's own business, like I would expect, but once a file is created or modified in the watched directory, it runs rsync which I expect. But then, from then on, until I kill the script, it continues to run rsync again and again. The output that I gave originally, with the repeated "sending incremental list" text... that's still what's happening now, even without the additional while loop. Surely that's not the expected behavior, right?

---

### Post by Tadaen_Sylvermane on 2022-10-01
No it's not... It should run the rsync then only fire again when inotify picks up another change. That doesn't make sense. I'll mess with it a bit and see what happens.

---

### Post by Tadaen_Sylvermane on 2022-10-02
[SIZE=2]Ok. I'm sorry for taking awhile, life is endlessly annoying.

The problem is the lack of specifics.  Excerpt from man page. I'm unsure of what all it is registering as changing but it is working as supposed to. You just need to limit it's triggers. In my test case just now I used create and moved_to. If you use the delete flag along with adjusting the rsync like so....

```
rsync -auv --delete "$SOURCE" "$TARGET"
```

Then it will remove the stuff from the target that has been removed from the source.

[/SIZE]```
[SIZE=2][B]-e <event>, --event <event>
[/B][/SIZE][SIZE=2]Listen for specific **event**(s) only. The events which can be listened for are listed in the **EVENTS** section. This option can be specified more than once. If omitted, all events are listened for.[/SIZE]
```[SIZE=2]

[/SIZE]

---

### Post by rebeltaz on 2022-10-02
So I just need to add a couple of limiting events to it? I'll try that tonight. Thank you! (and no worries about time... I understand completely. I just appreciate your help!)

---

### Post by rebeltaz on 2022-10-02
I just wanted to say thank you again. I added modify, create, delete and move as events and it is working great now. I also changed the sleep timer from 5 seconds to 30 because if I tried to create a new file in that directory, I would run rsync while I was renaming it and didn't see that I had changed the name. I figured a little more time to allow changes like tat to propagate couldn't hurt :) Move was needed as an event because if you "move to trash" from a gui file manager, it's seen as a move and not an actual delete, so it wasn't triggering rsync. Once again, thank you for your time and patience!

---

