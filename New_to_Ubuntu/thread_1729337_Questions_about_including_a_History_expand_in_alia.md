---
title: "Questions about including a History expand in alias"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by JingfengLi on 2011-04-14
Hey, I try to create an alias that contains a history expand. I have worked on this for hours and I desperately need help. Thanks.

I tried
alias Echo='echo \!*';  which works on the other linux machine. 
Also, I tried Echo='echo `history -p`', which works fine. However, when I try to use the same thing for my command, like 
alias Bacd='cd Home/Ba `history -p`'.
It is not working.

Thanks.

---

### Post by seawolf167 on 2011-04-14
You mean editing bashrc to make an alias to run the history command?

```
gedit ~/.bashrc
```Add an alias at the bottom like

```
alias hh='history'
```Then save, close gedit, close your terminals and re-open them

---

### Post by JingfengLi on 2011-04-15
Hey, thanks for replying.
My issue is that I want to include a history expand in my alias.
Say I want to copy a file a directory, which is almost the same every time, but the file name would be different.

I want to create an alias like this,

```
alias Cpfile='cp ~/Work/ \!*'.
```

PS: ```
\!* 
```  is the code I try to use to accomplish that.

When I want to copy things, say macro.i from ~/Work/ directory, I just need to use the command
```
Cpfile macro.i ~/Newfold
```

However, this is not working.

Thanks.

---

