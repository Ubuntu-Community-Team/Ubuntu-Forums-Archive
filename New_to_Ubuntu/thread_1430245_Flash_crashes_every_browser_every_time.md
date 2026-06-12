---
title: "Flash crashes every browser every time"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by rockerphil on 2010-03-15
well the title pretty well says it but here it goes. ever since i upgraded my flash player to Flash Player 10 it crashes every single browser i've got installed, this includes Firefox 3, Google Chrome, Kazehakase, Opera, Swiftfox and even ies4linux (dillo doesn't count since it doesn't do Flash). here's some quick stats on the machine. it's an old Dell L500cx with a 500 MHz Intel Celeron processor and 512 MB PC100 SD RAM. the OS is Ubuntu 8.04 minimal install using Fluxbox and several other lightweight apps since my system resources are pretty limited. granted Flash wasn't that great before the upgrade, all i could do was listen to a youtube video and watch the video jump, but at least it didn't crash 100% of my browsers 100% of the time. i can't seem to figure it out, so any help at all is greatly appreciated.

Phil

---

### Post by xifer on 2010-03-15
> **rockerphil said:**
> well the title pretty well says it but here it goes. ever since i upgraded my flash player to Flash Player 10 it crashes every single browser i've got installed, this includes Firefox 3, Google Chrome, Kazehakase, Opera, Swiftfox and even ies4linux (dillo doesn't count since it doesn't do Flash). here's some quick stats on the machine. it's an old Dell L500cx with a 500 MHz Intel Celeron processor and 512 MB PC100 SD RAM. the OS is Ubuntu 8.04 minimal install using Fluxbox and several other lightweight apps since my system resources are pretty limited. granted Flash wasn't that great before the upgrade, all i could do was listen to a youtube video and watch the video jump, but at least it didn't crash 100% of my browsers 100% of the time. i can't seem to figure it out, so any help at all is greatly appreciated.

Phil


Had problems with this too not 100% sure if this will fix it for you but it will be a start

first create a config file with these two params.  It's worth reading about all the options for this file.

/etc/adobe/mms.cfg
```

WindowlessDisable=true
AVHardwareDisable=false


```


Then try starting firefox with this shared library preloaded like this

```

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox &

```


worked for me - hopefully flash developers will get around to sorting it out eventually...

---

