---
title: "Firefox bookmarks problem."
date: 2009-05-21
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-05-21
So, I am having a really strange problem concerning firefox and dropbox.

As anyone who has used those services knows you can use dropbox to backup things up, but sometimes it has trouble recognising the newest version of a file. This I believe is my problem. Here is the scenario.

1. A bookmark is created in firefox.
2. I close firefox
3. Re-open firefox and the bookmark dissapears.

As I can't imagine this being anything else I am inclined to think that it is related to dropbox and it doing some weird synchronisation.

I initially had symlinked the "bookmarkbackups" folder from the firefox profile into dropbox, but I realised that this may be causing problems, so I deleted it.

Then a folder kept appearing in a sub-directory in my dropbox folder called "Firefox" inside which the bookmarkbackups kept appearing.

Any thoughts?

---

### Post by abhiroopb on 2009-05-29
So I managed to fix part of this problem. The magic folder (Firefox) appearing in my Dropbox folder was due to a cron job that I had forgotten to delete. Howevever, I still have a cron job every three hours copying my firefox folder into a "Configbackup" folder in dropbox. This allows me to backup my firefox settings. I don't see how this could be causing my problem. Although for a while I could make bookmarks, suddenly I can't. I make them and they dissapear on restart. Its ver irritating! Any thoughts? I guess I could try and stop the backup (I use an rsync script), but I don't see how this could be affecting it, as it isn't a symlink or anything its just a copy.

---

### Post by Ms_Angel_D on 2009-05-29
Just a suggestion but why not use [Xmarks]("http://www.xmarks.com") to backup your bookmarks? It's free and a really easy way to do so. 

Wish I could help with your other issue, unfortunately I'm not sure about it.

---

### Post by abhiroopb on 2009-05-29
Its funny you mention xmarks...

I was using it for a while, and I thought my problem was being caused by xmarks! So, I got rid of it for the time being.

---

### Post by Ms_Angel_D on 2009-05-29
hmmm did you try possibly creating a new firefox profile and seeing if the problem still exists?

make sure firefox is closed completely then hit your alt+f2 buttons to bring up the run box, and in it type 

```
firefox -p
```

that will bring up a profile manager where you can create a new profile. It may just be an issue with the profile, I have had strange occurrences in the past where my profile has simply went wacky for no apparent reason.

---

