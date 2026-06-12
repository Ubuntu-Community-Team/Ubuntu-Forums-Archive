---
title: "screen taskbar: any ideas how to put the clock to the right corner and with colours?"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by frenchn00b on 2009-11-24
I have this config and can we put this clock to the right side, at corner?

 cat .screenrc
```
h**ardstatus alwayslastline "%c %w"**


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

```


SOLVED:
> 

 
# status
hardstatus alwayslastline "%{= Yk}%H %{= yk}%-Lw%{= kG}%50> %n%f* %t %{-}%+Lw%< %=  %{= yk} %l %{= Yk} %0c:%s %d/%m %{-}"

# add CPU idle/sustem/user/interrupt stats
backtick 200 5 5 date +%H:%M
backtick 100 5 5 tail -n 1 $HOME/.log
caption always '%{= kY} %200` %= %100` %='


bindkey ^[[1;5A prev
bindkey ^[[1;5B next
bindkey ^[[1;5D prev
bindkey ^[[1;5C next
bindkey ^N screen
bindkey ^[[1;2D prev
bindkey ^[[1;2C next

bindkey -k F1 prev
bindkey -k F2 next



---

