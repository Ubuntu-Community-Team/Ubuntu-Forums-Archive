---
title: "Ubuntu 10.04 and 10.10 headaches"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by texasboy2084 on 2010-10-30
I have Ubuntu 10.04 on my laptop and thought it is time to switch my desktop over.  But with 10.04 and 10.10 in 32bit or 64bit I get stuck on a black screen. I have uploaded a vid from start to finish to youtube found here [http://www.youtube.com/watch?v=GC5Xi8twy3o](http://www.youtube.com/watch?v=GC5Xi8twy3o) 

My specs are 

vista 64
Phenom 9850 x4 2.5mhz
6 gigs of memory
ati radeon hd 5770 gpu


Any help would be great.

---

### Post by 73ckn797 on 2010-10-31
Search here: [http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

I do not use an ATI graphics card but there have been issues with them. Also do a search on the forums.

---

### Post by Omnomnom on 2010-10-31
Loading up Gnome from the CD can take a while, did you try booting from a USB?

---

### Post by texasboy2084 on 2010-10-31
Havnt tried that yet after work I'm going to pick up one.  I'm skiming through alot of threads but no answers yet. It does seem to be my gpu.

---

### Post by 73ckn797 on 2010-10-31
> **texasboy2084 said:**
> Havnt tried that yet after work I'm going to pick up one.  I'm skiming through alot of threads but no answers yet. It does seem to be my gpu.

Search for info on the "nomodeset" command that can be inserted in the boot menu line.
That search engine I referenced gives this result:
[http://www.google.com/cse?cx=012285703143635244993%3Ai9yr8qlpb18&q=nomodeset&sa=Search&siteurl=crunchbang.org%2Fubuntu-search-engine%2F](http://www.google.com/cse?cx=012285703143635244993%3Ai9yr8qlpb18&q=nomodeset&sa=Search&siteurl=crunchbang.org%2Fubuntu-search-engine%2F)

See what you can find there.

---

### Post by texasboy2084 on 2010-10-31
While at work I kept searching how to fix this and I came across something that did work. If anyone else has this problem with an ATI HD 5770 the steps you take are:

At the screen with the keyboard and man you press any key
Then you press Esc and hit enter to go to the command line
Type "install-live xforcevesa" with no ""
Profit

I'm not sure why it is different but this doesn't work with 10.10, It only works with 10.04 from my experience.

---

