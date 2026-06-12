---
title: "SCREEN: start detached several commands?"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by frenchn00b on 2009-11-22
I would like that into the process, the music is running under screen. The problem is that ;. shall I put into nothing, or " or ', whats the best would you think?

```
 screen -d -m killall -e cplay splay ; sleep 10s ;  cplay music
```
or
```
 screen -d -m "killall -e cplay splay ; sleep 10s ;  cplay music"
```
or 
```
 screen -d -m 'killall -e cplay splay ; sleep 10s ;  cplay music'
```

---

### Post by BenAshton24 on 2009-11-22
The last two should work, but the first one won't because the semicolon would be treated as the delimiter between the screen command and those following and thus "sleep 10s ;  cplay music" would be ran on the current screen.

Hope everything works for you :)
Ben.

---

### Post by frenchn00b on 2009-11-22
> **BenAshton24 said:**
> The last two should work, but the first one won't because the semicolon would be treated as the delimiter between the screen command and those following and thus "sleep 10s ;  cplay music" would be ran on the current screen.

Hope everything works for you :)
Ben.

thank you !! you are very kind. 

I was thinking, can we insert Windows instead of at the end, when we do c-a c-n ?



cat .screenrc
> hardstatus alwayslastline "%c %w"


# Don't display the copyright page
startup_message off

# tab-completion flash in heading bar
vbell off

# keep scrollback n lines
defscrollback 1000

#For windows, F11 and F12 (NOT F1 and F2) to previous and next screen window can go to next prev window
bindkey -k F1 prev
bindkey -k F2 next
bindkey ^[[1;5A prev
bindkey ^[[1;5B next
bindkey ^[[1;5D prev
bindkey ^[[1;5C next
bindkey ^N screen
bindkey ^[[1;2D prev
bindkey ^[[1;2C next



---

