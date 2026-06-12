---
title: "How do I make computer to boot into terminal?"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by damien750 on 2010-12-23
Hey everyone,
I've been using different linux distros for a while now, including linux mint, and ubuntu.
I'm still a beginner using terminal, so I'm trying to learn as much as I can about it. Currently running Maverick.

My question is, normally when I boot my computer up, because I dual boot, My bios gives me an option to boot to windows or linux. When linux is selected, the ubuntu splash screen pops up and I can pick myself as a user.

WHAT I'M TRYING TO DO IS: After I select linux, my computer boots to into the terminal, requiring me to login to the computer via terminal, and then start x window and gnome from there.

Is this possible? How difficult will it be?

Thanks for your help in advance.

---

### Post by sandyd on 2010-12-23
> **damien750 said:**
> Hey everyone,
I've been using different linux distros for a while now, including linux mint, and ubuntu.
I'm still a beginner using terminal, so I'm trying to learn as much as I can about it. Currently running Maverick.

My question is, normally when I boot my computer up, because I dual boot, My bios gives me an option to boot to windows or linux. When linux is selected, the ubuntu splash screen pops up and I can pick myself as a user.

WHAT I'M TRYING TO DO IS: After I select linux, my computer boots to into the terminal, requiring me to login to the computer via terminal, and then start x window and gnome from there.

Is this possible? How difficult will it be?

Thanks for your help in advance.
```

sudo update-rc.d -f gdm remove

```
to start
```

sudo /etc/init.d/gdm start
```

---

### Post by damien750 on 2010-12-23
Thanks sandy d. This code is what I was after, and a quick search of the code gave me the rest of the info I was after.

[http://ubuntuforums.org/showthread.php?t=664199](http://ubuntuforums.org/showthread.php?t=664199)

I guess I didn't know how to really ask the question, heh.

Thanks again.

---

