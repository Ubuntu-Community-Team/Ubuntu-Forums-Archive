---
title: "alittle bash help"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by ja660k on 2008-12-25
hey guys, i have a simple i mean real simple bash script, that just tells me the time and date.

but i have echo "XXXXXX" and im wondering if i can change the color of the string im trying to display. instead of it being the default colour of the terminal?

---

### Post by croto on 2008-12-25
Hi, what you need is to tell the console to change colors, which is done through xterm color codes. I googled it and this was the first result:
[http://www.frexx.de/xterm-256-notes/]("http://www.frexx.de/xterm-256-notes/").

An example of what you can do is:
```

echo -e "\033[1;31m$(date)\033[0m"

```

where the first escape sequence: \033[1;31m sets the foreground color to red, and the last sequence: \033[0m resets the terminal defaults.

---

### Post by ja660k on 2008-12-25
perfect, thankyou i didnt even know what to look for

---

