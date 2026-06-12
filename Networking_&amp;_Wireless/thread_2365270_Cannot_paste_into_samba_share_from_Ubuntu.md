---
title: "Cannot paste into samba share from Ubuntu"
date: 2017-07-04
forum: Networking &amp; Wireless
---

### Post by bazzieb2 on 2017-07-04
Hi There

I have created a samba share for guest access at my home. We have Mac, linux and windows machines. I can copy, paste and delete from the share using mac and windows, but not from my ubuntu laptop. The share is on a server running Ubuntu Server 16.04.

Here is my Samba file:
[FONT=monospace][COLOR=#000000][movies][/COLOR]
        comment = Movies
        path = /mnt/movies
        browsable = yes
        writable = yes
        read only = no
        guest only = yes
        create mask = 0644
        directory mask = 0755

Am I missing something?

Kind regards

[/FONT]

---

