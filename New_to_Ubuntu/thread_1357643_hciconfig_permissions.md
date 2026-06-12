---
title: "hciconfig permissions"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by branstonpickle on 2009-12-17
Very new to ubuntu but have installed bluez bluetooth and a dongle successfully and written some python scripts. I want to do the command hciconfig hci0 name 'mutton' to change the friendly name of my bluetooth device (to mutton in this example) but can only do it using sudo. I want it to do it without sudo so it can be carried out in a python script. I am sure its a permissions or ownership thing but I've no idea where to start. Any thoughts?

TIA

---

### Post by llawwehttam on 2009-12-17
Could you please post the contents of your script then I may be able to help you. Where the password is you could use 'echo yourpassword' but anyone with access to the script sould read your password.

For something like this I would use sh shell script instead of python but its up to you really.

---

### Post by Hetepeperfan on 2009-12-17
type sudo chmod 775 yourfile

this makes yourfile executable for you

> **branstonpickle said:**
> Very new to ubuntu but have installed bluez bluetooth and a dongle successfully and written some python scripts. I want to do the command hciconfig hci0 name 'mutton' to change the friendly name of my bluetooth device (to mutton in this example) but can only do it using sudo. I want it to do it without sudo so it can be carried out in a python script. I am sure its a permissions or ownership thing but I've no idea where to start. Any thoughts?

TIA

---

### Post by branstonpickle on 2009-12-17
My script is short as it was purely a test

import sys
import os
sys.stdout.write(os.popen("hciconfig hci name 'big'").read())

It reacts the same as when it is executed froma command line in that it refuses unless I use sudo

I changed permissions of the file to 100777 but no joy so I was wondering if it could be permissions on a file affected by hciconfig when it executes

---

### Post by branstonpickle on 2009-12-17
I have got it working. I found something on another site
>*# chown root hciconfig*
>*# chmod 4711 hciconfig *

this solves the problem but I am concerned there may be a downside as hciconfig now shows in the file browser as being a program whereas before it was shown as a shared library

any feedback on whether this was dumb would be much appreciated

---

