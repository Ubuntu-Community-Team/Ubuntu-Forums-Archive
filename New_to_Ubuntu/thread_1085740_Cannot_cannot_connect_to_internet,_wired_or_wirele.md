---
title: "Cannot cannot connect to internet, wired or wireless"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Magical Tiger on 2009-03-03
The taskbar says that I am connected to the internet with an ~80% connnectability, I cant go to any sites or any thing.

I ran a hardware scan that when it checked the internet came up with the following error message:
Testing your connection to the Internet:

ERROR:root:Could not find def gateway info in /proc
Traceback (most recent call last):
  File "/usr/share/hwtest/scripts/internet_test", line 132, in <module>
    sys.exit(main(sys.argv[1:]))
  File "/usr/share/hwtest/scripts/internet_test", line 118, in main
    host = route.get_default_gateway()
  File "/usr/share/hwtest/scripts/internet_test", line 81, in get_default_gateway
    t1 = self._get_default_gateway_from_bin_route()
  File "/usr/share/hwtest/scripts/internet_test", line 69, in _get_default_gateway_from_bin_route
    if def_gateway:
UnboundLocalError: local variable 'def_gateway' referenced before assignment

I will can get more info later if needed.

---

### Post by Het Irv on 2009-03-03
It sounds like you do not have a Gateway assigned to your computer, or maybe to your router.  Without a gateway, you are connected to the internet, but you can't go anywhere.  Check your router to make sure the settings are correct, it may need to be reset.  If that doesn't work you may need to call your ISP to get the correct settings.

---

