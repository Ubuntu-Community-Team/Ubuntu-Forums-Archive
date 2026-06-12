---
title: "sharing files between ubuntu and a ubuntu/windows PC"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by ianb72 on 2010-11-16
Can any one tell me how I share files between my laptop, which is a clean install of Ubuntu, and my main PC which is a dual boot of Ubuntu and windows xp.

Due to the dual boot I have most of my old files on the windows part of the dual boot but I want to put them on to my Ubuntu laptop.

Can this be done using a network cable rather than the wireless connection, as it much quicker and I have about 200Gb to transfer and I'd love to play on my PS3 online sometime this week!! Lol

Also when I try and boot into Ubuntu on the dual boot pc and copy the files across to my Ubuntu Laptop it comes up with an error
Operation not supported by backend -- see screenshot

---

### Post by aeiah on 2010-11-16
if you're transferring that amount of files, you should use something like rsync. it'll syncronise folders.. so you can start/stop/resume etc quite easily and it'll make sure everything has transferred properly.

rsync is a command line application and will already be on your linux systems, but there are gui tools as well that incorporate rsync (like grsync, or zynk) but ive never used them. there's also rsync for windows, but this will be a lot easier if you're using ubuntu on your dual boot pc.

rsync can sync over the ssh protocol, so you'd need the ssh daemon (server) running on one of your computers.

if it's possible to plug both of your computers into your router with network cables then this is far preferable to plugging them into eachother directly, and of course is faster than relying on your wifi. you could of course unplug your router and take it to your desktop rather than the other way around, although you won't be able to use the internet whilst doing that so it'd be something you left running over night.

your basic rsync syntax, running on your source device (the one with the files) is:
```

rsync -a -n /path/to/source/ username@target.ip:/path/to/destination/

```

the '-a' flag means archive, and the -n flag means dry run. ie, this won't actually do anything for real, it'll just show an output like it's working. if you're confident it's acting like it should you can remove the '-n' flag and it'll do it for real.

i know this seems more complicated than mounting a shared folder and just copy/pasting but with 200GB of files you want to make sure everything goes across ok and also have the option of stopping and starting the process as you wish.

---

### Post by pricetech on 2010-11-16
I have nothing to add except that I would go ahead and add openssh server to both computers first.  Then get WinSCP for your windows install.  That will let you access the files in the future.

---

