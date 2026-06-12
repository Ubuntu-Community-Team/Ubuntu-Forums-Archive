---
title: "HELP!!! im stuck at point 11 of HOWTO: Broadcom 4318 HOWTO: Step by Step"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by buttyshell on 2007-02-27
I am working my way through "HOWTO: Broadcom 4318 HOWTO: Step by Step" however I seem to be stuck at part 11

Can anyone who knows about this maybe help me through messenger?

---

### Post by chili555 on 2007-02-27
Where is this HOWTO? Link, please.

---

### Post by buttyshell on 2007-02-27
[http://ubuntuforums.org/showpost.php?p=1189681&postcount=105](http://ubuntuforums.org/showpost.php?p=1189681&postcount=105)

---

### Post by johnc4510 on 2007-02-27
What kind of problem are you having with point 11?

---

### Post by buttyshell on 2007-02-27
it says press enter on the google box and wait for page to load, yet no page loads????????

---

### Post by johnc4510 on 2007-02-27
Put your mouse cursor in the box and left click as if you were going to type in a word to search, but do not type in a word. The cursor  should be blinking in the box. Now just hit enter and it will take you to Google home page. Then close the browser and go to point 12 and follow the instructions.

---

### Post by buttyshell on 2007-02-27
thats just it I click the box and press enter but page does not load
jsut says "Server not found"
"Firefox can't find the server at www.google.com"

All the other steps worked as planned until i got to no.11

---

### Post by chili555 on 2007-02-27
I think that step is 4-5 steps premature. Go on to the next steps and post back if you get stuck.

---

### Post by buttyshell on 2007-02-27
OK i carried on and did step 13
13.)UN@CN:~/Desktop$ sudo -i
A.)Press the Return/Enter key
B.)Key in your administrator password
C.)Press the Return/Enter key

But now terminal screen says
root@trev-laptop:#     instead of trev@trev-laptop:~/Desktop#

and cd Desktop states -bash: cd: Desktop: No such file o directory

---

### Post by chili555 on 2007-02-27
Try ```
cd /home/UN/Desktop
```

And then proceed.

---

### Post by buttyshell on 2007-02-28
14.)UN@CN:~/Desktop# modprobe ndiswrapper
A.)Press the Return/Enter key

[COLOR="Red"]THIS DOES NOTHING[/COLOR]

[COLOR="Black"][/COLOR]

15.)UN@CN:~/Desktop# ifdown eth1
A.)Press the Return/Enter key
[COLOR="Red"]THIS SAYS THAT eth1 IS NOT CONFIGURED, HOW DO YOU CONFIGURE IT?[/COLOR]

16.)UN@CN:~/Desktop# ifup eth1
A.)Press the Return/Enter key
[COLOR="Red"]THIS SAYS THAT eth1 IS NOT CONFIGURED, HOW DO YOU CONFIGURE IT?[/COLOR]

---

