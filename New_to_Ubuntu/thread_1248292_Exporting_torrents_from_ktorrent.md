---
title: "Exporting torrents from ktorrent"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by breem42 on 2009-08-24
I wanted to switch from ktorrent (3.5.10) to Transmission (1.73).  I got the software installed, and it looks like it works, but I wanted to import the torrents I had running under ktorrent.

I know ktorrent has the option of saving torrents to a directory, but that only applies to new torrents, and I did not have it checked when I started these torrents, so it's too late for that now.

I nosed around a bit and I found where the torrents are stored.  They live in directory ~/.kde/share/apps/ktorrent/tor###/ where "tor###" is one of "tor1", "tor2" "tor3" etc.  The actual torrent file is "~/.kde/share/apps/ktorrent/tor###/torrent", named exactly the same in each of these N directories.  Annoying, since there are quite a few of these buggers, all the same name, all in different directories.

So I decided to write a little script to copy all those files called "torrent" to a temp directory called "tortemp", each with their own name:

```
#!/bin/sh
mkdir ~/tortemp
for  i in `seq 999` ; do
  cp -vRTpu ~/.kde/share/apps/ktorrent/tor$i/torrent ~/tortemp/$i.torrent
done
```

Just ignore all the errors that say "cp: cannot stat ...".  BTW, I would have used something like "for (( i = 0; i <= 999; i++ ))", but kept getting "Syntax error: Bad for loop variable".

I'm a real noob when it comes to shell scripts, but it worked.  I ended up with a directory full of files called "1.torrent", "2.torrent" etc. Transmission imported those torrents perfectly.  Of course any other torrent software should be able import these torrents too.

**WARNING:** Because I was seeding many the torrents when I switched to Transmission, I told Transmission to save the files it downloaded to the same directory as ktorrent was using (for me that was "~/Downloads"), but Transmission assumes that any torrent it loads has not yet been started -- and starts downloading from scratch.

To avoid this, go to the "All" tab, select all listed torrents (i.e. press "Ctrl-A") right click and select "Verify Local Data".  This has to be done quickly, otherwise you may lose some of the data you have already downloaded.  (Am I right on this?)

This verifying can take a long time, depending on how many torrents you have.  And for some reason Transmission did not start verifying all of the torrents I selected properly, and I had to fiddle with it a fair bit to get everything right.  YMMV.

All in all a pleasant bit of fun :).

---

### Post by lukjad on 2009-10-11
Nice tutorial. I was wondering if this was possible to do. :)

---

### Post by shved on 2013-03-03
I think, the better way is:

```
#!/bin/shDEST_DIR=$HOME/torrents


if [ "$#" -ge "2" ]
then DEST_DIR="$1"
fi


if ! [ -e "$DEST_DIR" ]
then mkdir -p "$DEST_DIR"
fi


cd $HOME/.kde/share/apps/ktorrent/


TORRENT_LIST=


if [ -e tor0 ]
then TORRENT_LIST="$TORRENT_LIST tor?"
fi


if [ -e tor10 ]
then TORRENT_LIST="$TORRENT_LIST tor??"
fi


if [ -e tor100 ]
then TORRENT_LIST="$TORRENT_LIST tor???"
fi






for  i in $TORRENT_LIST ; do
  cp -vRTpu $i/torrent $DEST_DIR/$i.torrent
done 
```

---

### Post by Stonecold1995 on 2013-05-01
Is there a way to adapt this to import to rTorrent from KTorrent?

---

### Post by oldos2er on 2013-05-01
Old thread closed, please start a new thread.

---

