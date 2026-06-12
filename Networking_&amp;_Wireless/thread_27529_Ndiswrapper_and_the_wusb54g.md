---
title: "Ndiswrapper and the wusb54g"
date: 2005-04-16
forum: Networking &amp; Wireless
---

### Post by jkndrkn on 2005-04-16
Hello all. New ubuntu user here.

I am currently using ndiswrapper along with wusb54g and official linksys .inf driver files. My connection works *most* of the time.

The network I am on has a fairly weak signal, so short outages are common. Windows handles it fine, but when it happens in hoary, my system hangs shortly afterward.

I'm not sure where to begin looking for problems. The ndiswrapper wiki mentions that the stack size available within hoary is less than that within windows. How would I go about confirming this? Would this require a kernel patch of some sort?

Any solutions within ndiswrapper to keep this from happening?

Thanks in advance.

---

### Post by jkndrkn on 2005-04-20
Turns out the problem wasn't ndiswrapper, it was my nvidia graphics card. Apparently the drivers "nv" and "nvidia" do not work properly, and my system was often hanging.

Thanks.

---

