---
title: "Unclaimed Graphics Controller???"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by SeeeingRed on 2009-05-13
I loaded Ubuntu 9.04 onto my laptop about a week ago. Everything has run great except for one thing. I am having a problem with my graphics card driver.

I cannot enable desktop effects. 

When i switched to the newer version i just completely wiped my hard drive and installed 9.04. I was run 8.04 before and my desktop effect worked perfectly fine, so i figure it cannot be my graphics card is to old or shitty. Not to mention the laptop i am using isn't even a year old.

SO, i ran:

```
 sudo lshw -C video
```

And here are my results.

```

  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

```

Also, i have checked in the System > Administration > Hardware Drivers
and here are my results.

[IMG]http://i40.tinypic.com/1zqbqzp.png[/IMG]

Please help!!!

---

### Post by Dynaflow on 2009-05-13
Do this: [http://ubuntuforums.org/showpost.php?p=7132843&postcount=5](http://ubuntuforums.org/showpost.php?p=7132843&postcount=5)

It should cure what ails you.

---

### Post by SeeeingRed on 2009-05-13
Well thanks for that, i tried it and i am sure i did it right. Still no fix.

Hmmm...

Any other ideas?

---

### Post by Dynaflow on 2009-05-13
Yes:  [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by SeeeingRed on 2009-05-13
Man, i don't know what is going on here!

I tried that as well. Everything went fine, but i am not sure about the very last step.

```
sudo /etc/init.d/gdm restart
```

I am not sure what exactly that does, but i do not think it is working properly. I have tried it twice and the second time it was different from the first. My computer re-starts, then it runs the restart thing, and it just stops at one of the lines.

UGH!

:confused:

---

### Post by SeeeingRed on 2009-05-13
bump

---

### Post by Dynaflow on 2009-05-13
That command *should* restart the [Gnome Display Manager]("http://en.wikipedia.org/wiki/GNOME_Display_Manager").  Logging out and logging back in should do the same thing.

If things have somehow become so hosed that you can't get into a graphical environment at all, try rebooting into recovery mode and do the graphics reconfiguration option.

---

