---
title: "Keeping Jaunty Jackalope &lt;3 alive"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by js31 on 2010-09-25
Hey guys,

I wasn't able to find any information on this (on my level), so I just ask:

Due to old hardware, I can't move on to a newer version of Ubuntu (e.g. Jaunty was the last one where the [v4l1-fix]("https://help.ubuntu.com/community/Webcam#Fixing%20Webcam%20issues%20while%20using%20Flash%20since%20Intrepid") worked; and I got other problems like 10.04 stopping at ~80% setup process/different hardware conflicts, which I won't be able to solve any time soon/$).

Ok, I hope this not to be offensive (I mean, just an exotic minority problem), but provided one would be willing to -> what parts of the system should be updated manually, in order to stay safe, and where does one find reliable security bulletines/mailing lists so not to damage something? As far as I can see, it should be safe to keep the kernel patched + webbrowser (Opera), video chat software (Ekiga/Zfone), FTP (NcFTPsyncput) and firewall (ufw) up to date, provided one doesn't exchange office files (except Google Docs cloud viewer), nor e.g. has an email client.

But I'm not experienced, and work in a field where it would be a desaster to find oneself hacked... :redface:

---

### Post by mörgæs on 2010-09-25
If your hardware does not support a full 10.04, you could try Lubuntu:
[http://ubuntuforums.org/showpost.php?p=9834517&postcount=261](http://ubuntuforums.org/showpost.php?p=9834517&postcount=261)

Don't try to keep a system updated without official support. It is almost impossible.

---

### Post by Bachstelze on 2010-09-25
> **js31 said:**
> rovided one would be willing to -> what parts of the system should be updated manually, in order to stay safe,

Everything.

> and where does one find reliable security bulletines/mailing lists so not to damage something?

That's not an easy question to answer, because most security alerts are based on the most recent upstream version of a program, so it is possible that one of your packages are affected by a security vulnerability, but you wouldn't know it because not a lot of people search for security flaws in old versions.

So basically, you would need to track the changes of all the programs you use, and backport all security-related changes to your version. In practice, that would be unfeasible, so the only correct answer is: upgrade.

---

### Post by mörgæs on 2010-09-25
> **Bachstelze said:**
> ... not a lot of people search for security flaws in old versions.

- and the people who do search are not doing it with a good purpose...

---

### Post by js31 on 2010-09-25
Ok, thanks for the advise!

To be true about it, the reason why I considered that was a friend of mine (who's a guru) shaked with laughter about my willingness to upgrade a Debian-based distribution, and I didn't get that what he meant probably was s.th. like "take Slackware or use Windows!". Sometimes it's hard to get what they mean with such, since not always so consequent as it seems... %)

---

### Post by limestone on 2010-09-25
Compile a custom kernel, or switch distro.

---

### Post by Bachstelze on 2010-09-25
> **pont.andersson said:**
> Compile a custom kernel, or switch distro.

There's much more to it than just the kernel...

---

### Post by js31 on 2010-09-25
I guess the latter is the choice, since I need pppoeconf for the DSL modem, and that's unlikely to be included <20mb?

---

### Post by Rocket2DMn on 2010-09-25
Have you filed any bug reports for your hardware compatibility issues? This is the best way to get support for your hardware in future versions of Ubuntu.  Then you can stay upgraded to a supported Ubuntu release.

---

### Post by js31 on 2010-09-25
No, I haven't, yet. Though working several days on this alone, and even tried all sorts of jumper settings (only to find out that it's not related to an error on this side). In part the hardware is damaged, and I'm real surprised the whole system actually still works X) (several times crashed hard drive, defunct DVD I have to open with software command, etc.), so I doubt it would be much of use, or representative.

Btw., I just upgraded to Karmic; when the 9.10-release first came out, the wiki-entry said one should upgrade over a fresh install from live-cd. - Strange, the other way worked fine, and since it takes over the modified v4l-settings, now I'm able to use Flash video, which isn't available with a clean install from CD (package *ld.so.preload-manager* missing in Karmic repository). That completely solves all my problems for 1/2 year till new hardware arrives. -

Thanks to all of you for pointing to this direction! =)

---

