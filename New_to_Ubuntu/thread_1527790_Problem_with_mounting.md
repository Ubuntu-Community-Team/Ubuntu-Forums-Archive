---
title: "Problem with mounting"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by dokukoneko on 2010-07-09
[FONT=Tahoma][SIZE=2]Konnichiwa :)

I have a problem with mounting..

[/SIZE][/FONT][FONT=Tahoma][SIZE=2]Previously I added a line "shared /mnt/shared vboxsf defaults 0 0" in fstab, 
and I could share a folder between Windows vista (host) and Ubuntu (guest).[/SIZE][/FONT][FONT=Tahoma][SIZE=2]
But after upgrading ubuntu to 10.4, it doesn't work.
Now I don't know what I should do with this.. :confused:

I'm a beginner in Ubuntu.. Could anyone help me?

Thank you

[/SIZE][/FONT]

---

### Post by bodhi.zazen on 2010-07-09
> **dokukoneko said:**
> [FONT=Tahoma][SIZE=2]Konnichiwa :)

I have a problem with mounting..

[/SIZE][/FONT][FONT=Tahoma][SIZE=2]Previously I added a line "shared /mnt/shared vboxsf defaults 0 0" in fstab, 
and I could share a folder between Windows vista (host) and Ubuntu (guest).[/SIZE][/FONT][FONT=Tahoma][SIZE=2]
But after upgrading ubuntu to 10.4, it doesn't work.
Now I don't know what I should do with this.. :confused:

I'm a beginner in Ubuntu.. Could anyone help me?

Thank you

[/SIZE][/FONT]

Did you try (re) installing the guest additions in Ubuntu ? I believe they need to be re-installed with every kernel update.

---

### Post by dokukoneko on 2010-07-09
Thank you! :wink: It works now!
Arigato~!

---

