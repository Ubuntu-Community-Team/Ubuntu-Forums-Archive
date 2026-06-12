---
title: "Mouse freezes on Toshiba NB305"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by brodiewells on 2010-10-03
I have a Toshiba NB305 netbook with a clean install of Ubuntu 10.04 NBR.  The touch pad mouse froze in the middle of working, and would not come back even with a restart.  It will come back after a full shutdown, but freezes again after a few minutes.  A USB mouse works, but i have a kid that makes using it a pain.

Any help would be greatly appreciated!

Thank you so much.

---

### Post by Hippytaff on 2010-10-03
what does
```

xinput list

```
return

---

### Post by brodiewells on 2010-10-03
> d:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
Oh wow, it's not there.  So, why would it see it for a few minutes and then lose it?  Thank you so much for looking into this.

---

### Post by Hippytaff on 2010-10-03
I don't know much about this but it might be driver issue...would need to research it, but a shot it the dark I'd try

```

sudo apt-get update && sudo apt-get upgrade

```in the first instance

---

### Post by brodiewells on 2010-10-03
I tried that but I get this

> 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Thanks again.

---

### Post by Hippytaff on 2010-10-03
try

```

sudo apt-get install gpointing-device-settings

```

if it still doesn't work try

```

sudo apt-get install touchfreeze

```

---

### Post by brodiewells on 2010-10-03
I tried the first one and restarted.  Again it worked for about a minute and then quit.

I now have a new mouse menu under accessories tho.  Playing around with it makes no difference.

The mouse does show up with the xinput list now tho


> xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=11	[slave  pointer  (2)]
&#9116;   &#8627; HID 1241:1166                           	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]


---

### Post by amjjawad on 2010-10-03
I'm not quite sure but I guess it's from the laptop itself. What made me think that is one of my friends has Toshiba laptop and he has Windows 7 (before had Vista) and he's suffering from the same issue. He said his pad works only when he formats his HD.

I know it's irrelevant but the same guy was also complaining about his Wireless Connection as it's always disconnected on Toshiba Laptop. I'm not saying Toshiba is bad, I'm just saying some functions may not work probably sometimes.

---

### Post by brodiewells on 2010-10-03
Now I tried the second one and it does not work either.  Now the gpointing-device-settings does not show the mouse anymore.  And it does not show in the xinput list either.

---

### Post by brodiewells on 2010-10-03
I have tried everything.  I have even tried using an old kernel image from when it was working.  Does anyone know if there is a way to use a windows driver on ubuntu?  Because it looks like there is a new one from toshiba.

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=2523339&rpn=PLL3AU&modelFilter=NB305-N410BL&selCategory=2756709&selFamily=2336267](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=2523339&rpn=PLL3AU&modelFilter=NB305-N410BL&selCategory=2756709&selFamily=2336267)

---

### Post by amjjawad on 2010-10-03
> **brodiewells said:**
> Does anyone know if there is a way to use a windows driver on ubuntu?  

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=2523339&rpn=PLL3AU&modelFilter=NB305-N410BL&selCategory=2756709&selFamily=2336267](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=2523339&rpn=PLL3AU&modelFilter=NB305-N410BL&selCategory=2756709&selFamily=2336267)

I don't think it's possible.

---

### Post by brodiewells on 2010-10-16
So, nothing huh?  I feel like I can't be the only one with this problem.  It's like the mouse got got shut off internally and there is no way to turn it back on.  This is my wifes computer and a USB mouose is not a viable option.  We have a 2 year old running around pulling on cables all day.

---

