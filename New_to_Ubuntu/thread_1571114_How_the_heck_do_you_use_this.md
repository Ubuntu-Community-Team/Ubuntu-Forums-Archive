---
title: "How the heck do you use this?"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by cbanakis on 2010-09-09
I'm running the latest ubuntu on my netbook and on my desktop.

I have a windows based file server with all my collected movies/tv shows/music

I'm using Windows Media Center computers in my living room, bedroom, and family room to watch live tv and stream videos from the server.

Since I have started to use linux (maybe 2 years ago?) I have been looking for an alternative to Windows Media Center.  (Media Center Sucks)

So far, I have experimented with about a dozen linux media centers, and either the dont do everything I need, or they just plain dont work.

I can access everything on my windows server with ease through ubuntu, but for the life of me I cannot get at them through any linux media center.

In most of these programs, I cant even figure out how to add files stored locally.

MythTV looks promising, but I'm about to throw my computer through a wall.

I have gone into the backend, and added all my network shares.

I tried entering the path using every format I can think of, and no matter what, it says directory not found.

Am I just a moron or what?

Am I stuck dealing with Mr Gates?

if anyone has any ideas how to get this work, I will be forever in your debt...

or even....

Anyone in the Chicago Land Area who considers themselves to be masters of mythbuntu?

I would gladly pay someone to come out and get me setup.

---

### Post by JohnHeikkila on 2010-09-09
You could try the MythTV but if you want to access the files, MediaTomb.

---

### Post by Barrucadu on 2010-09-09
Have you tried mounting the network share and using the path to the mountpoint? I don't expect it'll work with Windows-style share paths (ie //servername/path)

---

### Post by Peter09 on 2010-09-09
I have gone back to using rythmbox on my downstairs system - however I have tried some of the media centre software. They way I do it is to mount the network shares (using fstab) permanently onto the local Music folder, this appears to the applications just like a folder on a slightly slow disk, no problems.

---

### Post by cbanakis on 2010-09-10
I tried the mount points 
192.168.1.5/my-terabytes/

and file-server/my-terabytes/

I tried to do the fstab thing before but couldnt figure it out

---

### Post by Peter09 on 2010-09-10
There is an application called mount-manager (or similar) - which is in the repositories which, although I have never used in anger, may help you.
 
The thing to recognise in Linux is that network file systems are 'mounted' on an empty directory (what ever one you want) and once done, going into that directory shows the contents of the network share, not the contents of the original directory.

---

### Post by aeiah on 2010-09-10
work on getting your samba shares mounted in linux, like any other drive or directory, and then you shouldn't have a problem browsing in any media player.

if you don't want live tv or tv recording, i would advise you check out xbmc. if you do want live tv and recording, then mythtv is deff what you want.

both may offer you the opportunity to mount and browse samba shares directly but really you'd find things a lot simpler if you mount them properly

---

### Post by cbanakis on 2010-09-10
OK, so I finally figured out the fstab business, but its still not helping.

I've decided to dedicate my time to mythtv because it looks like the most promising alternative to windows mce.

I have my share mounted using fstab

It appears in my home directory now
/home/chris/****in-terabytes

The drive even shows in in mythtv now under system status/machine status...  (See Screen Shot)
But for some reason, the mythtv backend wont recognize the directories when I enter them.

I have tried the following formats

file:///home/chris/****in-Terabytes/Movies/
/home/chris/****in-Terabytes/Movies/
The-Machine:/home/chris/****in-Terabytes/Movies/
...

No matter what I enter, it warns me when exiting the backend saying "Path Does Not Exist"

Am I missing something here?
[IMG]http://ubuntuforums.org/[IMG]http://i340.photobucket.com/albums/o344/cbanakis/Screenshot.png[/IMG]
[IMG]http://s340.photobucket.com/albums/o344/cbanakis/?action=view&current=Screenshot.png[/IMG][IMG]http://i340.photobucket.com/albums/o344/cbanakis/Screenshot.png[/IMG]

(Sorry, cant figure out how to make it a thumbnail)
I did make it smaller though ;)
[IMG]http://ubuntuforums.org/%3Ca%20href=%22http://s340.photobucket.com/albums/o344/cbanakis/?action=view&current=Screenshot.png%22%20target=%22_blank%22%3E%3Cimg%20src=%22http://i340.photobucket.com/albums/o344/cbanakis/Screenshot.png%22%20border=%220%22%20alt=%22Photobucket%22%3E%3C/a%3E[/IMG]

---

### Post by Grenage on 2010-09-10
While Myth is quite good, I'd totally recommend XBMC as a media centre for both Linux and Windows.  It's blows MCE out of the water.

---

### Post by cbanakis on 2010-09-10
I think I messed with that one a while ago, but XBMC does not support live tv does it?

---

### Post by Grenage on 2010-09-10
> **cbanakis said:**
> I think I messed with that one a while ago, but XBMC does not support live tv does it?

Touché, it does not.  I wasn't aware you needed that - Myth is the way to go.

Back to the problem; I would have expected */home/chris/****in-Terabytes/Movies* to work.  If you type this in the terminal:

```
cd /home/chris/****in-Terabytes/Movies
```

If it enters the directory, then you know it's working as it should.  Further details should be listed [here]("http://www.mythtv.org/docs/mythtv-HOWTO-9.html#storagegroups").

It's possible than you'll get better help in the MythBuntu [subforum]("http://ubuntuforums.org/forumdisplay.php?f=301") - so you might want to 'report' your post and ask a mod to move it there.

---

### Post by ibod on 2010-09-10
did you use MythTV or  Mythbuntu 

[http://www.mythbuntu.org/10.04/beta1](http://www.mythbuntu.org/10.04/beta1)

We have this and it works but its not easy and no I did not set it up

---

### Post by cbanakis on 2010-09-10
> **Grenage said:**
> Touché, it does not.  I wasn't aware you needed that - Myth is the way to go.

Back to the problem; I would have expected */home/chris/****in-Terabytes/Movies* to work.  If you type this in the terminal:

```
cd /home/chris/****in-Terabytes/Movies
```If it enters the directory, then you know it's working as it should.  Further details should be listed [here]("http://www.mythtv.org/docs/mythtv-HOWTO-9.html#storagegroups").

It's possible than you'll get better help in the MythBuntu [subforum]("http://ubuntuforums.org/forumdisplay.php?f=301") - so you might want to 'report' your post and ask a mod to move it there.

Worked like a charm through terminal...
But still not in mythtv ???
I already spent like 2 hours exploring the link you gave.  But MythTV's "How To" seems to only teach me how to get a headache..

Haha, I just realized that since my drive is named F*ckin, when I copied and pasted from your post into terminal, it put the *'s in instead of the correct name...
But the funny thing is that it somehow worked anyway?
Like my computer was like "he must mean this"

LOL WTF?

---

### Post by cbanakis on 2010-09-10
> **ibod said:**
> did you use MythTV or  Mythbuntu 

[http://www.mythbuntu.org/10.04/beta1](http://www.mythbuntu.org/10.04/beta1)

We have this and it works but its not easy and no I did not set it up

MythTV in Ubuntu...

I figured, once I master that on my desktop, and I can put MythBuntu on my HTPC's, and hopefully what I learn here will still apply there.

If that makes any sense?

I assume MythBuntu operates very similarly to MythTV in Ubuntu

---

### Post by Peter09 on 2010-09-10
Not sure what the real name of your directory is but I would avoid using anything but alphanumeric characters. It may be that these applications (designed to work across a number of O/S) are stumbling over that.

---

### Post by cbanakis on 2010-09-11
Yeah, screw this.

I guess I can only run ubuntu on my dektop and laptop...

Back to windows media center for me.

Maybe I'll give it another go when mythbuntu 11 comes out.

"I'd rather run windows and have it work sometimes, than mythbuntu and not work at all"

---

