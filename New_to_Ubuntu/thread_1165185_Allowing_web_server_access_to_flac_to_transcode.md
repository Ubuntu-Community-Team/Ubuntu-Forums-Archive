---
title: "Allowing web server access to flac to transcode"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by NDPeter on 2009-05-20
Whether you can tell from the title of the thread or not, I think I have a problem that involved my web server being able to run flac.  

I've used ampache for a year now, but recently added some albums in flac and the ape format.  It's always handled my mp3 and ogg files just fine for transcoding and downsampling.  from what I've figured out, it'll be easiest to convert the ape to flac.  But I also have figured I should be able to get ampache to play nice with the flac files and I haven't yet.

I have 'flac' installed from the package manager.  In the ampache config file is mentions that any programs needed to transcode need to be in the web server directory or executable by the web server.  So I'm guessing that's my issue, but I don't know how to check if those are the case or not.

Any help on how to install something where you webserver can run it?  I'm pretty sure I don't want to make everything accessible to read and write by everyone.  Thanks.

---

### Post by NDPeter on 2009-05-20
The specific bit in the ampache.cfg.php file that caught my attention...

```
These are commands used to transcode non-streaming
; formats to the target file type for streaming. 
; This can be useful in re-encoding file types that don't stream
; very well, or if your player doesn't support some file types. 
; This is also the string used when 'downsampling' is selected
; as some people have complained its not bloody obvious, [B][I]any programs
; referenced in the downsample commands must be installed manually and in
; the web server path, and executable by the web server[/I][/B]
```

---

