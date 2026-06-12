---
title: "Seamonkey"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by h8uthemost on 2009-03-18
How exactly can I get Synaptics to get the latest stable build of Seamonkey? It's stuck on version 1.1.12 I believe. So is there a pretty easy to get Synaptics to get the latest version?

Thank you.

---

### Post by the wombat on 2009-03-18
Have you checked the update manager? if the repositories are up to date you should be able to sudo apt-get or sudo upgrade if the version is too old.Any particular reason for choosing seamonkey?

---

### Post by kansasnoob on 2009-03-18
Use Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

It's simple! Just download it to your Desktop (or place of choice), then double click the icon/folder and Ubuntuzilla will install to synaptic.

Then, for Seamonkey, go to terminal and run the command:

```
ubuntuzilla.py -a install -p seamonkey
```

Ubuntuzilla is supported here on the forums:

[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

---

### Post by nanotube on 2009-03-19
> **h8uthemost said:**
> How exactly can I get Synaptics to get the latest stable build of Seamonkey? It's stuck on version 1.1.12 I believe. So is there a pretty easy to get Synaptics to get the latest version?

Thank you.

the ubuntu repos don't update seamonkey with any haste, so you're unlikely to see a newer seamonkey in the official repos any time soon.

your best bet is the ubuntuzilla project.

---

### Post by h8uthemost on 2009-03-19
Thank you guys for the info on Ubuntuzilla. It seems like a great app. I got it installed just fine. But when I try getting the newest seamonkey version, it goes through the downloading process just fine, but at the very end I get this error:

```
Creating link to Seamonkey in /usr/bin/seamonkey

dpkg-divert: `local diversion of /usr/bin/seamonkey to /usr/bin/seamonkey.ubuntu' clashes with `local diversion of /usr/bin/seamo to /usr/bin/seamonkey.ubuntu'
sudo dpkg-divert --divert /usr/bin/seamonkey.ubuntu --rename /usr/bin/seamonkey
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1146, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 215, in start
    si.start()
  File "/usr/local/bin/ubuntuzilla.py", line 236, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 611, in install
    self.linkLauncher()
  File "/usr/local/bin/ubuntuzilla.py", line 977, in linkLauncher
    self.util.execSystemCommand(executionstring="sudo dpkg-divert --divert /usr/bin/seamonkey.ubuntu --rename /usr/bin/seamonkey")
  File "/usr/local/bin/ubuntuzilla.py", line 140, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, http://ubuntuzilla.sourceforge.net/
```

So I'm not sure what the problem is. But I'll try again later and maybe it will have fixed itself.

---

### Post by nanotube on 2009-03-19
Hi
can you run this command from a terminal manually, and see what it says? :

```
sudo dpkg-divert --divert /usr/bin/seamonkey.ubuntu --rename /usr/bin/seamonkey
```

---

