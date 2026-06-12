---
title: "HELP!  Crashed during upgrade"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by solarpenguin on 2010-09-14
Hi.

A few months ago I got a second-hand computer which had Ubuntu on it instead of Windows.  Not having the faintest idea how to take it off and replace it with proper Windows, I decided to stick with it, and I'm starting to like it.

Yesterday I tried to upgrade to the Lucid version of Ubuntu.  All went well, until the display was showing 21 minutes to go, then it suddenly crashed, dumping me in a text-only console log-in screen.

I logged in at that screen, hoping the upgrade would continue once I'd done it.  It didn't.  I can use the console all right (or at least I could if I could remember all the commands!) but I can't get into the Gnome desktop at all.

What do I need to do to complete the Lucid uprade?  Or failing that, downgrade back to the non-Lucid version?  Is there a simple command (or more likely a long, complicated command) that I could give to fix it?

Most of the threads about this seem to assume the user has had the experience of installing Ubuntu on the machine in the first place.  I don't, like I said, so I haven't got the faintest idea what they're talking about when they mention "partitions" and things like that.

---

### Post by amjjawad on 2010-09-14
> **solarpenguin said:**
> Hi.

A few months ago I got a second-hand computer which had Ubuntu on it instead of Windows.  Not having the faintest idea how to take it off and replace it with proper Windows, I decided to stick with it, and I'm starting to like it.

Yesterday I tried to upgrade to the Lucid version of Ubuntu.  All went well, until the display was showing 21 minutes to go, then it suddenly crashed, dumping me in a text-only console log-in screen.

I logged in at that screen, hoping the upgrade would continue once I'd done it.  It didn't.  I can use the console all right (or at least I could if I could remember all the commands!) but I can't get into the Gnome desktop at all.

What do I need to do to complete the Lucid uprade?  Or failing that, downgrade back to the non-Lucid version?  Is there a simple command (or more likely a long, complicated command) that I could give to fix it?

Most of the threads about this seem to assume the user has had the experience of installing Ubuntu on the machine in the first place.  I don't, like I said, so I haven't got the faintest idea what they're talking about when they mention "partitions" and things like that.

I guess you can access the internet from another PC/Laptop. If so, then you need to go to:

[www.ubuntu.com](www.ubuntu.com)

and from there, try to download Ubuntu and then create a CD or USB to boot from. Everything is explained from there.

Try it and then post back so I can take you through the next step!

---

### Post by sikander3786 on 2010-09-14
Re-installation will always be an option but before that go through the following commands. Make sure your Ubuntu box is connected to the internet.

```

sudo apt-get clean

```

```

sudo apt-get update

```

```

sudo apt-get upgrade

```

If the above commands give some error, try

```

sudo apt-get install -f

```

```

sudo dpkg --configure -a

```

If it still doesn't fix the problem, post back the exact error message.

---

### Post by solarpenguin on 2010-09-17
Thanks for the suggestions.  I'll try them this weekend, and let you know how it goes.

---

### Post by solarpenguin on 2010-09-19
Sikander, the "sudo dpkg --configure -a" did the trick.

Thanks.

---

### Post by sikander3786 on 2010-09-20
> **solarpenguin said:**
> Sikander, the "sudo dpkg --configure -a" did the trick.

Thanks.
Nice to hear that. Happy Ubuntu.

Regards.

---

