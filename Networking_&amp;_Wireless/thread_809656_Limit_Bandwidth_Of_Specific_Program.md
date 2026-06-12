---
title: "Limit Bandwidth Of Specific Program"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by Thee_Baron_ on 2008-05-27
Hello, I'm with an ISP that limits the amount I can download from 4-9pm everyday. During this time when I downloaded stuff (on Windows XP) I would limit my upload to 30kb/s and 100kb/s down. I would like to limit the the speed of a specific program and don't know if this is possible.

Any help would be great!
Thanks!

---

### Post by Kebabman on 2008-05-27
You can do this using the 'trickle' program. Install it using apt/synaptic and have a look at the man page.

-d rate      Limit the download bandwidth consumption to rate KB/s.
                                
-u rate      Limit the upload bandwidth consumption to rate KB/s.

The two command line arguments above should help you achieve what you want.

---

