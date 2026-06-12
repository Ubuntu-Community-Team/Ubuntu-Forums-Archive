---
title: "Internet does not work!"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by acompay on 2010-09-17
[COLOR=black][FONT=Verdana]Hello There![/FONT][/COLOR]
[COLOR=black][FONT=Verdana]My computer has wired and wireless capabilities. When the computer is on the wired connection is active but I can't log on the Internet. I turned off a few times the router and the modem but this did not work. What can I do? You all know that without access to the internet I can't use Ubuntu.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks![/FONT][/COLOR]

---

### Post by Arla on 2010-09-17
YOU BROKE THE INTERNET!!!! OMG!!!

Okay sorry, just had to throw it out there, so starting the "easy" way, first off can you reacdh the internet with other computers/operating systems?

Second, when on the wired connection, can you reach anything? I.E. can you reach your local network (the router menu is a good place to try) or can't even reach that?

---

### Post by ajgreeny on 2010-09-17
Try to go to your router with your web browser.  It is probably at 192.168.0.1 or something similar (look in the router manual, or under the router itself on the label, to find it)

That will at least tell us if that connection is working.  You could also try pinging something with ```
ping -c 5 www.google.com
``` to see if you can get out of your LAN to the outside world.

Lastly show the output of ```
ifconfig
```

---

