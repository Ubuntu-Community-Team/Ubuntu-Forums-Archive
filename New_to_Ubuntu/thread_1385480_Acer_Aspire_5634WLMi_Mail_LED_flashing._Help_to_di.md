---
title: "Acer Aspire 5634WLMi Mail LED flashing. Help to diagnose?"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by KingOfMyCastle on 2010-01-19
Hi! I installed Ubuntu 9.10 the other day and all was working well until I either hibernated or suspended the machine (I can't recall which). Now as soon as GRUB loads the orange LED underneath the 'launch email app' button starts flashing. I had an error message that came up during the re-awakening but failed to note it.

Here's a link to a picture of it [IMG]http://paper0k.files.wordpress.com/2008/10/mailled.png?w=300&h=225[/IMG]

Now I haven't installed anything apart from a few games really so I was wondering, as an Ubuntu newbie, how best to attempt to solve this issue. 

What steps does somebody take to try to figure out how to turn this off? I have done the usual 2 hour trawl through this forum and Google but to no avail, it did solve the other 99% of little issues I had though.

---

### Post by KingOfMyCastle on 2010-01-19
Right. It's fixed!

After having a think about it happening even before GRUB had finished loading I decided it was probably a hardware issue. Well I booted XP instead to see if it still happened, and once in I pressed the email button and the orange light disappeared!

So I'm not sure if the initial event was triggered by the Hibernate but it was fixed by going back into XP.

God, XP seems so slugish after a few days on Ubuntu :)

If it reappears due to hibernation I'll create a bug report.

---

### Post by bunkertor7 on 2010-02-06
Same problem here on my Aspire 5685WLHi. I had it since the last update. Definitely a bug.

I wish I could get rid of Windows, but it seems I have to keep it to solve Linux bugs!  :frown:

Ok, now I have to find out why Ubuntu can't leave my bluetooth LED off after startup and why the heck the volume is always off when I log in :x

---

### Post by gvoima on 2010-02-06
Does this give you any result, if you type it into a terminal?
```
ls /proc/driver/acerhk
```

---

### Post by bunkertor7 on 2010-02-06
Hi, thanks for your reply, unfortunately there's no such file on my installation (Ubuntu 9.10).

---

### Post by gvoima on 2010-02-06
Oh..hmm
Try this.
```
lsmod | grep acer
```
If it gives some output, paste it here.

And do you have a bluetooth installed and working?

(Eventhough the topic issue is fixed, I'm just curious) :)

---

### Post by bunkertor7 on 2010-02-06
Hi, I've just installed acerhk and was trying to do something with it ... anyhow, here's the output of lsmod:

acer_wmi               15936  0 
led_class               4096  4 iwl3945,iwlcore,sdhci,acer_wmi

Yes, bluetooth is installed and working. I've read somewhere that to fix my problem it's enough to uninstall the bluetooth deamon/service, but it doesn't look like a proper solution to me.
The bluetooth manager is already disabled in 'preferences -> startup applications', but the LED is always ON after a reboot.

It's like with the volume, it seems that some settings are just lost between reboots and even more settings are lost after an update.

Well, I don't wanna go OT with all this...

---

### Post by s1a on 2010-02-24
Hi, I have the exact same problem, however I don't have windows on it. The problem wasn't there when I loaded 9.10 for the first time. However, I did a lot of updates and now it's always flashing.

Here is the output of lsmod | grep acer
acer_wmi  15936 0 
led_class  4096 4 iwl3945,iwlcore,sdhci,acer_wmi

Someone has any idea how I can disable that led.
Pushing the button doesn't help...

---

