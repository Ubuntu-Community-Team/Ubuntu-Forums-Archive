---
title: "Username problem"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by Spacemarine288 on 2009-05-10
Well, my son last night decided to install Ubuntu 8.10 last night alongside  our Windows XP home edition without my permission. I told him to wait off on installing it, as i wanted to learn more about it, but he installed it anyways. Well, in the process, he put a username and password on it, so I cannont log in. He refuses to tell me, even though ive punished him best I can.
Its currently installed on a old HP system that runs extremly slow.

Any help?

-An angry parent.

---

### Post by Sef on 2009-05-10
Read [Psychocats Forgot Password]("http://www.psychocats.net/ubuntu/resetpassword").

Once you are able to get into the system with a new password.  Then go to System > Administration > Users and Groups.   There you can set him up with a nonadmin account.

---

### Post by sisco311 on 2009-05-10
:)

You can reset the password in the Recovery Mode.

[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by krzysz00 on 2009-05-10
This is a command-line related procedure (read: typing, not very "'user-friendly'")
This will get you his username and let you change his password.
print this out before starting
Here is the deal.
1. When the computer turns on, (assuming he left windows installed) there will be a menu. The menu should have various options in it (for example: Ubuntu 9.04, krenel 2.6.28-11) or such. Or, there will be text which says "press ESC to get to the menu" (in that case press escape). Use the up and down arrow keys to select the one with "(recovery mode)
" at the end.  (The keys are also used to select windows btw) Hit the "Enter" key when done
2. You will see a bunch of text. Eventually, you will get to a menu-looking structure with various recovery options in it. Use the arrow keys to go to either of the options which say anything about a "root prompt" Again, hit enter when is is selected.
3. You will see a # and a little blinking line after it. This is a root shell, the most powerful and arcane place in Linux (This is the only place I could think of from which you can do this)  You must now type:
```
grep 1000 /etc/passwd
``` and hit enter
You will see a line like this:
```
**krzys**:x:1000:1000:Krzysztof Drewniak,,,:/home/krzys:/bin/bash

```(The little part in bold is his username. Remember it (or write it down)(The name will be different on your system)
4. To change the guy's password type:
```
passwd <his username>
``` (same with enter)
(replace <his username> with the username from step 3)
Now proceed to type the password (there are no * or anything so do not be alarmed) and hit enter 
Then retype the password and hit enter
You should see "Password changed"
now type reboot (and then enter)
The system will reboot. You know his username and password now. Just login as normal.
P.S. You will want to add a user for yourself. It's under System->Administration->Users and Groups (follow directions)
**Remember the password**!!!!! Is is needed to preform many system administration tasks, such as installing new software with Synaptic Package Mananger (just talk to your son or read the help for more info)
_*I appoligie for your rough intoduction to the wonderful world of Linuix. If you are at all curious about how that all worked, that knowledge is avalable to all who look.*_

---

### Post by krzysz00 on 2009-05-10
Someone beat me to it, drat!

---

