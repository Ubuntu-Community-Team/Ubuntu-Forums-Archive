---
title: "acerhk or successor for amilo pro V3505 needed"
date: 2014-03-25
forum: Networking &amp; Wireless
---

### Post by Bartje on 2014-03-25
Hi all,

I've got a Amilo Pro V3505 which has wireless, but the button doesn't react. A couple of years ago I could get it to work using acerhk drivers.
I upgraded to 13.10 and surprise, surprise, the drivers aren't available anymore, nor maintained so it seems, and the button doesn't work anymore -> no wireless.

So I thought I'd be clever and use an external wireless receiver, but again, surprise, surprise, that little button disables the external receiver too (a tp-link which works out of the box on other machines).
No working button = no wireless, no matter which receiver I connect.

My question now is.. Is there a solution to get that button to work again? I'd love to use that old machine again.

grtz,
Bart

---

### Post by mörgæs on 2014-03-26
Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

