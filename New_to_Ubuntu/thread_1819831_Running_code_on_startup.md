---
title: "Running code on startup"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by BelugaWail on 2011-08-06
Hello everybody.

This is my first thread in the forum and I hope you guys will be able to help me out :).

I just installed 11.04 to my Early 2008 Macbook 4,1.  This is my first experience with linux and there are a few bugs I'm trying to work out.

The first issue is that my touchpad was having trouble detecting my finger.  I found a fix for this which was to run the commands "synclient FingerLow=10" and "synclient FingerHigh=20" in the terminal.

This seems to fix the issue, however, after restarting my computer the touchpad returns to its original state.  I'm wondering if there is a way to permanently change this or if I could just set up some kind of script to run after a restart?

Thanks in advance for your guys help.

---

### Post by lmarmisa on 2011-08-06
Hi BelugaWail.

Welcome to the forums. :D

I recommend to add those commands at the bottom of the file **.bashrc**. Try this command:

```

gedit ~/.bashrc

```

```

...
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

synclient FingerLow=10
synclient FingerHigh=20

```

Save & Quit.

You will have to log again into your user account for running the file **.bashrc**.

Best regards,

Luis

---

### Post by BelugaWail on 2011-08-06
Thanks for the quick reply!

I made the recommended change, but it does not seem to fix the issue.

Like I said before I am completely new to Linux.  Does the .bashrc always run at start up/log in?

---

### Post by lmarmisa on 2011-08-06
Yes, that is wrong. The script .bashrc runs when a new bash process is started (including a terminal).

Try to create a script (for example named inittouchpad.sh) with this content:

```

#!/bin/bash
synclient FingerLow=10
synclient FingerHigh=20

```

Then add the execution privileges to the script file:

```

chmod +x inittouchpad.sh

```

Finally add this script to the Startup Application list (System -> Preferences -> Startup Applications -> Add). Define a name (for example, InitTouchpad), and select your script in the field command.

I hope this solution will work.

---

### Post by BelugaWail on 2011-08-07
Excellent.  That seems to be exactly what I was looking for.

Once again thanks for the help.

---

### Post by lmarmisa on 2011-08-07
Great!!!. :D

Do not forget to delete the two lines added to the file **~/.bashrc** .

Best regards,

Luis

---

