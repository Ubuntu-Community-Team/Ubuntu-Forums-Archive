---
title: "RhythmBox Question"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by neu5eeCh on 2010-02-08
Easy question: Why can't a figure out how to sort my playlists? Rhythmbox has loaded playlists in the wrong order and clicking on a given column (as in other media players) doesn't do anything?

Is this a limitation of Rhythmbox or what am I missing?

---

### Post by Jefferythewind on 2010-02-08
Maybe try running rhythm box as root.

---

### Post by neu5eeCh on 2010-02-08
Hey! That worked. Now, I guess, I need help changing permissions on Rhythmbox so I don't have to use it as root?

How do I do this? Chown?

By the way, I got all sorts of warnings running it as root (may or may not be relevant to my problem):

** (rhythmbox:9017): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (rhythmbox:9017): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:9017): Rhythmbox-WARNING **: Unable to grab media player keys: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

** (rhythmbox:9017): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (rhythmbox:9017): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (rhythmbox:9017): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (rhythmbox:9017): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

---

### Post by Jefferythewind on 2010-02-08
you can change permissions in Ubuntu using the chmod command in the Terminal ([http://ss64.com/bash/chmod.html]("http://ss64.com/bash/chmod.html")).

I have never changed a permission to run a program as root by default.  It seems like it may be an unsafe way to use your computer.  Hopefully you can change the permissions of the rhythmbox directories to give you write permissions.

---

### Post by ajgreeny on 2010-02-08
I strongly advise against running a program as root, particularly one that will access the web as rhythmbox can, and does. I am sure there must be another reason for your problem.

Perhaps related to tags in the audio files? Or do you mean that the playlists themselves are in the wrong order, not the audio files in the lists?

---

### Post by Enigmapond on 2010-02-08
Seems like too much hacking to get it to work. Why not just toss it aside and install Banshee? It works so much better...at least for me.

---

### Post by neu5eeCh on 2010-02-08
> **Jefferythewind said:**
> you can change permissions in Ubuntu using the chmod command in the Terminal ([http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)).

I have never changed a permission to run a program as root by default.  It seems like it may be an unsafe way to use your computer.  Hopefully you can change the permissions of the rhythmbox directories to give you write permissions.

I started nautilus as root and changed permissions for rhythmbox (the executable) from root to my username, but it didn't help. 

I don't need to run the program as "root", but it seems that my own permissions are lacking? 

I'm dead in the water until somebody with more experience helps me with this.

---

### Post by neu5eeCh on 2010-02-08
> **Enigmapond said:**
> Seems like too much hacking to get it to work. Why not just toss it aside and install Banshee? It works so much better...at least for me.

I'll try it. I'm not wedded to Rhythmbox.

Still, I might learn something if I could fix the problem.

---

### Post by Enigmapond on 2010-02-08
> **VTPoet said:**
> I'll try it. I'm not wedded to Rhythmbox.

Still, I might learn something if I could fix the problem.

True but MY GOD MAN! It's such a simple thing you want it to do and NO audio application should compel you to run it in root to play or act right...IMHO...:p

---

### Post by neu5eeCh on 2010-02-08
Yeah, I just downloaded Banshee and am listening to it right now. Works beautifully. I'm sold.

---

### Post by Jefferythewind on 2010-02-08
I like this solution.

---

### Post by Enigmapond on 2010-02-08
I love Ubuntu but one thing I've learned is if one application is EVIL, exorcise it as there is another application that will probably work better. He got a lot further than I would ever have gotten...:p

Cheers!

---

### Post by ajgreeny on 2010-02-08
As a follow on to my post #5, I have just updated to karmic from jaunty and have found that my pls files made in rhythmbox in jaunty, are, just like your playing tracks completely out of order. It is possible to to get them right by remaking them from the music library.

However, I have also now looked at banshee, and WOW!  What a great player that is; much nicer than rhythmbox, but in many ways so similar, to look at, at least, and also much better at downloading album art, which seemed broken in karmic's rhythmbox.

---

