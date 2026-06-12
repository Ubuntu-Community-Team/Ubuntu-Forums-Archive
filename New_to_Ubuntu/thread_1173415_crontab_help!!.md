---
title: "crontab help!!"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by aagavin on 2009-05-29
Here is my crontab entry that I have but it doesn't seem to be working:

> * *  * * *  /home/aaron/Pictures/change-background.py



---

### Post by kerry_s on 2009-05-29
cause you didn't put no time.

```
<minutes><hour><dayofmonth><month><dayofweek><command>
```

*** */1 * * * $HOME/Pictures/change-background.py**

that should do hourly. i hope you put the "export DISPLAY=:0" in that script. otherwise:

*** */1 * * * export DISPLAY=:0 && $HOME/Pictures/change-background.py**

---

### Post by aagavin on 2009-05-29
its a python script: here is the code:

> 
#!/usr/bin/python
#
# change-background.py
#
# A script to change to a random background image
#
# (c) 2004, Davyd Madeley <davyd@madeley.id.au>
#
#   This program is free software; you can redistribute it and/or modify
#   it under the terms of the GNU General Public License as published by
#   the Free Software Foundation; either version 2, or (at your option)
#   any later version.
#
#   This program is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License
#   along with this program; if not, write to the Free Software Foundation,
#   Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.
#

backgrounds = "/home/aaron/Pictures"

import gconf
import os
import random
import mimetypes

class GConfClient:
        def __init__ (self):
                self.__client__ = gconf.client_get_default ()
        def get_background (self):
                return self.__client__.get_string ("/desktop/gnome/background/picture_filename")
        def set_background (self, background):
                self.__client__.set_string ("/desktop/gnome/background/picture_filename", background)

client = GConfClient ()


dir_items = os.listdir (os.path.join (os.environ["HOME"], backgrounds))
items = []

for item in dir_items:
        mimetype = mimetypes.guess_type (item)[0]
        if mimetype and mimetype.split ('/')[0] == "image":
                items.append (item)

item = random.randint (0, len (items) - 1)
current_bg = client.get_background ()

while (items[item] == current_bg):
        item = random.randint (0, len (items) - 1)

client.set_background (os.path.join (os.environ["HOME"], backgrounds, items[item]))


---

### Post by aagavin on 2009-05-29
I also tried to put it in the .profile but that still didnt work???

thanks for your help

---

### Post by unutbu on 2009-05-29
I saved the change_background.py script on my machine, and set my crontab with this line:
```

*    *     *     *   *   /home/me/pybin/change_background.py
```

and it works for me.

Here are some suggestions to get it working for you:

Type```

crontab -e
``` and put 

```

USER=aaron
HOME=/home/aaron
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/aaron/bin
DISPLAY=:0.0
MAILTO=aaron
LANG=en_US.UTF-8

```
at the top of the crontab file.

This will set some basic environment variables for the jobs you run through crontab. 
Not all of these are necessary for your current problem, though 
```

DISPLAY=:0.0
```

might be.

Another thing to check is that .Xauthority is not owned by root. That can cause cron jobs that try to run graphical programs to fail. To check that you own your .Xauthority, type
```

ls -l ~/.Xauthority
```

You should see this:```


  -rw-------  1 aaron aaron     117 2009-05-29 13:16 .Xauthority

```
If that does not catch the problem, please post the output of 
```

find ~ -uid 0 -print
```

---

### Post by aagavin on 2009-05-29
K i tried that and it still doesn't work also I get no output for:

find ~ -uid 0 -print

---

### Post by unutbu on 2009-05-29
Have you tried opening a terminal (Applications>Accessories>Terminal) and typing
```

/home/aaron/Pictures/change-background.py

```
(The exact command as you have it in your crontab)?

Does it work from the terminal?

Also, please post the output of this command:
```

grep -A2 -B2 background /var/log/syslog | tail -n 10

```

---

### Post by aagavin on 2009-05-29
> **unutbu said:**
> Have you tried opening a terminal (Applications>Accessories>Terminal) and typing
```

/home/aaron/Pictures/change-background.py

```
(The exact command as you have it in your crontab)?

Does it work from the terminal?

Also, please post the output of this command:
```

grep -A2 -B2 background /var/log/syslog | tail -n 10

```
I am tried /home/aaron/Pictures/change-background.py in the terminal and it works

and here is the output of grep -A2 -B2 background /var/log/syslog | tail -n 10

-----
May 29 17:52:01 aaron-laptop /usr/sbin/cron[3532]: (aaron) RELOAD (crontabs/aaron)
May 29 17:52:01 aaron-laptop /USR/SBIN/CRON[22327]: (aaron) CMD (/home/aaron/Pictures/change-background.py)
May 29 17:53:01 aaron-laptop /USR/SBIN/CRON[22429]: (aaron) CMD (/home/aaron/Pictures/change-background.py)
May 29 17:54:01 aaron-laptop /USR/SBIN/CRON[22532]: (aaron) CMD (/home/aaron/Pictures/change-background.py)
May 29 17:55:01 aaron-laptop /USR/SBIN/CRON[22631]: (aaron) CMD (/home/aaron/Pictures/change-background.py)
May 29 17:56:01 aaron-laptop /USR/SBIN/CRON[22750]: (aaron) CMD (/home/aaron/Pictures/change-background.py)
May 29 17:56:01 aaron-laptop /USR/SBIN/CRON[22743]: (aaron) MAIL (mailed 600 bytes of output but got status 0x0001 )
May 29 17:57:01 aaron-laptop /USR/SBIN/CRON[22853]: (aaron) CMD (/home/aaron/Pictures/change-background.py)
May 29 17:57:31 aaron-laptop acpid: client 3318[0:0] has disconnected 
May 29 17:57:31 aaron-laptop acpid: client 3318[0:0] has disconnected 

-----

---

### Post by unutbu on 2009-05-29
aagavin, I'm out of ideas on how to fix crontab at the moment.
However, the change-background.py script can easily be modified to run
continually, changing backgrounds every N seconds.
You can setup change-background.py to run when you log in.

Here is the modified script:

[PHP]
#!/usr/bin/python
#
# change-background.py
#
# A script to change to a random background image
#
# (c) 2004, Davyd Madeley <davyd@madeley.id.au>
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2, or (at your option)
# any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.
#

import sys
import gconf
import os
import mimetypes
import time
import random

backgrounds = os.path.join(os.environ['HOME'],'Pictures')

class GConfClient:
    def __init__ (self):
        self.__client__ = gconf.client_get_default ()
    def get_background (self):
        return self.__client__.get_string ("/desktop/gnome/background/picture_filename")
    def set_background (self, background):
        self.__client__.set_string (
            "/desktop/gnome/background/picture_filename", background)

client = GConfClient ()

dir_items = os.listdir (backgrounds)
items = []

for item in dir_items:
    mimetype = mimetypes.guess_type(item)[0]
    if mimetype and mimetype.split ('/')[0] == "image":
        items.append (item)
try:
    sleepnum=int(sys.argv[1])
except (IndexError,ValueError):
    sleepnum=60

while True:
    item=random.choice(items)  
    current_bg = client.get_background()
    while (item == current_bg):
        item=random.choice(items)
    client.set_background (os.path.join (backgrounds, item)) 
    time.sleep(sleepnum)

[/PHP]

Click System>Pref>Sessions, add a new item, and use this as the command:
```

/home/aaron/Pictures/change-background.py 60
```

You can change 60 to any positive number. It represents the number of seconds the script will sleep before changing the background again.

---

### Post by aagavin on 2009-05-29
OK thanks for all your help I will try the script tomorrow

---

### Post by aagavin on 2009-05-31
> **unutbu said:**
> aagavin, I'm out of ideas on how to fix crontab at the moment.
However, the change-background.py script can easily be modified to run
continually, changing backgrounds every N seconds.
You can setup change-background.py to run when you log in.




Thank it works very well as I am using it now but it is taking up 4.5MB of memory..:(.

I did some experting with the crontab and found that the crontab works but when I use it to run a Python script it doesn't work but the script works when I run it from the Terminal...??

anyone have any ideas???????????????????????????????????

---

### Post by unutbu on 2009-05-31
aagavin, I'm glad to hear the modified script I posted works for you.
Regarding the memory issue: I'm no expert, but it seems to me if you were to run the original script through cron once every minute, you would still be consuming 4.5MB of memory for a few seconds every minute. Most programs last longer than a minute, so the memory consumption required by the script would still effectively be 4.5MB continuously. If at some point you were so tight on memory as to not have 4.5MB, then the cron job would fail anyway.

To locate the problem with cron, you might want to go to System>Admin>"Users and Groups"
and create a new temporary user. Log in as the new user, setup cron to run the original script, and see if it works for the new user. If it does, then you know the problem has to do with some configuration file in your normal user home directory. If the new user has the same problem, then at least we know the problem is system-wide. 

I'm still mystified what could be wrong, but at least the above would give us a clue as to where to focus our attention.

PS. Have you tried running other non-graphical python scripts via cron? Are you saying that all python scripts fail to run properly via cron, but bash scripts don't fail?

---

### Post by aagavin on 2009-05-31
> **unutbu said:**
> 

To locate the problem with cron, you might want to go to System>Admin>"Users and Groups"
and create a new temporary user. Log in as the new user, setup cron to run the original script, and see if it works for the new user. If it does, then you know the problem has to do with some configuration file in your normal user home directory. If the new user has the same problem, then at least we know the problem is system-wide. 

I'm still mystified what could be wrong, but at least the above would give us a clue as to where to focus our attention.

PS. Have you tried running other non-graphical python scripts via cron? Are you saying that all python scripts fail to run properly via cron, but bash scripts don't fail?

Ok I created another user and tried the script and it still doesn't work so i guess that it means that its system wide so bash scripts work and python scripts don't work with crontab.

---

### Post by unutbu on 2009-05-31
Could you save this in ~/bin/test.py
[PHP]
#!/usr/bin/env python
import os
os.system('env > /tmp/env.out')
[/PHP]
Make it executable:
```

chmod 755 ~/bin/test.py
```

Then edit crontab:
```

crontab -e
```

add this:
```

*    *	   * 	 *   *   /home/aaron/bin/test.py >/tmp/test.out 2>&1
```

save and exit crontab. 

Then wait a minute and see /tmp/env.out gets written.
Also see if there are any error messages in /tmp/test.out.

---

### Post by aagavin on 2009-05-31
> **unutbu said:**
> Could you save this in ~/bin/test.py
[PHP]
#!/usr/bin/env python
import os
os.system('env > /tmp/env.out')
[/PHP]
Make it executable:
```

chmod 755 ~/bin/test.py
```

Then edit crontab:
```

crontab -e
```

add this:
```

*    *	   * 	 *   *   /home/aaron/bin/test.py >/tmp/test.out 2>&1
```

save and exit crontab. 

Then wait a minute and see /tmp/env.out gets written.
Also see if there are any error messages in /tmp/test.out.

```
HOME=/home/aaron
XDG_SESSION_COOKIE=6d5fd50083447f8f3168a3a549f76139-1243800061.247441-1147770461
LOGNAME=aaron
PATH=/usr/bin:/bin
SHELL=/bin/sh
PWD=/home/aaron
```

ok here is the output of that file....

---

### Post by unutbu on 2009-05-31
Hm. Could you please run
```

crontab -l > crontab.txt
```
and post the crontab.txt file as an attachment.
And remind me, are you using Jaunty?

---

### Post by aagavin on 2009-05-31
> **unutbu said:**
> Hm. Could you please run
```

crontab -l > crontab.txt
```
and post the crontab.txt file as an attachment.
And remind me, are you using Jaunty?


k done here is that file:
```

# m h  dom mon dow   command
* * * * * /home/aaron/bin/test.py >/tmp/test.out 2>&1

```

and yes I am using Jaunty...

---

### Post by unutbu on 2009-05-31
Attached is a modified crontab.txt.

How about save it to your home directory and type
```

crontab ~/crontab.txt
```

This will update your current crontab with the contents of crontab.txt. Wait a minute for the cronjob to run, then check the contents of /tmp/env.out.

Please post the contents of /tmp/env.out. They should (hopefully) be different than the previous one you posted. It is important to see the DISPLAY=:0.0 environment variable. You need that for graphical apps to work properly.

---

### Post by aagavin on 2009-05-31
> **unutbu said:**
> Attached is a modified crontab.txt.

How about save it to your home directory and type
```

crontab ~/crontab.txt
```

This will update your current crontab with the contents of crontab.txt. Wait a minute for the cronjob to run, then check the contents of /tmp/env.out.

Please post the contents of /tmp/env.out. They should (hopefully) be different than the previous one you posted. It is important to see the DISPLAY=:0.0 environment variable. You need that for graphical apps to work properly.

K thanks, I downloaded the file and saved in my home dir and here the contents of /tmp/env.out 


[CODE]
USER=aaron
SHLVL=1
HOME=/home/aaron
XDG_SESSION_COOKIE=6d5fd50083447f8f3168a3a549f76139-1243813261.92780-485281878
MAILTO=aaron
LOGNAME=aaron
_=/home/aaron/bin/test.py
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/aaron/bin
DISPLAY=:0.0
LANG=en_US.UTF-8
SHELL=/bin/bash
PWD=/home/aaron
/CODE]

---

### Post by unutbu on 2009-05-31
Okay, that looks good.
Now let's try running this cronjob again:
```

*    *     *     *   *    /home/aaron/Pictures/change-background.py

```

---

### Post by aagavin on 2009-05-31
WOW it works thank you Unutbu for helping me on this one I owe you one, but may I ask you one more thing how did you fix it and what was the problem.

And Thanks again

---

### Post by aagavin on 2009-05-31
WOW it works thank you Unutbu for helping me on this one I owe you one, but may I ask you one more thing how did you fix it and what was the problem.

And Thanks again

---

### Post by unutbu on 2009-05-31
aagavin, I'm really happy to hear it works now.
I really don't know for sure what made the difference.

Overall, the problem was that the DISPLAY variable had to be set for the script to work.

When we concluded that the problem was "system-wide", all I did was suggest we try a really simple non-graphical python script that would report its environment variables in /tmp/env.out.

When I saw the DISPLAY variable was not set, I tried setting it by adding the variable to the top of your crontab file.

We ran the simple python script again, and the DISPLAY variable was set! That was the break through we needed.

---

### Post by kstarkey1 on 2009-06-09
> **unutbu said:**
> aagavin, I'm really happy to hear it works now.
I really don't know for sure what made the difference.

Overall, the problem was that the DISPLAY variable had to be set for the script to work.

When we concluded that the problem was "system-wide", all I did was suggest we try a really simple non-graphical python script that would report its environment variables in /tmp/env.out.

When I saw the DISPLAY variable was not set, I tried setting it by adding the variable to the top of your crontab file.

We ran the simple python script again, and the DISPLAY variable was set! That was the break through we needed.

My situation is almost exactly the same, except that my python script to change the wallpaper is based on the local temp, all other details are the same.  I went thru all of the step above, but no luck.  I was so psyched as I was going along, sure that it would work.  I've been working on this for days.  But alas, no luck.  How could that be?  It's not making sense to me (and that bothers me greatly).

Anyone have any thoughts?

Thanks!

---

### Post by unutbu on 2009-06-09
kstarkey1, please post your crontab:
```

crontab -l
```

and your python script.

---

