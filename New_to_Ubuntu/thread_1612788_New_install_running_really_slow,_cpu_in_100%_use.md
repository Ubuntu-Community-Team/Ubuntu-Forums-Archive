---
title: "New install running really slow, cpu in 100% use"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by Ima2k on 2010-11-03
Hey all, just installed Ubuntu 10.10 i686 and I'm getting really slow loading times.
It started from the beginning of the install, I noticed things were going really slow (a min to delete each lang pack etc) but didn't think mucvh of it as it was my first install. But when I got into the OS after install, it was still running really slow.

Some loading times - 
1 hour 15m to install from live CD 
1 min 50 seconds from loader to login
55 seconds from login to desktop
30 seconds on desktop loading
15 seconds to open a new blank file
30 seconds to log in after logout
opening Mozilla 15ish seconds. 5 cores went to 100%
1 min 20seconds to shutdown

Atleast 3 of my 8 cores are 100% all the time, this is on boot up. I'm running a Core i7 920 2.67 ghz, 6gb ddr3 ram and a Western Digital black 500gb hdd. The partition is 76gb ext4, dual booted with Windows 7 x64.

A pic of System Monitor: 



Edit - sorry for the high res pic, I don't know how to convert a png to a jpg yet, yet alone resize an image. As for the hdd icon up the top right, that is a non system drive that is failing, it has nothing to do with the install.

When I installed Ubuntu I didn't associate a swap area, but I did make one under the disk utility, but I don't think it's being detected as per that pic.

I haven't installed any updates yet, so maybe that might be the problem, I'm updating now, but on a very slow connection.


Thanks a lot.

---

### Post by cariboo on 2010-11-03
Open a terminal and run top, that will give a better sense of what is using all your resources. The output should look something like the attached screen shot

---

### Post by beew on 2010-11-03
Well if it takes an hour and 15 minutes to install there is something wrong other than some Ubuntu processes using up resources.

---

### Post by DooM55 on 2010-11-03
hi 

open terminal (ctrl+alt+t)

use command

```

$ kill -9

```

to end process :guitar:

---

### Post by sikander3786 on 2010-11-03
System Monitor itself eats up a lot of resources (graphs etc), so the output from top as already suggested will be really helpful.

---

### Post by Ima2k on 2010-11-03
> **cariboo907 said:**
> Open a terminal and run top, that will give a  better sense of what is using all your resources. The output should  look something like the attached screen shot

Alright here you go - [http://i.imgur.com/yV6sK.png](http://i.imgur.com/yV6sK.png)


> **DooM55 said:**
> hi 

open terminal (ctrl+alt+t)

use command

```

$ kill -9

```to end process :guitar:
ah, what is that killing?

> **beew said:**
> Well if it takes an hour and 15 minutes to install  there is something wrong other than some Ubuntu processes using up  resources.

Like I said, it was my first Linux install and I'm used to longish Microsoft installations.

---

### Post by beew on 2010-11-03
Well it took me about 15 minutes to install 10.10 from a usb, probably takes 20-25 minutes if you use a live CD. That's why I think there is something very wrong even before Ubuntu processes can use up your resources,--which are plenty.

---

### Post by DooM55 on 2010-11-03
hi

open terminal write 
```
man kill
```
to more info :guitar:

---

### Post by sikander3786 on 2010-11-03
Seems like you ran *top* the same time when gnome-system-monitor was running and it tops the charts with 37% CPU usage. Please close it and post again. Everything else seems fine to me. Xorg is using a bit unusual resources but it will be confirmed in the next post.

---

### Post by Ima2k on 2010-11-03
> **sikander3786 said:**
> Seems like you ran *top* the same time when gnome-system-monitor was running and it tops the charts with 37% CPU usage. Please close it and post again. Everything else seems fine to me. Xorg is using a bit unusual resources but it will be confirmed in the next post.

Alright, sorry about that, here is another pic. [http://i.imgur.com/ohm8S.png](http://i.imgur.com/ohm8S.png)

Could any of this be related to not having a swap? I made one under disk utility, but it's not being detected.

Thanks

---

### Post by sikander3786 on 2010-11-03
Total CPU usage is 3.3. Pretty much free memory available. I fell it is not a problem associtated to resources in any way.

Besides that delay in boot, loading etc, is there some other problem like laggy windows? Or anything else worth mentioning?

---

### Post by Ima2k on 2010-11-03
> **sikander3786 said:**
> Total CPU usage is 3.3. Pretty much free memory available. I fell it is not a problem associtated to resources in any way.

Besides that delay in boot, loading etc, is there some other problem like laggy windows? Or anything else worth mentioning?

Everything is laggy, the entire system is slow, loading a window is slow, changing a desktop is slow, it's like a slide show as it changes from the last desktop to the next.

I'm about to reinstall now, hopefully it works right.

---

### Post by sikander3786 on 2010-11-03
Did you enable compiz? If yes try switching to metacity and see if it improves the performance. Then we can work to sort out that compiz problem.

Press Alt + F2 and type

```
metacity --replace
```

in the box that appears. See if it changes anything.

---

### Post by Ima2k on 2010-11-03
> **sikander3786 said:**
> Did you enable compiz? If yes try switching to metacity and see if it improves the performance. Then we can work to sort out that compiz problem.

Press Alt + F2 and type

```
metacity --replace
```in the box that appears. See if it changes anything.

I don't think I did unless it did it automatically, I've just reinstalled Ubuntu, reinstall took 20 mins, but this load up took about 3 mins, about 30 seconds from log in screen. Hopefully was just a first run, things seem to be running faster and loading times are a lot better. Hopefully this is it, I can live with a long boot up, but that's about it

Thanks a lot for your help.

---

