---
title: "Touchpad scrolling not working"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by steelfox15 on 2011-02-27
I'm currently running the 32 bit version of 10.10 on my laptop (Dell Latitude E5410), and  the touchpad scrolling doesn't work. I've looked into the issue and it  looks like it's documented here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625)[URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625"]
[/URL] 
After reading through the comments, I found that the issue is fixed in the 2.6.38 kernel. I updated to the 11.04 Alpha and the scrolling does indeed work. Unfortunately, I ran into too many unrelated issues due to the Alpha status of 11.04 so I went back to 10.10.

So what are my options (if any) to get this working on 10.10? I'm pretty new to Ubuntu, but from what I can tell it looks like there are 2.6.38 kernels backported for Lucid, but none for Maverick? Is there any way to use that kernel in Maverick or would there be too many issues? I'd really prefer not to switch to 10.04 if possible.

Would it be possible to just compile the mouse module from the 2.6.38 source and use it in my currently installed kernel or would that cause problems? And if so, could someone help me with that process?

Again, I'm pretty new to this whole thing, so I might be completely off base. Any help would be appreciated! Thanks!

---

### Post by Slave2Metal on 2011-02-27
Have you installed synaptics?  If not look on the first page of Hardware & Laptops and see if you find a solution.

---

