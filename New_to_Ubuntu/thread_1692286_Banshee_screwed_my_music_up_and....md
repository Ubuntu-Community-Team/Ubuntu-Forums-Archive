---
title: "Banshee screwed my music up and..."
date: 2011-02-21
forum: New to Ubuntu
---

### Post by mikee55 on 2011-02-21
..keeps crashing my PC, I'm having to reboot. Videos play slow as well. I'm back to movie player, when I select files to play, it plays them twice, and I have skipping and jumping. Banshee has separated all my music out of categories and created individual artist folders. I have, say, an Ambient folder, its been pulled apart and all the tracks are now in separate folders. How do I reverse that?

Peed off
Mike:confused:

---

### Post by wyth on 2011-02-22
Under the Edit > Preferences > General tab, there are a few boxes you can tick:
[LIST]
[*]Copy files to media folders when importing
[*]Write metadata to files
[*]Write ratings and play counts to files
[*]Update file and folder names
[/LIST]

Those seem to cause a lot of trouble. You can manually import media, so there's not much point to having it do so automatically unless you import regularly. Writing metadata has been buggy and runs the memory into overload, stalling the app. What you probably had trouble with was updating file and folder names -- that option lets Banshee organize your data however it sees fit. 

For some reason, it can't ever seem to get that right. In my case, it's often renamed songs as Unknown and throws them into an Unknown folder, even after fixing the metadata. It's also deleted scores of data when trying to fix metadata when that feature is enabled.

There's also the Library Watcher plugin. It should just see if new data is present. That tends to work okay, but on one of my machines, it constantly drags any and all video files from anywhere into the Video directory, which is really annoying and eats up space fast. 

So you may want to un-tick those options in the General tab, check the plugins and remove those you don't use, or consider a different application. Banshee has been running into all kinds of little niggling issues for well over a year now, but instead of fixing those bugs, they've been more focused on adding new features, which introduces more bugs.

---

### Post by DeviantGuy on 2011-02-22
If Banshee is bug-o-tastic. I might just be sticking to Rhythmbox.

---

### Post by wyth on 2011-02-23
> **DeviantGuy said:**
> If Banshee is bug-o-tastic. I might just be sticking to Rhythmbox.

Yip. I only ever wanted music and podcast management. Banshee's podcast management is miles beyond Rhythmbox's, so I just use gPodder now for podcasts and Rhythmbox for music.

---

### Post by k4nz4k1g4w4 on 2011-08-22
@ wyth Thanks for a very very helpful post. After pulling my hair out I wished I'd seen it sooner! Banshee developers should employ you, if they don't already.

---

