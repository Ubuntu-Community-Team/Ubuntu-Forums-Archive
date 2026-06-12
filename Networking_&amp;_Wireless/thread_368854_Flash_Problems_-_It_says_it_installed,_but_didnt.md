---
title: "Flash Problems - It says it installed, but didnt"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by Tag_yer_dead on 2007-02-23
Hey guys,
just did the whole spoof to get flash and it went fine
however, when i run firefox it still doesnt work and doesnt detect the plug in

Ne ideas? Please be as specific as possible

Thanks

---

### Post by taurus on 2007-02-23
Do you see flash 9 on the list when you type this command in the address field?

```
about:plugins
```

Otherwise, here is a guide.

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Tag_yer_dead on 2007-02-23
no i do not see ne thing flash

---

### Post by sdide on 2007-02-23
First ask in general help, or perhaps Multimedia thread - this seems to be not a networkrelated problem.
Second:
# ls -l /usr/lib/mozilla-firefox/plugins | grep flash

if nothing returns, you need to make links to whereever you put your flash installation.
eg:
# ln -s /usr/lib/mozilla-firefox/plugins/libflashplayer.so <full_path_to_libflashplayer.so>

and also to "flashplayer.xpt" and if you installed firefox somewhere else, you need to change the above paths accordingly.

---

### Post by taurus on 2007-02-23
Then how did you install it?  Try to use the link in my previous post to see if you can get it install on your machine.

---

### Post by Tag_yer_dead on 2007-02-23
ooo i got it now, had to do it the complicated way
thanks ubuntu god

---

