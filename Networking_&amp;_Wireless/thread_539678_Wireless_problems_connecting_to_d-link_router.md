---
title: "Wireless problems connecting to d-link router"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by Ultra Magnus on 2007-08-31
Hi, I've been having this problem for a while and its really confusing.

I can connect to pretty much all networks that I have tried, including public wifi points and stuff except for the network at home. For some reason I can't see my network on Ubuntu - I have a d-link router and XP works fine with it as does vista - I once saw the network pop up but it disappered and doing "iwlist scanning" produced no results. Any ideas?

Thanks

---

### Post by noob12 on 2007-09-01
Most routers these days are 802.11b/g mode, and normally they run mixed-mode.  If you've set your home router to run only g mode but the card in your Ubuntu is a b-only card or an a/b card, this could explain what you are seeing.  But that's kind of a wild-a** guess.

If I didn't get the hole-in-one with that, then I'd need more info for more ideas, like the output of these commands.

What kind of device you have and what driver you're using:
```

sudo lshw -C network

```

When in the vicinity of your router, gather these:
```

sudo lshw -C network

sudo iwconfig

sudo iwlist scan

```

Note is that you really need to do **sudo iwlist scan**.   As non-root, you just see the prior scan results.

---

