---
title: "Is Googlebot going to find this directory?"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by adamjkok on 2010-10-06
After losing my flash drive and needing a way to easily keep my music files with me at school (my animation teacher is really cool and lets us listen to music on our headsets), I decided to hide a music directory among one of my vhosts on a nonstandard port. How can I keep Googlebot from finding this? It's well hidden and not on port 80. Am I already protected? I don't wanna get in trouble for sharing copyrighted music or wind up serving thousands at a time with a 10-year-old server by letting Googlebot find it, but I don't wanna mess with authentication for this directory (I might also wanna let a few close friends on).

---

### Post by robsoles on 2010-10-07
Provided you never expose a link to it, Googlebot will not 'stumble upon' it.

The primary way Googlebot finds anything is by finding a link to it in something else it already knows about. A secondary way is by someone submitting it for inclusion in Google's index at which point it is fed to the crawler using a different method.

It is likely one (or more) of your friends will effectively betray you by exposing a link to it publicly or in a lesser way by personally inviting some of their other friends to hit your server for some music.

Not being served on port 80 is no guarantee that Googlebot won't 'look' at it if someone links to it publicly or if it is submitted by someone.

robots.txt is an effective enough way to keep your music files out of Google's index (search results).

Assuming the hostname and port is example.com:90 and the folder you've put the music into is ./hidden-music the file at [http://example.com:90/robots.txt](http://example.com:90/robots.txt) should read
```
User-agent: *
Disallow: /hidden-music
```

If robots.txt already exists then add the second line above below the existing instance of the first line above (add both lines if 'User-agent: *' line isn't there).

HTH

---

### Post by jtarin on 2010-10-07
Don't put your fingerprints on it.

---

