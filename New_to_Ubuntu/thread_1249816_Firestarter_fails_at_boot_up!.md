---
title: "Firestarter fails at boot up!"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-08-25
Hello,

When installing Firestarter, it said that it starts itself up automatically and runs in the background without having to launch the GUI. But when I start my computer, in the terminal where all the booting info is listed, there it says that Firestarter launch failed.

Did I set it up wrong or do I need to specify to my computer to start at boot up?

Thanks!

---

### Post by kansasnoob on 2009-08-25
> **sylvainrb said:**
> Hello,

When installing Firestarter, it said that it starts itself up automatically and runs in the background without having to launch the GUI. But when I start my computer, in the terminal where all the booting info is listed, there it says that Firestarter launch failed.

Did I set it up wrong or do I need to specify to my computer to start at boot up?

Thanks!

Probably not. I began with Gutsy, and in both Gutsy and Hardy I even spent the time to edit 'sudoers' so the Firestarter gui launched in the panel at startup.

I later decided this was not only foolish but possibly created a security flaw. I had for a time even thought Firestarter was no longer in development but I've since noticed some "activity", but anyway 'ufw' is now installed by default and if you like a gui you can install 'gufw' from synaptic or run the command:

```
sudo apt-get install gufw
```

But, whether you're using Firestarter or Gufw (which will show up in System > Administration > Firewall Config.) they are both just "front-ends" to help configure iptables, so once they're set - you're set!

Shameless screenshot of Gufw:

[ATTACH]126240[/ATTACH]

---

### Post by sylvainrb on 2009-08-25
I had ufw before, though I didn't know about gufw. Thanks for the info! I switched to firestarter since when researching for different firewalls, that's the name that came up most of the time so I thought it was better than ufw...

Do you know?

---

### Post by kansasnoob on 2009-08-25
I honestly think either Firestarter or Gufw are fine.

If you have text during boot (rather than a quiet boot) you'll see either fail until X starts because they are gui's.

Using just the command line (terminal) you can always run:

```
sudo ufw enable

```

And if you want to restore the defaults:

```
ufw default allow
```

```
ufw default deny
```

---

### Post by 3rdalbum on 2009-08-26
> **sylvainrb said:**
> I had ufw before, though I didn't know about gufw. Thanks for the info! I switched to firestarter since when researching for different firewalls, that's the name that came up most of the time so I thought it was better than ufw...

Do you know?

Firestarter and gUFW are just configuration panels for the same firewall, which is built-in to the kernel.

If you need a personal firewall (most people don't if they already have a firewall inside their ADSL modem/router), then you should configure it with gUFW. There are a number of issues with Firestarter that make it less optimal for desktop users.

---

### Post by sylvainrb on 2009-08-26
Ok then I guess I'll go back with gufw. There is a firewall inside my router but for some reason I don't totally "trust" it, but then again I don't know much about firewalls...

---

