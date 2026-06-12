---
title: "dual boot Hardy and Lucid"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by mystmaiden on 2011-01-28
I am having some difficulty getting Poser 5 to run under Wine in 10.04 LTS, and since its quite old - so far I haven't found much help. It ran great with Hardy and Wine though so I was wondering about setting up a dual boot with Lucid and Hardy. I've never managed to (successfully) set up a dual boot system though. Is it something that is relatively easy to do since they are both linux?

---

### Post by Nytram on 2011-01-28
I think you'd be fine dual booting, but it's wise to backup data before working with partitions. I believe support for Hardy ends in April so I wouldn't advise using it beyond that date.

---

### Post by mystmaiden on 2011-01-28
The only thing I would use Hardy for would be to run Poser under wine - so continuing to use it after April shouldn't be that much of an issue should it? Everything else I'd use Lucid..

---

### Post by NightwishFan on 2011-01-28
You can install Wine1.0 in Ubuntu Lucid, it is in the repositories and works quite well. I would stick to 10.04.

---

### Post by Nytram on 2011-01-28
> **mystmaiden said:**
> The only thing I would use Hardy for would be to run Poser under wine - so continuing to use it after April shouldn't be that much of an issue should it? Everything else I'd use Lucid..

If I was going to use an unsupported version I'd make sure the internet lead was removed ;) But if you don't use the net on Hardy, such as services, web browser etc then I think you'd be ok.

---

### Post by mystmaiden on 2011-01-28
Thanks for the replies :)

Nightwish, I did try to use wine 1.0 but when I installed winetricks it automatically brought it up to wine 1.2, not sure how to avoid that since I do need to have wine tricks installed.

---

### Post by NightwishFan on 2011-01-28
Winetricks is just a script and you do not need the .deb package installed. A newer version is of course recommended, however if it works it works.
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by mystmaiden on 2011-01-29
Nightwish wrote -

> Winetricks is just a script and you do not need the .deb package installed. Thanks, Nightwish, that's very good to know. Hopefully  it will solve my issues with Poser 5

Edited to add - Nightwish - you rock. I did as you suggested, added vm6 and voila - Poser 5 works like a charm.

---

