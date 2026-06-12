---
title: "Spotify for Linux"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by peakshysteria on 2010-07-16
Finally Spotify is available for Linux. I was thrilled to see the following: [http://www.spotify.com/no/download/previews/]("http://www.spotify.com/no/download/previews/")

I installed it right away. After some minor problems I got it up and running. It plays fine. All my lists came up. Even some my peoples list worked. This haven't worked on my **Wine-Spotify**.

I haven't tested it fully yet because of one big problem. I can't seem to find out where Spotify is located on my system. Therefore I start Spotify from terminal. Every time I go to **--> Edit --> Preferences --> Spotify** chrashes! So I'm not able to add my last.fm account or my music library. Any one have a fix for this?

Update:

1. After trying prefrences five times I suddenly made it. I put in my Last.fm username and password. But the client doesn't seem to scrobble.

2. Trying to import local files failed.

3. Now Prefrences are unavailable again.

4. Still now menu entry or icon for Spotify.

---

### Post by silentrebel on 2010-07-16
To start, you might want to run the following in a terminal:
```
find / spotify 
```

The output might be a little lengthy, so don't be afraid to send it to a file too peruse it all there:
```
find / spotify > ~/Desktop/spotify.search
```

If you have a second or third (or more...) keyword you a looking for, you may easily use grep to narrow your search:
```
find / spotify | grep -i <keyword2> | grep -i <keyword3> | ... | grep -i <keywordn> > ~/Desktop/spotify.search
```

I hope that gets you started,
Nuagerebelle

---

### Post by peakshysteria on 2010-07-16
Thanks man. But no cigar (tried both suggestions. After going through all discs I get:

> find: `spotify': No such file or directory

And Spotify under Wine scrobles fine. The linux client still don't.

---

### Post by silentrebel on 2010-07-16
You might try adding *-iname* right before spotify in the find commands I gave you earlier...  This ignores case, in case that helps...

Also, what command do you use to get spotify to run from the command line?
Nuagerebelle

---

### Post by da burger on 2010-07-16
A couple of things, once you have the command that you use to start up spotify, run ```
which spotify
```(or whatever the command you use to start spotify with is) which will tell you it's exact location (which you wanted to know for some reason).

The page you linked to said local music is not yet supported.

However as they said it's a "preview" release. Your going to have to take the rough with the smooth and report problems to them when you find them, not us.

(Thanks for bringing my attention to this though)

Angus

---

