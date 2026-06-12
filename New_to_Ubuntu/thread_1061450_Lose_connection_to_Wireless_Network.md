---
title: "Lose connection to Wireless Network"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by flylehe on 2009-02-05
Hi,
My laptop had been using a wireless network very well until I changed to another wireless network which I was not sure if I typed the right password. Suddenly my laptop lost the ability of wireless connection and its icon on the panel. I inactivate my wireless driver "Broadcom B43" and activate it, but it doesn't help. Here is what Hardware Testing reports: 

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

Thanks for your help!

---

