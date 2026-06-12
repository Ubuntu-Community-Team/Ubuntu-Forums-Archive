---
title: "SCREEN : how to duplicate the root session on another window?"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-03
Hello

screen
[enter]
sudo su

then I would like to do :
ctrl + A + N or whatever binding to get a next window with root #
is that possible?

here is my .screenrc
```
 hardstatus alwayslastline "%c %w"


bindkey ^[[1;5A prev

bindkey ^[[1;5B next


bindkey ^[[1;5D prev
bindkey ^[[1;5C next

 

bindkey ^N screen



bindkey ^[[1;2D prev
bindkey ^[[1;2C next



 
```

---

### Post by wheredidrealitygo on 2010-01-05
Just run 'sudo su' then run screen, every screen session will be root, the problem you're having is you're running screen as a normal user, so every new screen session is made from a normal user.

If you sudo su then run screen as root, every new screen will be root too.

The only compromise is you'll have to sudo su again before you resume the screen, because a normal user can't resume a rooted screen session.

---

### Post by frenchn00b on 2010-01-28
You like this one, screenshot?

```

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



```

---

