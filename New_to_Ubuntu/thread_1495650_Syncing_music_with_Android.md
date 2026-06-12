---
title: "Syncing music with Android"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by Zenze on 2010-05-28
So I just got a Android based phone and I think its great except for one thing. I was hoping to use it as my music player and replace my iPod, which managing my iPod is also the main reason that I still ever boot into Windows. The only thing is I can't really figure out a good way to sync music to it.

I wrote a small flex program to take all my playlists that are on iTunes and convert all the file paths so that they work correctly on my Ubuntu side. However, syncing these playlists to the phone is a whole other story. Rhythmbox will throw all the music files on there but thats not really what a I want, I need the playlists on there.

Anyone know of a good way to do this?

---

### Post by Brandon Williams on 2010-05-28
I've got scripts that I use to generate .m3u playlists, so I don't know if there's an easier way to do this with a common GUI application, but ...

If you mount the phone and create the directory /media/Music/Playlists, where "media" is whatever mount-point Ubuntu used for your phone, you can simply drop standard .m3u files into that directory and they will be picked up automatically by the Music app on your phone.

If you haven't used them before, an .m3u file is simply a listing of .mp3 files. I generally specify the full path to the .mp3 file so they're easier to move around if I want to, but you might be able to specify a relative path, too. The base directory for the sdcard when it's mounted on the phone is /sdcard/. If you have your tracks in the Music directory on the sdcard and you have a directory for each artist with a subdirectory for each album (as I do), then the .m3u file might look something like this:
```
/sdcard/Music/artist1/album1/track1.mp3
/sdcard/Music/artist1/album1/track2.mp3
/sdcard/Music/artist1/album1/track3.mp3
/sdcard/Music/artist1/album2/track1.mp3
/sdcard/Music/artist2/album1/track5.mp3
/sdcard/Music/artist3/album4/track6.mp3
etc...
```

If relative paths work, it might be possible for you to get rhythmbox to generate .m3u file for you based on playlists that are already defined in rhythmbox.

---

