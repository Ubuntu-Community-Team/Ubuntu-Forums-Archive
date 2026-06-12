---
title: "Where is vlc in the root directory?"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by paker on 2009-09-05
How do I watch online TV using vlc?
The file name to play is xxxx.m3u.
The site says I can play it with vlc under linux.
When I click on the link, the following screenshot pops. (I cannot post the screenshot. I don't know how to)
I have "play with movie player" "play with other application" and "save" to choose from.
I select "open with other application." Next window is the root directory. Where is vlc hidden?

---

### Post by NoaHall on 2009-09-05
Why not just type "vlc" in as a command.

---

### Post by PGScooter on 2009-09-05
did you install vlc?

```
sudo apt-get install vlc
```

---

### Post by falconindy on 2009-09-05
m3u is the file extension for a playlist, not a media file. Open it with gedit and you'll see its just a text file.

[http://en.wikipedia.org/wiki/M3U](http://en.wikipedia.org/wiki/M3U)

To actually answer your original question, any program installed to a directory in the $PATH variable can be found simply with the name alone -- you never need to worry about the path itself.

If you actually find yourself ever needing the path of such a program, just use the whereis command. `whereis vlc` should resolve to /usr/bin/vlc. (can't check atm, borrowing a friend's macbook).

---

### Post by paker on 2009-09-05
vlc was already installed.
I could not just type in vlc. I had to select vlc from a folder tree.
usr>bin>vlc. It worked. Mucho gracias.

---

### Post by gunksta on 2009-09-05
I'm guessing that you are using FireFox as a web-browser?

The full path to the vlc executable is:
```
/usr/bin/vlc
```

If you prefer the VLC version with the pretty skins:
```
/usr/bin/svlc
```

That should answer your immediate question and let you use VLC, which I agree is an excellent choice. But since you asked, I'll take the brief liberty to use this as a teachable moment.

1) Most applications that you can use as a non-root user can be found in /usr/bin. You can use Dolphin to browse over and look at it (it will take forever to load in Dolphin). My computer has over 1,500 files in this directory.

2) If you are looking for a file, especially a system file, there are two good programs to use. locate, find. You can learn more by reading the man pages with "man locate" or "man find" at the terminal (drop the "").

I'll spend a minute on locate.

You could have used the locate command to find vlc in a single command (at a terminal prompt):
```
locate vlc
```

You mileage may vary, but that generated several hundred possible options on my computer, because the string vlc occurs many many times on the computer. Fortunately, we can narrow this down. I know I am looking for a line that includes "bin" because I'm looking for an executable. So, I can use grep to filter out the rest of it.

```
locate vlc | grep bin
```

This takes all the crap produced by the first command and "pipes" it over to the command grep, which ONLY returns lines that have the string "bin" in them. 

This command only returns 9 options, and it's easy to see which ones are interesting.

Good Luck!

---

### Post by gunksta on 2009-09-05
Damn. Too slow.  :-)

---

