---
title: "I think I missed something on install"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by perry6897 on 2010-07-14
I installed 10.04 from cd to a system with xp and followed the instructions I THOUGHT. However, I think when it asked me about my documents and such I should have brought some other items over as well. My clue was in my looking at what this was I realized I can't go on line. I have read every post and still can't get the fix. Did I forget to turn on the radio since I don't even receive a signal (that I can tell).
Why Ubuntu? You may ask. Because I'm retired but I want to challenge my mind.
So do I need to uninstall and start over if so HOW?
Thanks for the help.

---

### Post by nothingspecial on 2010-07-14
Before you reinstall, if your internet isn`t working then reinstalling isn`t going to fix it.

Go to your menu and go applications > accessories > terminal and copy and paste this command
```

sudo lshw -C network
```

and this one ```
ifconfig
```

Then copy the results here.

Also is it wireless or ethernet connection that isn`t working.

---

### Post by mikewhatever on 2010-07-14
From what I understood, the wireless internet connection doesn't work on Ubuntu. Is that correct?
If that's the case, the problem is not with something you have or haven't done, but rather with wireless drivers. Try connecting an ethernet cable, then open System->Admin->Hardware-Drivers.
Hopefully there is a driver available for your wireless card.

---

### Post by perry6897 on 2010-07-14
> **nothingspecial said:**
> Before you reinstall, if your internet isn`t working then reinstalling isn`t going to fix it.

Go to your menu and go applications > accessories > terminal and copy and paste this command
```

sudo lshw -C network
```

and this one ```
ifconfig
```

Then copy the results here.

Also is it wireless or ethernet connection that isn`t working.
Thanks. On the sudo I get command not found. The ifconfig shows 0 in all of the packets.
 
I'm able to go both ehternet and wireless when using windows. So I can go online that way?

---

### Post by nothingspecial on 2010-07-14
> **perry6897 said:**
> Thanks. On the sudo I get command not found. 

You shouldn`t, try typing it again.
 
> **perry6897 said:**
> I'm able to go both ehternet and wireless when using windows. So I can go online that way?

Get a wired connection in Ubuntu and come back here, then [COLOR=Red]copy and paste in the terminal[/COLOR]```
 sudo apt-get update && sudo apt-get dist-upgrade
```Then reboot.
Then in your menu go system > administration > hardware drivers, see if anything comes up.

If not, still in Ubuntu with a wired connection COPY AND PASTE
```

sudo lshw -C network
```

(that is a lower case L not a number 1)

Then paste the results back here.

---

### Post by perry6897 on 2010-07-15
**Thanks I'll try that.**

---

