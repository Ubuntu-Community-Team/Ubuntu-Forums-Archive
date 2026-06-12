---
title: "Script Automation with Expect Help"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by Chasingu on 2011-07-17
Hey there. I am running a minecraft server that starts via cron.

Now, when the script runs, it doesn't bring up a terminal window, giving me no GUI. So, I have decided to automate the process with Expect. However, I cannot find out how to send the terminal an enter key to start the script.

Here is my expect code:
```

#!/usr/bin/expect -f

#Get a Bash Shell
spawn -noecho bash

#Wait for a prompt
expect "$ "

#Type something
send "./start.sh"

#Hand over Control
interact

exit
```

All the above code does is just open terminal and post ./start.sh, but it doesn't hit enter. Is there anyway I can send it an enter key after it posts ./start.sh?

Thanks in advance.

---

