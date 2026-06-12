---
title: "automatic shutdown"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by nyuwa on 2009-05-12
When I order Linux (just yesterday installed Ubuntu 9.04) to "shutdown", the software "is halted", but the computer remains ON. And since it is "somehow" active, the monitor does not switch to standby mode either.

Both in Windows and with Mac I used to turn the computer off, by selecting "shutdown". Why do I have to dive under the desk to switch the power of manually with Linux. Is there a way to convince Ubuntu, that I want to turn the power of the computer OFF?

---

### Post by kpkeerthi on 2009-05-12
There are some workarounds in this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302452").

---

### Post by kozlovsk on 2009-05-12
Any BIOS related settings?

---

### Post by nyuwa on 2009-05-13
> **kozlovsk said:**
> Any BIOS related settings?

I don't know, if there are any such specific settings. While that thing ran on Windows, it did work fine for years.

Now, when I select "shutdown" (with Ubuntu 9.04), I get a black screen and in the left upper corner:
[1776,361626] System halted

Wonderful. But the computer does NOT power down. It remains turned on forever and so does the monitor, which does NOT switch into stand-by.

Please, don't tell me, that this is in Linux something absolutely essential for security reasons. It is NO fun having to dive under the desk and manually switch off the computer EVERY  time.

---

### Post by kpkeerthi on 2009-05-13
Open a bug report & provide your specs as much as you could. Hopefully, the devs will address it in a future release.

---

### Post by Cheesemill on 2009-05-13
How old is your machine? I know that on a couple of old laptops that I have Ubuntu doesn't activate ACPI by default.
I had to add the acpi=force directive to the kernel at boot time to get them to shutdown/reboot properly.

Cheesemill

---

