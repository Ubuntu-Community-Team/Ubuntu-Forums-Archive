---
title: "Won't Boot, believe it's a problem with GMA 950"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by Rick 250 on 2010-09-20
When I boot up it just is a black screen with a white cursor blinking on the top left of the screen.  I've been wanting to switch over to Ubuntu for a long time, but everytime I try, I get similar issues.  I'm using an Acer Aspire One AOD250-1955, it has an Intel Atom N280, 2GB RAM, Intel GMA 950.  

Background info:
Ubuntu Netbook Remix used to work with this computer around 7-8 months ago, but then when I tried upgrading 10.04 and UNE both have the boot problem described.  Now I've been trying 9.10 and UNR again, and those don't want to work, I've tried WUBI with 9.10 and 10.04, nothing seems to work anymore.  I once had a weird problem with UNE that I had to keep the flash drive which I had installed UNE from in the netbook for it to boot correctly, but it would still only work sometimes.

So how can I get Ubuntu 10.04 working on my netbook?

---

### Post by mikewhatever on 2010-09-20
This is tricky. I think gma950 is well supported under Linux, and the problem is possibly in the booting or in the iso to usb burning. How exactly did you make the bootable flash drive? Did you change the boot sequence in the BIOS to boot from USB?

---

### Post by snowpine on 2010-09-20
gma950 is well supported, the problem lies elsewhere.

I'd suggest running some hardware diagnostics such as 'memtest' from the Live CD.

---

