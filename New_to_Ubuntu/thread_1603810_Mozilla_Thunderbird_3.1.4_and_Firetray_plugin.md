---
title: "Mozilla Thunderbird 3.1.4 and Firetray plugin"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by idavid2013 on 2010-10-23
Sorry if double posting or so.

Recently I've upgraded to Ubuntu 10.10 and found out Mozilla Thunderbird 3.1.4 is acting a bit unwanted way: on start up it would not minimize to tray (using Firetray plugin for Thunderbird) and to close the window for the first time I've to click twice on the close button.

Hopefully that would be fixed some time soon. But for now I've used the next solution:

$ sudo apt-get install wmctrl

that would install **wmctrl** if you already don't have it installed, and start Thunderbird with custom bash script:

#!/bin/bash
sleep 15
thunderbird &
sleep 3
wmctrl -c "Mozilla Thunderbird"
wmctrl -c "Mozilla Thunderbird"

that would let system start up and then start Thunderbird, wait for Thunderbird to start and with **wmctrl** close the window with Mozilla Thunderbird twice. So I end up with everything running and Thunderbird  minimized to system tray.

PS! You might need to customize the sleep intervals for you system

Hope this would be helpfull to someone like me ...

---

### Post by idavid2013 on 2010-10-23
Just have noticed recently: if I disable "Start minimized" option in Firetray plugin, then Thunderbird closing works normally at one click on close button. So with option disabled I've shortened the start up script by one line:

#!/bin/bash
sleep 15
thunderbird &
sleep 3
wmctrl -c "Mozilla Thunderbird"

=D>

---

### Post by bogianen on 2010-12-09
Thank you very much, idavid. I was going mad trying to resolve the problem about starting thunderbird minimized in the icon tray.
I tried without success, or full satisfaction: kdocker, AllTray, various thunderbird's extensions.

---

### Post by hanspr on 2011-01-30
My small contribution to this problem, from your current idea. Create a script like this, you do not have to worry about timing, this is a perl script and you start ti from "Start up applications"
See below for change that does not affects ureadahead profiling.

```
#!/usr/bin/perl

$count = 0;
$tb = 0;
$ff = 0;

while ($count < 2) {
    $chk = `wmctrl -l | grep Thunderbird`;
    if (($chk) && (!$tb)) {
        system "wmctrl -c Thunderbird";
        $count++;
        $tb++;
    }
    $chk = `wmctrl -l | grep Firefox`;
    if (($chk) && (!$ff)) {
        system "wmctrl -c Firefox";
        $count++;
        $ff++;
    }
}
```

---

### Post by hanspr on 2011-01-30
Obsolete

---

### Post by hanspr on 2011-01-30
Well, I don't know why I dint' think about this before, with this modification your don't need to mess with rc.local.
```

#!/usr/bin/perl

if (!-e "/var/lib/ureadahead/pack") {
    exit 0;
}

$count = 0;
$tb = 0;
$ff = 0;

while ($count < 2) {
    $chk = `wmctrl -l | grep Thunderbird`;
    if (($chk) && (!$tb)) {
        system "wmctrl -c Thunderbird";
        $count++;
        $tb++;
    }
    $chk = `wmctrl -l | grep Firefox`;
    if (($chk) && (!$ff)) {
        system "wmctrl -c Firefox";
        $count++;
        $ff++;
    }
}

```

---

### Post by idavid2013 on 2011-02-27
Thank you for supporting the idea. I've recently played with BASH and found even better way. So if anyone is interested:

```

#!/bin/bash
thunderbird &
while [ true ]
do
   sleep 5
   status=`wmctrl -l | grep Thunderbird`
   if [ "$status" != "" ] ; then
      break
   fi
done
wmctrl -c "Mozilla Thunderbird"

```

It starts Thunderbird. Enters in a loop: sleep 5 sec, checks if Thunderbird's window has opened (then minimizing it and ends, otherwise continue in a loop until Thunderbird successfully minimized).

Always welcome any better ideas!

---

