---
title: "GTX-560ti drivers and kernel not loading on boot"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by Hiddenpants on 2011-05-24
I need help getting my Nvidia GTX-560ti drivers to load when I boot into Ubuntu. I'm running 10.04.2 LTS right now and I tried to update my driver to get a higher res out of the card but when I rebooted I can only use low graphics mode, and it's saying both the kernel and the driver are missing. I've tried everything I can think of and read post of similar issues with the older versions but nothing that worked for them had been able to help me. Any help or advice I can get would be greatly appreciated!

---

### Post by conradin on 2011-05-24
Goto NVIDIA's website, and download / use thier driver. It will work better, I promise!

---

### Post by Hiddenpants on 2011-05-24
I did, for the life of me I can't get it to install. It's actually what I was trying to switch the driver version to when all this started. When I enter the Hardware drivers menu it says it's active but not in use. I'm going to feel like such an idiot if the answers right in front of my face. If it helps at all I'm running the 64 bit version.

---

### Post by conradin on 2011-05-24
Did you chmod the script to make it executable?
```

chmod +x /driverLocation

```
and then log into a non graphical session, and kill all the x-server type processes?

Did you get any error messages?

Are you using the 32 bit or 64 bit module?
Links:
[http://www.nvidia.com/object/linux-display-ia32-270.41.19-driver.html](http://www.nvidia.com/object/linux-display-ia32-270.41.19-driver.html)
[http://www.nvidia.com/object/linux-display-amd64-270.41.19-driver.html](http://www.nvidia.com/object/linux-display-amd64-270.41.19-driver.html)

Im using the 32 bit version for the same hardware right now, it works beautifully.

---

### Post by Hiddenpants on 2011-05-25
Yeah I tried to chmod the script and it started to open the driver but stopped after a few seconds and told me that I need to be root to continue. I'm running the 64 bit module if that helps. I looked in system monitor and I don't even see any x server processes running during use. Is there another way I can get at them to kill them? Thanks for the help, it's my first week with Ubuntu (open source in general) so any assistance is great.

---

### Post by Paqman on 2011-05-25
> **Hiddenpants said:**
> I tried to update my driver to get a higher res out of the card

What driver were you using before, and what driver did you try to upgrade to?

I'd strongly suggest just using the recommended driver supplied by the Additional Drivers tool.

---

### Post by morgan141 on 2011-05-25
> **Paqman said:**
> What driver were you using before, and what driver did you try to upgrade to?

I'd strongly suggest just using the recommended driver supplied by the Additional Drivers tool.

Last time I checked drivers for the 5 series graphics cards don't exist in ubuntu. They might be around for 11.04, I haven't checked, but certainly 10.10 and below I've never been able to get a 5 series card working.

---

### Post by Hiddenpants on 2011-05-25
Should I try 11.04 and see if that helps?

---

### Post by conradin on 2011-05-25
lOL, I see from you thumbnail, what is going wrong.
Two things: 1, you will need to run the install script as root.
2. you cant be in, or even have running, a graphical session running.

Heres what you need to do:
Press control + alt + F5
then log in from that terminal. F1 - F9 should work, just so long as its not the one where the GUI is running. 
so, once youre logged in do this:

```

sudo -i


```

that will give you a root termianal session which will last, no more typing sudo in this session. (this is where its saying you need to run as root in the script)

then start killing processes:
```

pkill gdm
pkill gnome
pkill Xserver
pkill X11


```
once all the windowing type stuff is closed you should be able to run the script with out issues. 
change directories to the installer location and run the script:
```

cd /whereEverTheScriptIs
# ./ScritpName

```

A primitive installer will appear. You can navigate with arrows, tab, shift tab, select with space, and proceed with ENTER.

Try that and let us know.

I would bother with natty, its still to troublesome.
what is 

> **Hiddenpants said:**
> Yeah I tried to chmod the script and it started to open the driver but stopped after a few seconds and told me that I need to be root to continue. I'm running the 64 bit module if that helps. I looked in system monitor and I don't even see any x server processes running during use. Is there another way I can get at them to kill them? Thanks for the help, it's my first week with Ubuntu (open source in general) so any assistance is great.

---

### Post by Hiddenpants on 2011-05-26
Worked like a charm. Thanks for all the help guys, great community on this forum!:KS

---

