---
title: "remind gxmessage script Segmentation fault"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-05-22
Hi Everyone,

I recently started playing with Kubuntu and have a problem with a script that runs in Ubuntu 10.10 and Xubuntu 11.04.


```



#!/bin/bash

remind -q ~/.reminders-general | gxmessage -buttons "Close:1" -default "Close" -center -font "serif 16" -fg "#231" -bg yellow -wrap -title "Remember" -file -


```

Here is the output of the script:

```


/home/john/scripts/rg: line 3: 31808 Done                    remind -q ~/.reminders-general
     31809 Segmentation fault      | gxmessage -buttons "Close:1" -default "Close" -center -font "serif 16" -fg "#231" -bg yellow -wrap -title "Remember" -file -

```

I don't know what a segmentation fault is.  Does anyone see what might be causing the problem?

---

