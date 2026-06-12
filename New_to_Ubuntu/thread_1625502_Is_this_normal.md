---
title: "Is this normal?"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by Jeanke on 2010-11-19
Hi,

I was just messing around a bit and stumbled on the following:

```
jan@jan-laptop:/var/log$ tail -f syslog
Nov 19 11:56:42 jan-laptop kernel: [ 4520.378853] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:56:47 jan-laptop kernel: [ 4525.376067] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:56:52 jan-laptop kernel: [ 4530.373282] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:56:57 jan-laptop kernel: [ 4535.370494] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:57:02 jan-laptop kernel: [ 4540.367677] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:57:07 jan-laptop kernel: [ 4545.365073] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:57:12 jan-laptop kernel: [ 4550.361998] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:57:17 jan-laptop kernel: [ 4555.359416] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:57:22 jan-laptop kernel: [ 4560.356387] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:57:27 jan-laptop kernel: [ 4565.353633] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:57:32 jan-laptop kernel: [ 4570.350837] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:57:37 jan-laptop kernel: [ 4575.348023] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:57:42 jan-laptop kernel: [ 4580.345145] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:57:47 jan-laptop kernel: [ 4585.342330] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:57:52 jan-laptop kernel: [ 4590.339539] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:57:57 jan-laptop kernel: [ 4595.336727] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:58:02 jan-laptop kernel: [ 4600.333927] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:58:07 jan-laptop kernel: [ 4605.331114] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:58:17 jan-laptop kernel: [ 4615.325499] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:58:22 jan-laptop kernel: [ 4620.322682] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:58:27 jan-laptop kernel: [ 4625.319885] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:58:32 jan-laptop kernel: [ 4630.317078] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:58:37 jan-laptop kernel: [ 4635.314269] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:58:42 jan-laptop kernel: [ 4640.311451] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Nov 19 11:58:47 jan-laptop kernel: [ 4645.308899] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded 

```

This goes on and on....
Is this normal?

I do not notice anything wrong with performance or anything else.

PC:
Asus UL20FT
Intel® Core&#8482; i3-330UM Dual-Core
3gb DDR3-1333

Ubuntu Maverick
Kernel Linux 2.6.35-22-generic

---

### Post by azertyh on 2010-11-19
hello,
this issue is already reported in launchpad
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/628163](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/628163)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/636045](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/636045)

---

