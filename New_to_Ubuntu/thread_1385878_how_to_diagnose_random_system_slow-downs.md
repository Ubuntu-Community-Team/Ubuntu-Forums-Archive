---
title: "how to diagnose random system slow-downs"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by Knacker on 2010-01-20
hi,
i've just installed karmic. i've used ubuntu for years, but i'm not a real power-user and still need help when it comes to certain break-downs.

my problem is this. since upgrading to karmic, i've been having problems with my desktop slowing down to a stand-still occasionally. everything is usually snappy, but then suddenly everything runs as though i'm running too many things (which I'm not). i've tried to use the system monitor to see whether there is a process that is eating resources, but nothing is showing up. the cpu graph never goes above what looks like 40-50% when it happens. what seems to gum things up is switching between windows, which makes me think it's a graphics problem - i've installed the latest stable nvidia driver from their website with their script. it also seems to be triggered by me moving files around on my hard drive, though, so i'm not really sure what it is...but it makes my system more or less unusable when it comes up.

can someone please help me diagnose this problem. i've flipped through some log files, but haven't found anything that looks like an error...which logs should i be looking at? any suggestions would be much appreciated. 
thanks!

EDIT: my new guess is that it's something to do with compiz, which i've not really had much experience with (except turning it off)...i'd like to use it...any suggestions or places i should look?

---

### Post by lotharmat on 2010-01-20
open a terminal and type:

```
top
```

This shows what is taking up what memory and processor power

---

