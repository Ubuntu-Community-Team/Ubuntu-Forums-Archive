---
title: "Auto starting banshee"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-08-06
Ive added the command```
banshee1 --hide
```to my list of start up applications, i think this is supposed to make banshee start on login and start minimised to the tray, anyone have any ideas why it starts but open a full window, what am i doing wrong, i tried a few different commands but im not sure which one will work, also i tried to get it to play automatically and that didnt work either. 
Any ideas?

---

### Post by Repus on 2009-08-06
I don't have banshee installed myself but I know from my past experience that not all programs support the same hidden/minimised flag. I've seen variation to include -h, --h, -hidden, -minimised. If you haven't already, type "banshee -help" to see if it has a specific flag to start hidden or minimised

hope this helps

---

### Post by CaptainMark on 2009-08-06
yes it deos and this should be the correct command, thats what threw me. Im so confused
update:```
mark@mark-desktop:~$ banshee --help-ui
Usage: banshee-1 [options...] [files|URIs...]

User Interface Options

  --show|--present      Present the user interface on the active workspace
  --hide                Hide the user interface
  --no-present          Do not present the user interface, regardless of any other options

mark@mark-desktop:~$ 


```

---

