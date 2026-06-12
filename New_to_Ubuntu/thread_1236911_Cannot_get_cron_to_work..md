---
title: "Cannot get cron to work."
date: 2009-08-10
forum: New to Ubuntu
---

### Post by rob1101 on 2009-08-10
Hey I found a simple script that changes the desktop wallpaper and would like it to run every ten minutes or so but I cannot get cron to work at all. The script will run fine from the CLI.

here is my crontab -e
```
# minute (0-59), hour(0-23, 0 = midnight), day(1-31), month(1-12), weekday(0-6, 0 = sunday), command
10 * * * * python /home/robert/scripts/change-wallpaper.py
```Here is the script if anyone is interested :)

```
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

backgrounds = "/home/robert/.wallpapers"

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

```

---

### Post by quixote on 2009-08-11
I think the "python" is what's messing it up:
```
10 * * * * [COLOR="Red"]python[/COLOR] /home/robert/scripts/change-wallpaper.py
```
As far as I know, the correct format is 5 time fields followed by the command.  I think it reaches "python" and tries to run that.

---

### Post by llamabr on 2009-08-11
agreed.  try eliminating the word python and running the script.  It should know to run it with python.

---

### Post by rob1101 on 2009-08-11
Removed python still not working.

---

### Post by nandemonai on 2009-08-11
** Scratch that, I didn't read the original post properly.

---

### Post by unutbu on 2009-08-11
Put
```
DISPLAY=:0.0
```
at the top of your crontab.

---

### Post by rob1101 on 2009-08-11
Thanks guys its working like a champ now :D

---

### Post by quixote on 2009-08-11
Have you checked to make sure the script is executable?  If you use gedit or the like to write it, it has a nasty habit of saving as rw-r--r--.

(Just saw that there were other replies and that you got it working.  Excellent! :D)

---

### Post by rob1101 on 2009-08-11
actually I think I may have spoke too soon :( the wall paper changed and I thought it was due to the script but I guess not because it has been the same for longer than 10min.

Yes it has execute permissions.

```
-rwxr-xr-x  1 robert robert 1881 2009-08-09 21:35 change-wallpaper.py
```

And this is my crontab -e file

```
DISPLAY=:0.0

# minute (0-59), hour(0-23, 0 = midnight), day(1-31), month(1-12), weekday(0-6, 0 = sunday), command
10 * * * * /home/robert/scripts/change-wallpaper.py
```

---

### Post by Ram-Z on 2009-08-12
what your cronjob is doing is changing your wall paper at 10 past every hour...

you need to use:

```

# minute (0-59), hour(0-23, 0 = midnight), day(1-31), month(1-12), weekday(0-6, 0 = sunday), command
[COLOR="Red"]*/10[/COLOR] * * * * /home/robert/scripts/change-wallpaper.py
```

---

### Post by rob1101 on 2009-08-16
ok now it is working like a champ :P thanks for the help again guys.

---

