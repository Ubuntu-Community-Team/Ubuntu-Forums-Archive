---
title: "Do we need X11 to run Xvfb ?"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-24
Hello,

I would like to run skype without installing X11 or XORG. This might be difficult. But let's try ... what is the minimum required for running XVFB and also permit an SSH -X ? 

here my script:
```
#!/bin/sh
killall -e skype Xvfb 
Xvfb :5 & 
### while [ 1 ] ; do #not working
DISPLAY=:5 ; export DISPLAY ; cat $HOME/.skypestartrc  | skype --pipelogin 
killall -e skype  
sleep 1s
beep
##done
```


[B]which X packages are necessary? 
I guess :
> apt-get install xinit 
for sure but the rest?[/B]

---

