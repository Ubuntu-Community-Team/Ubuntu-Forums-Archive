---
title: "Is there a way to have ALL updates apply automatically, quietly in the background?"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by diablo75 on 2010-03-04
My girlfriend likes using Ubuntu a lot but she's easily irritated by the littlest things in life, and one of those things are the regular updates that Ubuntu alerts her to.  She almost never applies them herself because it's apparently too much of a hassle for her to type in a password.  Every time new updates come down, she says, "I just did this yesterday!  UUUGGHHHH!!!"

So I was wondering if there is a way for the updates to install themselves automatically.

---

### Post by Wootchismo on 2010-03-04
I don't know if there is a way to do it automatically, but I created the following bash file for my girlfriend, though it still requires the interaction of her entering her password:

sudo aptitude update && sudo aptitude safe-upgrade

Save it as updates.sh and change its permissions to be excutable.  Then she can double-click the icon and have it run in the terminal.

---

### Post by kanikilu on 2010-03-04
Well, you could easily set security updates to install automatically, but not all updates:

System > Administration > Software Sources > Updates

Select the "Check for updates: Daily" box and click the "Install security updates without confirmation" radio button.

At least then if she ignores the other updates, the more important security ones will be done...

That's not to say that you *can't* get all updates to install automatically, it just requires a little more work. Check out this page:

[https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo](https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo)

The Advanced Alternatives section lists one way to do this...

---

### Post by sandyd on 2010-03-04
out apt-get upgrade in a cron script?

---

### Post by nothingspecial on 2010-03-04
> **diablo75 said:**
> My girlfriend likes using Ubuntu a lot but she's easily irritated by the littlest things in life

You could take an entirely different approach as I do with my wife and

```
gconf-editor
```

apps > update-notifier

uncheck auto_launch and do it yourself.

---

### Post by kanikilu on 2010-03-04
> out apt-get upgrade in a cron script? Exactly. The link I gave explains how to do that rather than a) assuming the OP knows how to do that, or b) rehashing it here when it's already explained there.

> **nothingspecial said:**
> uncheck auto_launch and do it yourself.

Thanks for the tip - might have to do that...I didn't mind the old notifier in the tray, but the new pop-up window is a little annoying. I'm pretty diligent about updates anywasy, plus I'm subscribed to the USN feed, so know when there's something important to install.

---

### Post by nothingspecial on 2010-03-04
> **kanikilu said:**
> 



Thanks for the tip - might have to do that...I didn't mind the old notifier in the tray, but the new pop-up window is a little annoying. I'm pretty diligent about updates anywasy, plus I'm subscribed to the USN feed, so know when there's something important to install.

I can`t stand it, or the thing that comes up when you try to close a terminal, although I do appreciate their usefulness for new users.

The good thing is that you can easily disable them.

---

### Post by lykwydchykyn on 2010-03-04
> **kanikilu said:**
> Well, you could easily set security updates to install automatically, but not all updates:

System > Administration > Software Sources > Updates

Select the "Check for updates: Daily" box and click the "Install security updates without confirmation" radio button.

At least then if she ignores the other updates, the more important security ones will be done...

That's not to say that you *can't* get all updates to install automatically, it just requires a little more work. Check out this page:

[https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo](https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo)

The Advanced Alternatives section lists one way to do this...

I'll second this recommendation.  I use cron-apt at work on my non-critical or web-exposed servers.  Works flawlessly.

---

### Post by k3lt01 on 2010-03-04
Check the screenshot. If you tick security update automatically it will do that without any apparent hassle to you significant other. All other updates will have to be done manually.

---

### Post by mikewhatever on 2010-03-04
> **diablo75 said:**
> My girlfriend likes using Ubuntu a lot but she's easily irritated by the littlest things in life, and one of those things are the regular updates that Ubuntu alerts her to.  She almost never applies them herself because it's apparently too much of a hassle for her to type in a password.  Every time new updates come down, she says, "I just did this yesterday!  UUUGGHHHH!!!"

So I was wondering if there is a way for the updates to install themselves automatically.

That's just cute. I think you should turn the updates off and check manually once in a while.

---

### Post by koba101 on 2010-03-04
remove her from the sudoer list...which reminds me..i need to preform updates

---

### Post by ptn107 on 2010-03-04
Yes you can have all updates applied automatically.

1) Pop open System -> Administration -> Software Sources.  On the updates tab make sure "Check for updates: 'Daily'" is set and "Install security updates without confirmation" is set.
2) Then go edit '/etc/apt/apt.conf.d/50unattended-upgrades'.  Change:
```
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu karmic-security";
//      "Ubuntu karmic-updates";
};
```
to
```
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu karmic-security";
        "Ubuntu karmic-updates";
};
```
Save and close.  Your done.

---

### Post by diablo75 on 2010-03-04
> **ptn107 said:**
> Yes you can have all updates applied automatically.

1) Pop open System -> Administration -> Software Sources.  On the updates tab make sure "Check for updates: 'Daily'" is set and "Install security updates without confirmation" is set.
2) Then go edit '/etc/apt/apt.conf.d/50unattended-upgrades'.  Change:
```
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu karmic-security";
//      "Ubuntu karmic-updates";
};
```
to
```
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu karmic-security";
        "Ubuntu karmic-updates";
};
```
Save and close.  Your done.

Holy moly!  That's the kind of answer I was looking for.  I'll give it a shot.  THANKS!

---

### Post by 666f6f on 2010-03-09
Very nice, thanks!

---

