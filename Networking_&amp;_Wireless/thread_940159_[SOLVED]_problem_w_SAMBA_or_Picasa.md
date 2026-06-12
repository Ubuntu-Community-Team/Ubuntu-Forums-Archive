---
title: "[SOLVED] problem w/ SAMBA? or Picasa?"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by 40-Dan on 2008-10-06
I originally posted the below in Google's Picasa help forums, but got no response there, so I figured I'd try here.  FWIW, I set up samba using the directions located here - [http://industriousone.com/mounting-windows-shares-ubuntu]("http://industriousone.com/mounting-windows-shares-ubuntu")

It all seems to work great except for the problem outlined below.

> I'm having the same problem under version 3 and 2.7 in Ubuntu.  My
files are stored on a network drive (a windows home server machine)
and mounted to /mnt/photos in ubuntu.  When I try to do a redeye
correction, I get the following error:

"Unable to write redeye due to a disk error.  The disk may be full or
read only."

This could easily be a problem w/ samba and my setup rather than
picasa, as I am a complete linux newb, but I can read and write to the
share using more conventional means.  The only thing that gives me a
problem is picasa.

Has anyone else had this problem, or does anyone have any suggetions?

Thanks
Dan

---

### Post by 40-Dan on 2008-10-07
one bump - then I'll give it a few days.

Thanks

---

### Post by superprash2003 on 2008-10-07
it could be something to do with the current permissions of the folder.. try allowing others to write as well..

---

### Post by paris_alex on 2008-10-08
i do think it's a permission issue as well... include the uid=xxx,gid=xxx options in the fstab line for the windows share.

let me know if it works, if you're not sure how to set this, post your fstab file and i'll try to point you to the right direction (note the 'try', as i'm not an expert either..let's just share our experiences {g}).

---

### Post by 40-Dan on 2008-10-08
Thanks guys.  Adding my uid=username fixed the problem.

I figured had something to do w/ the share instead of Picasa.

---

