---
title: "i have stuffed up"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by cowboy7305 on 2009-03-07
i was playing with screen resolutions  and have put it to high now i cant see any thing and can not get to preferences to undo my mistake 
any help 
the whole top line with applications ect is not there 
many thanks 
i dont want to have to reinstall

---

### Post by ClaytonOT on 2009-03-07
Assuming you're still running the gnome desktop.
> 
gksu gnome-display-properties

---

### Post by cowboy7305 on 2009-03-07
Iam running this from the start up disk

---

### Post by ClaytonOT on 2009-03-07
Ignore this post; (Work-around I suggested would not work)

---

### Post by ClaytonOT on 2009-03-07
Okay rightclick your desktop select create launcher...

Make any name you want....
In the command line put: gnome-display-properties

That should do it.

---

### Post by cowboy7305 on 2009-03-07
i tested it on this live cd start up worked ok 
when i started up my session it did not put any icon on desktop 
i have just looked and the res i put in was 1600-1024

---

### Post by ClaytonOT on 2009-03-07
Anytime you reboot your LiveCD session your custom settings should be removed. I wasn't sure if that would be the case in terms of resolution, but in retrospect a reboot probably would have worked.

So you got everything working now?

---

### Post by cowboy7305 on 2009-03-07
no the resolution has not changed 
i can not run gnome-display-properties on my resolution settings
no icon shows up

---

### Post by ugm6hr on 2009-03-07
> **cowboy7305 said:**
> Iam running this from the start up disk

Then you never installed?

> i dont want to have to reinstall

Hence no need to reinstall.

---

### Post by iamkrazee on 2009-03-07
> **ugm6hr said:**
> Then you never installed?



Hence no need to reinstall.

He means he has it installed, and messed up the installation. And to be able to reply, he's here on the forums using his liveCD.

You can either replace the xorg.conf on the installation with your liveCD one, or start the installation in recovery mode and say dpkg-reconfigure xserver-xorg. I'm on my phone right now. I'll send you the details from my pc in fifteen mins.

---

### Post by cowboy7305 on 2009-03-07
thanks will wait

---

### Post by ugm6hr on 2009-03-07
Sorry - I was a bit confused by that!

How did you change your screen resolution?

Reboot using your HD (i.e. not using LiveCD), then...

If you used System -> Preferences -> Screen resolution:
Press Alt+F2
Enter: gnome-display-properties
You can use Alt+Left click to move the window around

If you used randr:
Press Alt+F2
Enter: gnome-terminal
You can use Alt+Left click to move the window around
Enter: sudo xrandr -s 1280x800
Enter: your_password

---

### Post by iamkrazee on 2009-03-07
run this code :

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by cowboy7305 on 2009-03-07
Got it many many thanks 
i did as ugm6hr said worked great 
once again many thanks

---

### Post by iamkrazee on 2009-03-07
In case if you happen to read this, the next time you do something similar.. try not to do ANYTHING for 15 sec. Because once the resolution is up´ed it waits for 15sec for you to say ¨yes¨ so that it would make that change permanent, else it will revert back to the previous working resolution.

---

### Post by cowboy7305 on 2009-03-07
Ok thanks for advice iamkrazee many thanks once again

---

