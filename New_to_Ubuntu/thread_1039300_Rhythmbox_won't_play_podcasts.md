---
title: "Rhythmbox won't play podcasts"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by jburrell on 2009-01-14
Hi all,
I've just loaded Ubuntu 8.10 on this computer and now that I've totally gone away from Microsoft Windows I still want my podcasts.

I opened RhythmBox and selected "Podcasts" on the left of the screen. After that up on the top I selected "New" and that gave me a box for a "New Podcast Feed" in which it asked for the URL of the feed.

I cut and pasted the URL of the podcast feed (and I know it works because I just used it in MS Windows before I loaded 8.10) and this is the error message I got: "Unable to Parse the Feed Contents."

This podcast is password protected as well.

Is there any way to fix this? I read something about a "gvfs-backend," is that something applicable to this situation?

Thank you for your help...

---

### Post by Martje_001 on 2009-01-14
[http://ubuntuforums.org/showthread.php?t=969728](http://ubuntuforums.org/showthread.php?t=969728)

lopatoid says reïnstalling **gvfs-backend** works for him. Maybe you should try it also. Open up Synaptic and search for **gvfs-backend**. Right click on it and select **reinstall** and then **Apply**.

---

### Post by jburrell on 2009-01-19
I went into the Synaptic and selected the GVS Backends file for reinstallation.  I accomplished the reinstallation and still get the same error.  

The error tells me it is unable to parse the feed contents and to verify the URL.  I know the URL is good though.

What is interesting is that on my Netbook I'm still using 8.04 and I have no problems getting to the password protected Podcast, everything works just fine.

Could it be that I'm missing a file or something?

---

### Post by jbraswell on 2009-02-02
Did this ever get resolved?  I'm having the same problem.  Yes, I reinstalled the gvfs-backends, and it didn't help.

---

### Post by Temposs on 2009-02-03
Maybe it would help if we could have the URL to the podcast you're wanting to connect to. Then we could test it out ourselves.

---

### Post by jbraswell on 2009-02-03
Er, I'm sorry.  I forgot to mention that it's the password protected ones that are giving me problems. The exact message is

> 
There was a problem adding this podcast: Unable to parse the feed contents.  Please verify the URL: [http://www.japanesepod101.com/premium_feed/custom_0129_5275904_UpperIntermediate.xml](http://www.japanesepod101.com/premium_feed/custom_0129_5275904_UpperIntermediate.xml). Would you like to add the podcast feed anyway?

---

### Post by jburrell on 2009-03-02
'JBraswell, all - Hi again.  We've just had a baby so I've been away from the computer for awhile and now I have a spare moment...

My podcast issue is not resolved and I get exactly the same error message that JBraswell posted on this thread.  I know the URL I'm using is good because it works just fine in ITunes.  The podcast is also password protected.

---

### Post by NoBugs! on 2009-03-03
If that's a valid podcast file then it should open fine in Firefox. Does that work?

---

### Post by jburrell on 2009-05-01
I can open the podcast file I'm trying to listen to just fine in Firefox - no problem there.  I just deleted the feed in Rythymbox, reinstalled the gvfs-backend file in the synaptic, re-added the feed and I get the same error "can't parse the contents..."

---

### Post by mister_p_1998 on 2009-05-01
Try using Icepodder for your podcasts, Ive used it for years (formerly Ipodder) and I think its the best available.

Steve

---

### Post by cytenticle on 2010-05-23
Have a solution for password protected podcasts and rhythmbox

When you add the podcast feed add it in this format

```
http://username:password@podcasturl.com
```
for example

your username - user
your password - password
podcasturl - secretpodcast.com/podcast.xml

the way you would add the feed is -

```
http://user:password@secretpodcast.com/podcast.xml
```

Hope that helps - worked for me.

---

