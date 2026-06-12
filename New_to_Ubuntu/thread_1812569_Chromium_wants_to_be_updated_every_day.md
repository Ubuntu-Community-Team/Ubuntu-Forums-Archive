---
title: "Chromium wants to be updated every day"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by Blutkoete on 2011-07-26
Hello!

Since last week, Kubuntu reports available updates to me every day. It's actually the same packages each time:

```
chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg
```

Each time, the system downloads the whole packages, installs them without errors and doesn't show any more updates when I run a*pt-get update*.

The next day (and after a reboot) it shows me again: Available updates, the forementioned packages.

Is there anything I can do about that?

At first I thought that maybe they really changed something two days in a row, but I doubt that they change something every day in the same packages for a week now.

Thank you very much,

Blutkoete

---

### Post by uRock on 2011-07-26
Are you running the updates via the Update Manager or via CLI?

---

### Post by oldos2er on 2011-07-26
That would be normal if you're using the Chromium daily builds PPA.

---

### Post by Blutkoete on 2011-07-26
I've tried both multiple times by now, the effect is the same (or appears to be the same).

Here's a ls chromium* from my /etc/apt/archives/ directory, it actually looks like they are really changing something everytime ... how weird is that.

```

chromium-browser_14.0.832.0~svn20110724r93815-0ubuntu1~ucd1~natty_i386.deb
chromium-codecs-ffmpeg_14.0.832.0~svn20110724r93815-0ubuntu1~ucd1~natty_i386.deb
chromium-browser-l10n_14.0.832.0~svn20110724r93815-0ubuntu1~ucd1~natty_all.deb
chromium-browser_14.0.831.0~svn20110723r93759-0ubuntu1~ucd1~natty_i386.deb
chromium-codecs-ffmpeg_14.0.831.0~svn20110723r93759-0ubuntu1~ucd1~natty_i386.deb
chromium-browser-l10n_14.0.831.0~svn20110723r93759-0ubuntu1~ucd1~natty_all.deb
chromium-browser_14.0.830.0~svn20110722r93513-0ubuntu1~ucd1~natty_i386.deb
chromium-codecs-ffmpeg_14.0.830.0~svn20110722r93513-0ubuntu1~ucd1~natty_i386.deb
chromium-browser-l10n_14.0.830.0~svn20110722r93513-0ubuntu1~ucd1~natty_all.deb
chromium-browser_14.0.825.0~svn20110716r92801-0ubuntu1~ucd1~natty_i386.deb
chromium-codecs-ffmpeg_14.0.825.0~svn20110716r92801-0ubuntu1~ucd1~natty_i386.deb
chromium-browser-l10n_14.0.825.0~svn20110716r92801-0ubuntu1~ucd1~natty_all.deb
chromium-browser_14.0.822.0~svn20110714r92464-0ubuntu1~ucd1~natty_i386.deb
chromium-codecs-ffmpeg_14.0.822.0~svn20110714r92464-0ubuntu1~ucd1~natty_i386.deb
chromium-browser-l10n_14.0.822.0~svn20110714r92464-0ubuntu1~ucd1~natty_all.deb
chromium-browser_14.0.817.0~svn20110711r91986-0ubuntu1~ucd1~natty_i386.deb
chromium-codecs-ffmpeg_14.0.817.0~svn20110711r91986-0ubuntu1~ucd1~natty_i386.deb
chromium-browser-l10n_14.0.817.0~svn20110711r91986-0ubuntu1~ucd1~natty_all.deb
chromium-browser_12.0.742.112~r90304-0ubuntu0.11.04.1_i386.deb
chromium-codecs-ffmpeg_12.0.742.112~r90304-0ubuntu0.11.04.1_i386.deb
chromium-browser-l10n_12.0.742.112~r90304-0ubuntu0.11.04.1_all.deb

```

I'll run another update and look whether a new packages pops up.

---

### Post by Blutkoete on 2011-07-26
I'll check that. I haven't used this computer for two or three months and might have forgotten something like that. Would be kind of embarassing.

---

### Post by Blutkoete on 2011-07-26
I'm ashamed, I really used the daily-build PPA. Argh.

Sorry for wasting your time.

---

### Post by oldos2er on 2011-07-26
No need to be sorry, and you didn't waste my time!  :)

---

