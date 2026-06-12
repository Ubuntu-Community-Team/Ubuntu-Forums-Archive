---
title: "Ugly ncurses in terminals?"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by scheibo on 2009-09-26
I was wondering whether it's possible to do something about how various terminal applications look when run in X. For example:

[IMG]http://imgur.com/CTr1L.png[/IMG]

Canto (on the right) is running and the whole terminal is faded when compared to the others on left. The same thing happens if I run "emacs -nw", or various other terminal apps. When run in a terminal without X running (ie. Ctrl-Alt-F2 or something), canto (et al) will all display nicely with a non-faded background and text. As a purely random guess, it looks like it has something to do with ncurses or some sort of framebuffering thing. I'd love some help in fixing it so that all my terminal apps look the same and theres no ugly fading going on.


PS. Off topic, but at the same time important: I'm trying to get mpd + ncmpcpp set up on ubuntu and its no go. I've changed my /etc/mpd.conf so that music_directory is "/home/<user>/music", but  when i run "sudo mpd --create-db" it doesnt do anything to add songs to the db file. It crates a db file, but theres no music in it. Any idea what I'm doing incorrectly?

thanks, 
kjs

---

