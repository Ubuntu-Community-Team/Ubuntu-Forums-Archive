---
title: "Shutdown Delay of 60 Seconds"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by golfnut324 on 2010-04-07
Can someone tell me how to change the shutdown delay? Right now it defaults to 60 seconds after selecting shutdown. I'd like to make that 10 seconds or so.

Thanks!

---

### Post by -humanaut- on 2010-04-07
sudo shutdown -h 10

will halt it in 10 seconds -r will restart it
I'll look around to change the defaults I don't remember how but that's a temp solution

---

### Post by Revolutionary101 on 2010-04-07
You could make a launcher on your desktop that has this command:

```
sudo shutdown -P 10
```

That would shut the computer down after 10 seconds.

---

### Post by golfnut324 on 2010-04-07
I stumbled on the solution for anyone else looking. Here's a link:

[http://smackerelofopinion.blogspot.com/2009/11/suppress-60-second-delay-in.html](http://smackerelofopinion.blogspot.com/2009/11/suppress-60-second-delay-in.html)

I used gconf-editor to change value to "True"

Thanks for your inputs.

---

