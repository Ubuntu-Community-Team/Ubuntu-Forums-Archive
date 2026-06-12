---
title: "Firefox is closing after pasting something!"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by ovroniil on 2009-10-09
Every time I am pasting some text my firefox is closing down. Is there any solution of it? I am sharing the video of that 'closing' process...

[B]  [ Here is the Video!! ]("http://tinypic.com/r/6rnfiq/4")
                                [/B]

---

### Post by taavikko on 2009-10-09
Test with new user
```
sudo adduser test
```
then logout and login to the new "test" account.

Test with another theme (try default human), there can be issues with theme.

Test with new firefox profile, close FF
```
firefox -ProfileManager
```

---

### Post by lovinglinux on 2009-10-09
> **taavikko said:**
> Test with new user
```
sudo adduser test
```
then logout and login to the new "test" account.

Test with another theme (try default human), there can be issues with theme.

Test with new firefox profile, close FF
```
firefox -ProfileManager
```

I don't think creating a new user is necessary. Just creating a new profile should do the trick.

BTW, take a look at [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). It has some optimizations that might help.

---

### Post by sandyd on 2009-10-09
try running firefox from terminal.

then you can collect the terminal output when it crashes.

that info will help us identify the problem.

---

