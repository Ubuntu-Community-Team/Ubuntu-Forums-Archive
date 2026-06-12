---
title: "Torrents"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Elfo33 on 2008-12-04
So, I have quite a few torrents from the Windows side that I'd like to keep seeding.  I currently have them set up in a specific folder format, such as

```

/media/disk/Folder/1
/media/disk/Arcade/2
etc
```

However, when I try to download the torrent file, Trasnmission and Vuze (Azureus) seem to insist on putting them into a folder named after the torrent file.  So for instance, if I download X.torrent and Y.torrent, then start the process, it goes into

```

/media/disk/Arcade/1/X
/media/disk/Arcade/2/Y
```

As this keeps happening to me with both Transmission and Vuze, *how do I convince my machine not to download to that extra folder?*

---

### Post by hyper_ch on 2008-12-04
you could use rtorrent. You can specify for each torrent where the actually data shall be put to...

however, as you said that is from your windows setup, I assume you use ntfs.. not sure if rtorrent plays nicely when storing stuff on ntfs.

---

