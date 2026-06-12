---
title: "Please help me to ping every hour automatically!"
date: 2015-04-17
forum: Networking &amp; Wireless
---

### Post by riadtaihi-hotmail on 2015-04-17
Hello,

I am new in this forum and i am managing a linux server and it was requested from me to ping and collect packet loss every hour from 9 am to 5 pm from monday to friday and provide the network packet loss at the end of every week.
Is there a GUI way that can do this? or a Simple command in the terminal which will do all this and save it in a file that i will take every week?
the command i do manually is:
ping -c100 xxxxxxx.xxxxxxxxx.com

Thanks in advance.

---

### Post by ajgreeny on 2015-04-17
You need to use cron to do this, which is easy enough.

Rather than simply tell you exactly how to do it, have a good read through [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) and then if this does not tell all you need, (it should do), come back and ask for clarification.  You will remember and understand the whole thing much better if you find out for yourself, and doing so will hold you in a better situation for any further queries.

Once you have figured out cron you will then need to edit your command to something which will send the output of the ping command incrementally to a file, such as
```
date && ping -c100 xxxxxxx.xxxxxxxxx.com >> output.txt
```

---

