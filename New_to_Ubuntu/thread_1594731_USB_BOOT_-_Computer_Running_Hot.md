---
title: "USB BOOT - Computer Running Hot"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by redsaint182 on 2010-10-12
Hi, I have a question about booting Ubuntu from USB. I have heard that it is slower doing that, and runs faster once installed. Will my computer also run hotter when running from USB? And will run a little cooler once installed? 

My internal laptop fan currently makes a hell of a racket when it turns on, and it usually doesn't need to since I have a cooling pad, but when i was running 10.10 from USB today, then fan was coming on even when only typing in open office and playing one of the songs from the example folder. 

(In windows, doing basic things like playing a video, a song, or typing a text document doesn't do enough to make my computer run over 40, and the fan usually kicks in around 45-50, and the fan comes on during those simple tasks in Ubuntu, should this be a non-issue once I install? Or is it something I will have to worry about?)

(also, as an aside, if you have any recommendations for how to fix the fan racket that doesn't involve replacing the fan, that would be great too lol, but thats not really related to Ubuntu so...)

Thanks in advance :)

---

### Post by 23dornot23d on 2010-10-12
What graphics card and computer are you using ..... ?

ok found the gtaphics card in one of your posts .... geforce 8600m gt

Have you looked at .... the 

System .... Administration .... Nvidia X server Settings  .... and then go to the Thermal readings ....

also are you running Compiz .... with the effects too .... this can make a difference ...

The temp is what matters ...... you should be able to see these screens if the driver is loaded correctly

[IMG]http://img837.imageshack.us/img837/7040/nvall.jpg[/IMG]

( if Windows keeps the temp low without using the fan .... then that is interesting ... which version > ? )

If its a really noisy fan the only thing you can do is to replace it ...... is it under warranty ...... maybe if its excessive they will
replace it ........

---

### Post by redsaint182 on 2010-10-12
> **23dornot23d said:**
> What graphics card and computer are you using ..... ?

ok found the gtaphics card in one of your posts .... geforce 8600m gt

Have you looked at .... the 

System .... Administration .... Nvidia X server Settings  .... and then go to the Thermal readings ....

also are you running Compiz .... with the effects too .... this can make a difference ...

The temp is what matters ...... 

( if Windows keeps the temp low without using the fan .... then that is interesting ... which version > ? )

If its a really noisy fan the only thing you can do is to replace it ...... is it under warranty ...... maybe if its excessive they will
replace it ........

I wasn't running any of the special effects stuff, no (idk what compiz is, but i'm guessing thats the effects?) I don't know if the system had the drivers for the Nvidia card, I had to do the nomodeset sort of thing before starting up)

And I am also running Windows Vista, but I have a cooling pad below my laptop, and that is why it runs around 30-45 instead of 45-55+. I'll try looking at that menu you told me about later though, thanks :)

---

### Post by sandyd on 2010-10-12
> **redsaint182 said:**
> I wasn't running any of the special effects stuff, no (idk what compiz is, but i'm guessing thats the effects?) I don't know if the system had the drivers for the Nvidia card, I had to do the nomodeset sort of thing before starting up)

And I am also running Windows Vista, but I have a cooling pad below my laptop, and that is why it runs around 30-45 instead of 45-55+. I'll try looking at that menu you told me about later though, thanks :)
next time you try ubuntu, and the fans go on, post output of
```

sudo apt-get install acpi
acpi -t
```
you might also want to look into cpufreqd, it scales down the processor speed (and therefore reduces the heat). Windows does this automatically, but Ubuntu's default profile is "performance", where it should be "ondemand" if you want less heat

---

### Post by redsaint182 on 2010-10-14
> **23dornot23d said:**
> 

System .... Administration .... Nvidia X server Settings  .... and then go to the Thermal readings ....

...... you should be able to see these screens if the driver is loaded correctly

[IMG]http://img837.imageshack.us/img837/7040/nvall.jpg[/IMG]

...

Hi, I can not access those menu's. I do not have the driver installed. I do have a question though, as I tried to install the driver -- Can you install these drivers on the USB? Like when you USB boot? Because I haven't done a full install yet, and whenever I try to install the nvidia drivers (or the wireless drivers), I get error messages. I can't remember the error I got when I installed the latest Nvidia driver, but now, when I am on the proprietary drivers page, it says "Driver activated but not in use", and when I click on Nvidia X Server Settings, I get an error that says "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." But I am not sure what it means to "run nvidia xconfig as root" or to restart X server.

Anyways, until next time, thanks, and take care.

---

