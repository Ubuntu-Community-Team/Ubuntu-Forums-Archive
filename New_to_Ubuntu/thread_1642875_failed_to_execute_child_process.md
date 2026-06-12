---
title: "failed to execute child process"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-12-11
last thing i have to do to complete my reinstalled. again had separate home folder. after i re-installed 10.04 and upgraded to 10.10 i went to the software center an installed chromium again. i get this error when i try to open chromium


could not launch chromium web browser-failed to execute child process "chromium--incognito" (no such file or directory)/tks

---

### Post by jtarin on 2010-12-11
Your launch command should be ```
chromium --incognito %U
```

---

### Post by rburkartjo on 2010-12-11
okay i figured out how to fix. 
first i went to /usr/bin/chromium-brower
i copied this to the desktop and could launch chromium no problem. still couldnt launch it from/app/internet/chromium web browser : i still received the aforementioned child process error. so i when to app right clicked and then left clicked the edit menu option and change the the launch command to chromium-browser  enabling  me to launch from the app menu. whew!!!

---

