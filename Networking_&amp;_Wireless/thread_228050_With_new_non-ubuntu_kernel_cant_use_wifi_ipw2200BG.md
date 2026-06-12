---
title: "With new non-ubuntu kernel cant use wifi ipw2200BG"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by jolae on 2006-08-02
Hi, I compiled new kernel image kernel-image-2.6.18-rc1 (coz with this I can finally use ACPI on my notebook Asus M6R).
But with this kernel I cant use my wifi Intel wireless 2200 BG.
With ubuntu kernel 2.6.15-686 I havent problem with WiFi but ACPI doesnt work:))
I can see it hardware list, but I havent this card in Networks.

when I do lshw I will get this:
network 1: UNCLAIMED
etc.

Pls anybody has any suggestion? Thx for ur help
Jolae

---

### Post by tkjacobsen on 2006-08-02
the ubuntu kernel team has patched the ubuntu kernel with loads of wireless drivers. Maybe your wireless driver isn't in the 2.6.18 kernel..

---

### Post by stoft on 2006-08-02
> **jolae said:**
> Hi, I compiled new kernel image kernel-image-2.6.18-rc1 (coz with this I can finally use ACPI on my notebook Asus M6R).
But with this kernel I cant use my wifi Intel wireless 2200 BG.
With ubuntu kernel 2.6.15-686 I havent problem with WiFi but ACPI doesnt work:))
I can see it hardware list, but I havent this card in Networks.

when I do lshw I will get this:
network 1: UNCLAIMED
etc.

Pls anybody has any suggestion? Thx for ur help
Jolae

Try the ipw2200 wiki:
[http://www.ipw2200.com/bin/view/Main/DistDebian](http://www.ipw2200.com/bin/view/Main/DistDebian)

I can't remember if I ran into your particular error but the steps above were enough to get it working on Debian Sarge for me. 

Also try the ipw2200 homepage:
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

---

