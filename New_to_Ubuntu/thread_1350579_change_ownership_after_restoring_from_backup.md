---
title: "change ownership after restoring from backup??"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by ray field on 2009-12-09
after my netbook became unuseable, I managed to find a backup from about two months ago, so I restored from that.  everything looked good, but upon bootup, I got this popup over a black screen before autologin:

**User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owne by user and not writable by other users.**

before I mess anything up with a really dumb chown, let me ask y'all experts what I need to do?

---

### Post by nothingspecial on 2009-12-09
Boot into recovery mode or root maintanence shell or whatever they call it and issue these 3 commands.

```
chown -R username:username /home/username
```
```
chmod 644 /home/username/.dmrc
```
```
chmod 644 /home/username/.ICEauthority
```

---

### Post by ray field on 2009-12-09
many thanks.

-rafe t.

---

