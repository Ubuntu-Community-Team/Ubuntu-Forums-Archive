---
title: "Share media from Ubuntu to Xbox 360"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by erik_gil on 2009-03-03
I've been following this guide to set up Ushare, [http://ubuntuforums.org/showthread.php?t=848144]("http://ubuntuforums.org/showthread.php?t=848144")

I got my xbox to pick up Ushare but there is one problem i'm faced with. I don't see any of my music or videos. Could anyone help me out?

this is what my /etc/ushare.conf looks like:

```
# /etc/ushare.conf
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=wlan0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49153

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=1337

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/chino/videos,/home/chino/music

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=yes

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=no

```

---

### Post by erik_gil on 2009-03-03
I think it has to do with my DIR, anyone?

---

### Post by new4me on 2009-03-03
are you using the xbox's new dashboard?

---

### Post by Delvien on 2009-03-03
google: Twonkymedia

---

### Post by simtaalo on 2009-03-03
> **Delvien said:**
> google: Twonkymedia

seems a bit daft to suggest a proprietary program (that is for windows!!) when all he needs is a little help in getting this to work.

@erik - maybe try posting in the original thread you posted the link to, you might get more help there.

sorry i can't help.

---

### Post by philinux on 2009-03-03
Erik,

I assume you've set up sharing of that folder. 
Right click >properties>share.

---

### Post by erik_gil on 2009-03-03
Philinux, you're a genius. Thank you so much, thats what I needed to do. lol

---

### Post by erik_gil on 2009-03-03
also, yes, I am using the new xbox dashboard. Philinux I set up share but still dont see my music. Any suggestions?

---

### Post by erik_gil on 2009-03-04
Problem solved. I got it to work, I just capitalized the M and V and it worked lol. Thank you everyone for the help

---

### Post by philinux on 2009-03-04
Ah yes linux is case sensitive. Glad you're good to go.

I've used mediatomb and fuppes for my PS3. Using fuppes now.

---

