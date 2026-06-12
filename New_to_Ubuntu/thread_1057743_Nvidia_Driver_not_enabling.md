---
title: "Nvidia Driver not enabling"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by 7ehWhitey on 2009-02-02
I just installed ubuntu on my new laptop.. I only had trouble with 2 drivers, my wireless and my nvidia graphics driver, I enabled my wireless driver no problem, but when I try to enable the graphics driver it shows that it is working, then just stops and no changes are made.  I'm running update manager now.. I had 244 updates so its taking awhile.

I also show 2 different drivers, one is version 173 and one is 177 neither work. I just tried once more before I submitted my topic and it said.. "SystemError: Failed to lock /var/cache/apt/archives/lock" is that from update manager?/

It's 5:51 A.M. where I live, I'ma get some sleep, hopefully I can get this figured out in the morning. =)

---

### Post by Divider on 2009-02-02
need some more info. run these.

```
lspci
```


```
glxinfo | grep direct
```

then repost

and i too am also in the EST.

---

### Post by 7ehWhitey on 2009-02-02
Driver is working now, my updates finished and I restarted, apparentally one of them had to do with my driver downloading. Thanks for the help though.

BTW, how do you remember all the codes for terminal, is there like a "cheat" sheet I can find somewhere?

---

### Post by PriceChild on 2009-02-02
I'm *guessing* you have a problem because you were downloading something meant to work with the newer updates. As a general rule of thumb, unless you're sure about what you're doing, I would advise that it is best to make sure your current system is updated before installing new packages. Meh, you should be fully updated at all times really to ensure you're protected from new security threats!

As for the cheat sheet... I think its best to pick up as you go. As you use things you can read the manpages (type 'man *command*' in the terminal to learn about *command*) Or you could pick up [http://store.xkcd.com/#LinuxCheatShirt](http://store.xkcd.com/#LinuxCheatShirt) !

---

### Post by Divider on 2009-02-02
> **7ehWhitey said:**
> Driver is working now, my updates finished and I restarted, apparentally one of them had to do with my driver downloading. Thanks for the help though.

BTW, how do you remember all the codes for terminal, is there like a "cheat" sheet I can find somewhere?

almost 99 percent of linux is run threw a terminal, installing updating, debuging, etc.

after a crash course in it, (group of power user buddies) I picked up on bash far more easily than i ever did "command prompt" the problem with windows is, the command prompt is useful for two things, screwing around with someones computer(non-remote) and netstat.

netstat is the only command in windows i found usefull, and maybe tftp right off the bat. (ubuntu requires installion through apt)

---

