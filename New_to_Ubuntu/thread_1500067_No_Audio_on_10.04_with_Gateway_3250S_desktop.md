---
title: "No Audio on 10.04 with Gateway 3250S desktop"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by brucewagner on 2010-06-02
I have a Gateway 3250S and the audio does not work at all on Ubuntu 10.04. 

Any ideas?

---

### Post by brucewagner on 2010-06-02
This is the system BTW....

[http://support.gateway.com/support/srt/allsysteminfo.aspx?sn=0034564577]("http://support.gateway.com/support/srt/allsysteminfo.aspx?sn=0034564577")

---

### Post by lidex on 2010-06-02
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"

---

