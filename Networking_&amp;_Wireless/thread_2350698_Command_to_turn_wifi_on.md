---
title: "Command to turn wifi on?"
date: 2017-01-26
forum: Networking &amp; Wireless
---

### Post by 98cwitr on 2017-01-26
Sorry for the n00b question, but if I switch wifi off in the gui, what is the terminal command to turn it back on? 

Ifconfig wlo1 up 

Doesnt seem to get the gui to flip the switch, nor show the wifi indicator.

---

### Post by 98cwitr on 2017-01-26
```
nmcli r wifi on
```

That did it...knew it was something simple!

---

