---
title: "kworker using 100% CPU and over 90°C when reconnecting lost WiFi connection"
date: 2016-08-14
forum: Networking &amp; Wireless
---

### Post by leozinho29_eu on 2016-08-14
Hello

When I use the WiFi on my notebook and it loses connection, it may  reconnect soon later, it may disconnect or it may keep trying to  reconnect forever and then use 100% CPU. The issue happens on this third  case: once that eternal reconnection attempt happens, the only 2 ways  it will stop using 100% CPU is by rebooting the computer or if (by a  miracle) it reconnects. 

When this happens, not only I become unable to connect to any wireless  network, but the notebook's temperature gets pretty high: after 2  minutes, it easily raises to 90°C. Nothing makes the temperature raise  so quickly, even other CPU intensive processes which use 100% all the  time. As a workaround to solve this if I can't reboot the notebook, I  change the CPU frequency to 1 GHz, so the temperature gets lower. But my  father don't know how to do this, so if this happens when he is using,  the only thing he can do is to restart the computer. 

When looking at the result of the command top when the bug happens, there are 2 different kworker processes that demands high CPU.

As consequence of this, the user can no longer use wireless connections and the temperature gets dangerously high. 

The notebook is a Asus M2400N with a 1.7 GHz processor and 1248 MB of  RAM. Its wireless device is a Intel Corporation PRO/Wireless 2200BG  [Calexico2] Network Connection (rev 05). All versions of Lubuntu which I  installed (from 12.04 to 16.04) present this issue.

Thank you.

---

### Post by bearlake on 2016-08-15
Have you tried to boot into your BIOS and hit save on the way out?

This is the first thing to try with kworker hogging all the resources. 

You still may have another issue but try the above first.

---

### Post by leozinho29_eu on 2016-08-15
Hello

Booting into BIOS would be to press Del or F2 at the screen loading the drives and memories, then should I save and exit? If these are the steps, then it didn't work. 

I have found some help pages about, especially this: [https://lkml.org/lkml/2011/3/31/68](https://lkml.org/lkml/2011/3/31/68)

One example cited is one about wireless. Now I know how to find detailed information about the rogue kworker processes, I will try to reproduce the bug (cause a wireless disconnect).

---

### Post by leozinho29_eu on 2016-08-23
I have discovered a way to recover the system after the error happens: just suspend the system and restore, then the bug stops. The dmesg informations from before the bug, after the bug and suspending the systems give informations which I believe that are important.

Relevant dmesg messages after boot, when the notebook was performing normally. Note how many problems related to wireless card have happened though more than 2 hours, still the notebook was working well:

```
[  646.079453] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[ 1090.385596] perf interrupt took too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 1606.040721] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[ 2566.068472] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[ 3526.093461] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[ 4486.074919] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[ 6406.105075] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[ 7366.065743] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[ 8326.112600] ipw2200: Failed to send ASSOCIATE: Already sending a command.
[ 9165.160087] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[ 9286.096584] ipw2200: Failed to send ASSOCIATE: Already sending a command.
```

The dmesg messages when the error started:

```
[10062.785770] IPv6: ADDRCONF(NETDEV_UP): wlp1s5: link is not ready
[10089.023440] IPv6: ADDRCONF(NETDEV_UP): wlp1s5: link is not ready
[10103.684133] IPv6: ADDRCONF(NETDEV_UP): wlp1s5: link is not ready
```

Then I tested and put the notebook to suspend. I noticed some particular lines which show a problem: 

```
[10129.517088] wlp1s5: Going into suspend...
[10129.536344] ipw2200: Firmware error detected.  Restarting.
[10129.567125] ipw2200: Unable to load ucode: -22
[10129.567133] ipw2200: Unable to load firmware: -22
[10129.567133] ipw2200: Failed to up device
```

Is this a error related to drivers?

---

### Post by leozinho29_eu on 2016-08-27
Hello

I believe I have solved the issue, I have made tests and I can no longer reproduce the bug. When I trigger the event (thought connecting to a network it was already trying to reconnect, as example), it uses 100% CPU very briefly, no longer all the time. When suspending, no error messages appear regarding wireless. Also, the wireless networks became much more stable.

The issue was the lack of the wireless module ipw2200. Well, not exactly the lack of the module: it was installed, but it was deactivated. So the wireless was probably working with a generic module. I didn't knew about loading modules, so I have not imaginated the right resource was already installed, but not activated.

So, to solve the issue, I have used the following command as superuser:

```
modprobe ipw2200
```

Which activated the right module. The only thing I wanted and not succeeded was to control the wireless LED, the experimental LED code have not worked on the Asus M2400N. :( Obs.: I was able to control the mail's LED (which is a beautiful blue, first time I have seen). 

I have found the needed informations here: [https://wiki.debian.org/ipw2200](https://wiki.debian.org/ipw2200)

---

