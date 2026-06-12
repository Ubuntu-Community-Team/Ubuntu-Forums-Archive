---
title: "Howto: get rid of the screensaver?"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by miamalleena on 2010-10-20
I have (what I think is) an automatic screensaver. But I would like to diable it because about after every 10 minutes, when being unactice, it turns on. I'm mainy stressed out because it's impossible to watch movies etc. 
a damsel in distress - is there any simple solution?

---

### Post by drs305 on 2010-10-20
miamalleena,

Welcome to the Ubuntu forums. I've moved your post to Absolute Beginners. It was in the Tutorials section, perhaps because the title started with "Howto".

To disable the screensaver, you can go to the Main Menu, System Preferences, Screensaver. 

You can make changes to the screensaver; if you want to turn it off completely untick the "Activate screensaver when the computer is idle." You can change how long before the screensaver activates with the slider bar on the same page.

Also, when your questions are all answered, we would like you to mark any thread you start as SOLVED. You do this with the 'Thread Tools' link to the top right of the first post. It helps others looking for threads with solutions and allows the helpers to concentrate their efforts on problems still needing a resolution. Thanks.

---

### Post by Brianmorin on 2011-09-16
So if I understand correctly, there is no way to override the time set other than setting the screensaver to activate after, say 2 hours. Nothing more automatic than that??? New to Ubutu! - bri 

> **drs305 said:**
> miamalleena,

Welcome to the Ubuntu forums. I've moved your post to Absolute Beginners. It was in the Tutorials section, perhaps because the title started with "Howto".

To disable the screensaver, you can go to the Main Menu, System Preferences, Screensaver. 

You can make changes to the screensaver; if you want to turn it off completely untick the "Activate screensaver when the computer is idle." You can change how long before the screensaver activates with the slider bar on the same page.

Also, when your questions are all answered, we would like you to mark any thread you start as SOLVED. You do this with the 'Thread Tools' link to the top right of the first post. It helps others looking for threads with solutions and allows the helpers to concentrate their efforts on problems still needing a resolution. Thanks.

---

### Post by Zeta-K on 2011-09-16
> **drs305 said:**
>  if you want to turn it off completely untick the "Activate screensaver when the computer is idle." 
I think that answers your question.

---

### Post by stinkeye on 2011-09-16
Your screen can turn off when idle for 10 mins irrespective
of your screensaver settings due to Energy Star (dpms).

To check for Energy Star enter in the terminal
```
xset -q
```
and look down the bottom for a line
```
DPMS is Enabled
```


To disable this use
```
xset -dpms
```

to enable use
```
xset +dpms
```


If you disable dpms it will be enabled at next boot.
You can add 
```
xset -dpms
```
to startup applications to disable altogether.

---

