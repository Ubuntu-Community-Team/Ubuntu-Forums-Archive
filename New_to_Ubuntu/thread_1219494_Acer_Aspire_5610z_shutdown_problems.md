---
title: "Acer Aspire 5610z shutdown problems"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by oddsocks1013 on 2009-07-21
In April 2009, I installed Ubuntu 8.10 (Intrepid) on a stock Acer Aspire 5610z laptop. I managed to get the wireless, etc, to work, but I've had a few problems with shutdowns since.


 Current system specs:
 Operating System: Ubuntu 8.10 (Intrepid), Linux Kernal 2.6.27-14-generic, GNOME version 2.24.1
 Memory: 2063 MB
Processor: 2x Genuine Intel CPU   T2060 @ 1.60GHz
 Hard Drive: ATA Hitachi HTS54168 [80GB original, 42GB Ubuntu partition (19.2GB still free)]
 

 Since installing Ubuntu, I've never been able to successfully shutdown completely from the terminal: when I try, it goes through everything it should, then the progress bar goes dark except for a bit still lit at the end. The computer will not finish shutting down, and I have to hold the hardware power button down for several seconds in order to turn it off.


 Last week, my father up and decided to upgrade my RAM from the original 512MB that came stock to two 1GB sticks, which the laptop is *supposedly* able to handle. I'm running Windows XP OEM (SP3) on my other hard drive partition, and there are no new problems there. On the Ubuntu partition, however, after the upgrade occurred, I started having a rather bizarre shutdown/restart problem. Since the upgrade, attempting to shut down or restart the entire system from the shutdown menu causes it to shoot me back to the login screen. I can suspend or hibernate the system alright, but shutting down from the terminal doesn't work (since it never has), so the only method I currently have to actually turn the system off or reboot is the hardware power button.
 

 I can't shut down from the login screen, either, because the option to do so has spontaneously vanished. Actually, all shutdown options (suspend, hibernate, restart, shutdown) have vanished from the login screen.  
 

 I really have no idea what, if anything, I did, to cause the new problems. The memory upgrade would seem to be the problem, because the new restart/shutdown problems didn't start occurring until then. 



Any permanent fix would be great, any assistance at all would be helpful.

---

### Post by c0mput3r_n3rD on 2009-07-21
You can alsways shutdown by:
```

sudo shutdown -h now

```
and restart:
```

sudo shutdown -r now

```

---

### Post by zeroseven0183 on 2009-07-22
You can check if you still have the problems by downgrading to 512MB RAM again. See if the problem has been eliminated. If not, then there's a different cause.

But I doubt that the problem is caused by the upgrade.

What were the commands you're typing in Terminal to shut down? Are they the same with what c0mput3r_n3rD posted?

---

### Post by rutz3n on 2009-09-02
I have an Acer Aspire 6930G.

I have 4GB RAM and I have the SAME problem.

When clicked to restart or shutdown, the shutdown bar runs perfectly. However, at the end, the computer does not shutdown and I must hold the hardware power button key in order to shut down the computer.

IT SUCKS! I'm already having problems with my HD because of these bad shutdows!!

Please!! Need a solution...

I'm with this problem since I installed Ubuntu on my laptop. It means version 8.04, 8.10 and now 9.04. All have the same problem.

Any ideas??

thanks

---

### Post by oddsocks1013 on 2009-11-12
Hi,

I used the commands that you suggested and they worked to make it shut down (finally!). I also upgraded to 9.10 Karmic earlier this month and the problem went away entirely.

I'm going to chalk it up to this particular laptop being made of fail, I think.

Thanks for the suggestions!

-oddsocks

---

