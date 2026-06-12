---
title: "Delete file automatically at shutdown"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by Miguellint on 2010-06-22
Hi all....Using Ubuntu 9.04

I want to automatically delete a file at shutdown as it always causes an error message next time the computer boots. The file is in....

/home/ubuntu/.config/.rainlendar2

and the file is called....

Rainlendar2-ubuntu

I'm guessing I'll need to use the rm command and also to edit a file in the /etc/init.d folder....but then again I may be wrong :-)

Any suggestions welcome

Miguellint

---

### Post by wilee-nilee on 2010-06-22
Are you actually using the program? If not remove it.

---

### Post by Miguellint on 2010-06-22
> **wilee-nilee said:**
> Are you actually using the program? 

Yes I am. It's a great app with this minor flaw.

Miguellint

---

### Post by lifeSum on 2010-06-23
This should do what you want:

```

cd /etc/init.d
sudo gedit rm_rainlendar_config.sh

```When gedit opens up, add the following to the file: (also make sure the correct directory/file is used with the rm command. It IS case-sensitive)
```

#!/bin/bash

rm /home/ubuntu/.config/.rainlendar2/Rainlendar2-ubuntu

```Next:
```

sudo chmod a+x /etc/init.d/rm_rainlendar_config.sh

```Last:
```

sudo update-rc.d rm_rainlendar_config.sh start 20 0 6 .

```Do **not** forget the dot at the end of the last command!

Good luck! Let us know how it goes.

---

### Post by Paqman on 2010-06-23
> **lifeSum said:**
> 
```

sudo gedit rm_rainlendar_config.sh

```

Please use gksu or gksudo for graphical apps like gedit, sudo is only for terminal apps.

---

### Post by Metrop021 on 2010-06-23
> **Paqman said:**
> Please use gksu or gksudo for graphical apps like gedit, sudo is only for terminal apps.

slightly off topic but just to increase my knowledge, what exactly is the difference? all i see is that gksu opens up a nice looking window and sudo you just type into terminal.

---

### Post by Paqman on 2010-06-23
> **Metrop021 said:**
> slightly off topic but just to increase my knowledge, what exactly is the difference? all i see is that gksu opens up a nice looking window and sudo you just type into terminal.

Psychocats explains it better than I could. Basically it's about which profile the app is run with:

[Gksu vs sudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

Note that on some distros gksu and gksudo are slightly different commands. On Ubuntu they're identical.

---

### Post by lifeSum on 2010-06-23
> **Paqman said:**
> Please use gksu or gksudo for graphical apps like gedit, sudo is only for terminal apps.

Good eye. I knew gksudo existed, but never thought to research it. Thanks for the tip. :)

---

### Post by Miguellint on 2010-06-23
> **lifeSum said:**
> This should do what you want:

<snip>

Good luck! Let us know how it goes.


Hello lifeSum....Thanks for the reply.

It doesn't seem to work although, even with my limited knowledge, I can see what you've done and understand that it should work.

I get a "missing LSB information" warning when running the update-rc.d command but the start-up links are still made in rc0.d and rc6.d so I don't think the warning is critical.

Out of curiosity, I changed the runlevel to 2, re-booted, and then watched the startup messages scroll by. Sure enough there was a "rm action failed. No such file" message (or words to that effect). I looked for the exact message in dmesg but it wasn't there. Don't know why not.

So it seems like a path fault although the path specified is correct. Just to make sure I fired up the terminal and ran the rm command you gave and it deleted the annoying file as expected.

Maybe it's something to do with /home not being mounted when the script runs. That's the only reason I can think of for the error message.

I'll keep playing around cos it should work. 

Thanks for your help
Miguellint

---

