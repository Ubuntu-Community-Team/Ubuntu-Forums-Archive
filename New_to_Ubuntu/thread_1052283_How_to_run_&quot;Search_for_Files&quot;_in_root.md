---
title: "How to run &quot;Search for Files&quot; in root"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Ralph L on 2009-01-27
To my dismay I discovered that neither Nautilus nor Main menu>Places>Search For Files" will find all files.  I think this is because in default mode (even though I am the administrator), these programs do not have permission to see all files.  I think I fixed this for Nautilus by making a special launcher, Nautilus Root, that has the command "gksu nautilus" and thus runs with root permissions--dangerous but I don't use it often.  However, the Nautilus search does not display a path to the files it finds. (Seems really strange--why do a search if you don't want to know how to get to the file--Properties gives the path but what a nuisance.)  

Search For Files does display a path for each file found in a nice readable format and I was able to add it to my Task Bar panel so it is very available.  I tried to create a special launcher with root permission for Search For Files (using gksu), which shouldn't be dangerous, but I can't find the command to initiate it.  For Nautilus I just did right click Main menu>Edut Menus>Accessories>File Browser>Properties to find the command. However, Search For Files does not appear in Edit Menus and when I right click the Icon in my 
Task Bar, it does not display Properties.

Does anybody know the command to launch Search For Files so that I can create a launcher for it with root permission?

Thanks
Ralph

PS. If anybody knows of an extension for Nautilus search that displays a path I would like to know about that also.

---

### Post by LowSky on 2009-01-27
just install beagle, its a better quality search program, its in the repos i believe
also here
[http://beagle-project.org/Main_Page](http://beagle-project.org/Main_Page)

---

### Post by Coreigh on 2009-01-27
The command you asked about is gnome-search-tool the command is;
```
sudo /usr/bin/gnome-search-tool
```

or from the run program dialog: > gksudo /usr/bin/gnome-search-tool

If you get familar with the command line both locate and find are very powerful search tools and are likely what is underneath the GUI searches that you are using now.
```
man find
....
man locate
```

You can also find the man pages on line just google the commands above.

---

### Post by Ralph L on 2009-01-27
Sorry for the post.  I found it in System Monitor.  Its gnome-search-tool.

But if anybody knows of a Nautilus extension that would show paths to found files, like Search For Files does, I am still interested.

Ralph

---

### Post by andrew.46 on 2009-01-28
Hi,

As Coreigh has mentioned you would do well to have a look, one day perhaps, at the linux 'find' command. If for example you wanted to search $HOME for ogg files you could simply run:

```

andrew@skamandros~$ **[COLOR="Red"]find $HOME -iname '*.ogg'[/COLOR]**
/home/andrew/music/ftgws_11012009.ogg
/home/andrew/music/ftgws_18012009.ogg
/home/andrew/music/iRiver/4last_songs.ogg
/home/andrew/music/iRiver/brahms_double.ogg
/home/andrew/music/iRiver/St_Ursula.ogg
/home/andrew/music/iRiver/Schumann_Cello_Concerto.ogg
/home/andrew/music/iRiver/bartok_4tet_1.ogg
/home/andrew/music/iRiver/mozart_requiem.ogg
/home/andrew/music/iRiver/Brahms_Clarinet.ogg
/home/andrew/music/iRiver/Victoria_requiem.ogg
/home/andrew/music/iRiver/rococo_variations.ogg
/home/andrew/music/iRiver/schubert_quintet.ogg
/home/andrew/music/ftgws_25012009.ogg

```

and that is the most basic example of find's capacities :-).

Andrew

---

