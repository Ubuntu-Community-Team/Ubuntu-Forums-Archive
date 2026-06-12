---
title: "Xbox One unable to auto connect after initial connection"
date: 2021-03-19
forum: Networking &amp; Wireless
---

### Post by makem2 on 2021-03-19
I want to use an Xbox One controller with Minecraft in Ubuntu 20.04.

After many connection attempts Bluetooth connects and the controller works correctly.

When I close down and later reboot having first turned on the controller which shows a slow blinking X button, the connection is not made.

If I use the Bluetooth devices method to connect sometime is shows as connected then not connected. When it appears to be connected, if I select disconnect I get an error, not connected.

I have a 10.3KB file at /home/makem/wireless-info.tar.gz but am unable to send it:

```

makem@XPS-13-9300:~$ cat /home/makem/wireless-info.tar.gz | pastebinit
Traceback (most recent call last):
  File "/usr/bin/pastebinit", line 343, in <module>
    content = sys.stdin.read()
  File "/usr/lib/python3.8/codecs.py", line 322, in decode
    (result, consumed) = self._buffer_decode(data, self.errors, final)
UnicodeDecodeError: 'utf-8' codec can't decode byte 0x8b in position 1: invalid start byte
makem@XPS-13-9300:~$

```

The controller I am using is a borrowed one to run tests to decide if I should use this input method. If I decide to use one and so far it appears I could, then I would need to research which to buy as ther are many.

Is it possible to list the details of Ubunto 20.04 Bluetooth requirement to enable me to try to match them before spending money on a controller which may prove incompatible. ie. avoid trial and error.

---

