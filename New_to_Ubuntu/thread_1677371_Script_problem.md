---
title: "Script problem"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by glh5 on 2011-01-28
Hello, I have a fileserver where I stream files from using the following line:

```
ssh server cat "~/path/to/video\ file.avi" | mplayer -cache 32768 -
```

Where server is the ip address to my file server added in ~/.ssh/config.

I want to create a script for this. It seems very simple on first sight, but I'm stuck.

At the moment I have this:

```
#!/bin/sh
$PATH="$1"
ssh server cat "$PATH" | mplayer -cache 32768 -
```

I want it to make so I can type 

```
streamscript ~/path/to/video\ file.avi
```

But when I try it the outcome is:

```
arjen@arjen-laptop:~$ streamscript ~/torrents/completed/timpe-thetown.mkv
/home/arjen/bin/streamscript: 2: /home/arjen/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games=/home/arjen/torrents/completed/timpe-thetown.mkv: not found
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing -.
Reading from stdin...
Cache fill:  0.00% (0 bytes)   /home/arjen/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory
Cache fill:  0.00% (0 bytes)   
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!


Exiting... (End of file)
```

It has obviously something to do with the PATH variable. Can someone point me in the right direction? Help is appreciated

---

### Post by glh5 on 2011-01-29
bump

---

### Post by cjhabs on 2011-01-29
$PATH is a special variable used by the shell for defining where to look for programs.
Try using a different variable name like $my_video for example.

---

### Post by glh5 on 2011-01-31
Ah, thanks! So stupid I didn't think of that. It works now!

---

### Post by kittkatt on 2011-01-31
Please mark as SOLVED

---

