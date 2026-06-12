---
title: "Failing to setup gfire for Pidgin"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Meian on 2009-01-16
When I try to use ./configure, this error message comes up, not sure what to do.

checking for PIDGIN... configure: error: Package requirements (pidgin) were notmet:

Package pidgin was not found in the pkg-config search path.
Perhaps you should add the directory containing `pidgin.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pidgin' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PIDGIN_CFLAGS
and PIDGIN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Help would be greatly appreciated.

---

### Post by jimreynold2nd on 2009-01-16
Did you install the package pidgin-dev?

---

### Post by Meian on 2009-01-16
Yes. T-T

---

### Post by m_duck on 2009-01-16
If you're running Ubuntu, why not use the pre-packages deb files on the [gfire website](http://gfire.site40.net/?page_id=24)?

Download it, then double click to install.

(Make sure you use the correct one for your computer - 32 / 64 bit)

---

### Post by Meian on 2009-01-16
I'm very new to Linux, that worked wonders. Thank you very much. ^^

---

### Post by m_duck on 2009-01-16
No problem, glad I could help :D

---

