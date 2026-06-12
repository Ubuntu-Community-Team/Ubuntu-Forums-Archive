---
title: "ureadahead status 4 problem"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by akelsall on 2010-07-03
Just passing along a fix I came across for a problem I just experienced.

In short, when I booted, it went through its normal boot sequence, but then got stuck. I saw several messages saying:

[INDENT]init:ureadahead-other main processes
terminated with status 4[/INDENT]

After googling a bit, I was lucky to find a fix that worked for me. Someone mentioned that this sometimes occurs when you have manually adjusted fstab to mount other partitions (other than the one's it mounts by default). Well, I had recently done just that (mounting three partitions on a secondary DRIVE). 

I booted to the LiveCD, opened up /etc/fstab, and "commented out" the three lines I had added (you comment out a line by placing a "#" symbol in front of it).

That did the trick.

---

