---
title: "Wi-Fi problem in Wubi on HP"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by katrin2 on 2013-10-23
I installed Wubi on my HP laptop but I can't make the Wi-Fi work. I tried typing some codes I found on the Internter but nothing worked. I also can't connect using the cable.

---

### Post by varunendra on 2013-10-25
Hello katrin2, Welcome to the forums !

While running Ubuntu, please open a terminal (Ctrl-Alt-T) and enter the following commands one-by-one -
```
lsb_release -d
uname -mr
lspci -nnk | grep -iA2 net
```

Copy-paste the output to a text file (make sure to set the "Line Ending" to "Windows" in the save dilogue box), then copy paste the output here in your next post.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

