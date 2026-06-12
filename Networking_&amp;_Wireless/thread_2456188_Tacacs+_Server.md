---
title: "Tacacs+ Server"
date: 2021-01-06
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2021-01-06
Is there any way to install this on Ubuntu 20?  I tried an 'apt install tacacs+', and it fails.  If not, are there any good alternatives?  I just got a cisco switch, and would like to stand this up.

---

### Post by slickymaster on 2021-01-06
I think that package isn't supported anymore and has been deprecated on Ubuntu 20.04

---

### Post by sniper8752 on 2021-01-06
Is tacas+ still a thing?  Or is there a "better" method?

---

### Post by slickymaster on 2021-01-06
Yes, it's still a thing.

A solution you could use is a docker container with ubuntu 18.04 as a base model to have Tacacs+ running it.

See [https://github.com/llima3000/tacplus_image](https://github.com/llima3000/tacplus_image)

---

