---
title: "ISDN Config help"
date: 2005-09-24
forum: Networking &amp; Wireless
---

### Post by Syphin on 2005-09-24
Im relativly new to using linux as my main system. Ive used it in classes, and other places.  But im planning on using it as my only OS on my home system now, Everything installed and is working great, accept for my ISDN.

I have a** 3com U.S. Robotics ISDN Pro TA (3CP3468A) External USB** modem, and i can not get it to work right for anything.

I have my wvdia.conf file setup like this:
```
[Dialer Defaults]
Modem = /dev/ttyACM0
Stupid Mode = 1
Carrier Check = no
Password Prompt = yes
Baud = 460800
Init1 = ATZ
Init2 = AT*PPP=3
ISDN = 0
Modem Type = USB Modem
Phone = 9254660
Username = Syphin
Password = ********
``` 

And whenever i try to connect i get this:
```
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: AT*PPP=3
OK
--> Modem initialized.
--> Sending: ATDT9254660
--> Waiting for carrier.
~[7f]}#@!}!} } }4}%}& [13]e[17]}#}$@#}"}&} } } } f1~~[7f]}#@!}!}!} }4}%}& [13]e[17]}#}$@#}"}&} } } } /"~~[7f]}#@!}!}"} }4}%}& [13]e[17]}#}$@#}"}&} } } } e[1f]~~[7f]}#@!}!}#} }4}%}& [13]e[17]}#}$@#}"}&} } } } ,},~~[7f]}#@!}!}$} }4}%}& [13]e[17]}#}$@#}"}&} } } } `l~~[7f]}#@!}!}%} }4}%}& [13]e[17]}#}$@#}"}&} } } } )[7f]~~[7f]}#@!}!}&} }4}%}& [13]e[17]}#}$@#}"}&} } } } cB~~[7f]}#@!}!}'} }4}%}& [13]e[17]}#}$@#}"}&} } } } *Q~~[7f]}#@!}!}(} }4}%}& [13]e[17]}#}$@#}"}&} } } } j}+~~[7f]}#@!}!})} }4}%}& [13]e[17]}#}$@#}"}&} } } } #[18]~~[7f]}#@!}!}*} }4}%}& [13]e[17]}#}$@#}"}&} } } } i%~~[7f]}#@!}!}+} }4}%}& [13]e[17]}#}$@#}"}&} } } }  6~~[7f]}#@!}!},} }4}%}& [13]e[17]}#}$@#}"}&} } } } lV~~[7f]}#@!}!}-} }4}%}& [13]e[17]}#}$@#}"}&} } } } %E~~[7f]}#@!}!}.} }4}%}& [13]e[17]}#}$@#}"}&} } } } ox~~[7f]}#@!}!}/} }4}%}& [13]e[17]}#}$@#}"}&} } } } &k~~[7f]}#@!}!}0} }4}%}& [13]e[17]}#}$@#}"}&} } } } oM~~[7f]}#@!}!}1} }4}%}& [13]e[17]}#}$@#}"}&} } } } &^~~[7f]}#@!}!}2} }4}%}& [13]e[17]}#}$@#}"}&} } } } lc~~[7f]}#@!}!}3} }4}%}& [13]e[17]}#}$@#}"}&} } } } %p~
NO CARRIER
--> No Carrier!  Trying again.

```

Now the thing is, with this setting, if i do "wvdial" and let it get to where it starts hanging for the carrier, and do the Ctr+c to close it, and do it again.. eventualy it connects..  Im on it right now.   But it usualy takes about 5-15 tries to get it to connect.

Ive searched for about a week trying to find what i could do, and have tried everything i can find, even diffrent network apps.

Only thing i found that i didnt try was compileing the kernel with the right USB Support, like it says to in this guide: [http://gentoo-wiki.com/HOWTO_ISDN_Alt](http://gentoo-wiki.com/HOWTO_ISDN_Alt)

I only havnt tried that, because ive never compiled a kernel before, and dont know how.  Ive looked at the guides, but the ones i found only showed how to compile it all, and not how to compile something into it.

Any help would be appreceated, as im trying to get this to work before i remove windows from my duel boot. :)

---

### Post by Syphin on 2005-09-28
Still need help if anyone has any ideas.
Lines went out for about 3 days, so havnt been able to do alot of tweaking to try and fix it the last few days.

---

