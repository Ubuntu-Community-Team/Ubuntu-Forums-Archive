---
title: "HP Laserjet P2035: Printer may not be connected!!"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by rakib.hasan on 2011-09-08
Hi,
I am using HP Laser Jet P2035 as a network printer. 
My OS is Ubuntu 10.10.

For last few days, i am not being able to use the printer.
Error is "Printer may not be connected."

I googled and found that I need to run "hp-check -r", then I did.

I am getting this error:
[B]warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

[/B]This is the only error/warning.[B] HPLIP 3.11.7 is installed.
[/B]
Any help will be appreciated.


- Rakib

---

### Post by relay_man on 2011-09-10
It looks like you need to install an additional module in order for your printer to work correctly.

Look here:

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

follow the "supported printers" link on the left side of the page to find
your printer and get the extra module that you need.

Hope this helps:)

---

