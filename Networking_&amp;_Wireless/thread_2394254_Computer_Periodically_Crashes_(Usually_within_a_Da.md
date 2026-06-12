---
title: "Computer Periodically Crashes (Usually within a Day)"
date: 2018-06-14
forum: Networking &amp; Wireless
---

### Post by satluri on 2018-06-14
Did a fresh install of Ubuntu 18.04 LTS, but my computer now periodically crashes. Seems to have to do with my WiFi? It's integrated with my motherboard ([https://www.asrock.com/mb/Intel/Z370%20Taichi/](https://www.asrock.com/mb/Intel/Z370%20Taichi/))

 Never had this issue on 16.04 LTS. Below is what I see in /var/log/kern.log

```
Jun 10 20:45:57 Fractal kernel: [ 6993.277247] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
Jun 10 20:45:57 Fractal kernel: [ 6993.277254] iwlwifi 0000:05:00.0: Error sending CMD_DTS_MEASUREMENT_TRIGGER_WIDE: enqueue_hcmd failed: -5
Jun 10 20:45:57 Fractal kernel: [ 6993.277255] iwlwifi 0000:05:00.0: Failed to get the temperature (err=-5)
Jun 10 20:45:59 Fractal kernel: [ 6995.306718] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
Jun 10 20:45:59 Fractal kernel: [ 6995.306727] iwlwifi 0000:05:00.0: Error sending CMD_DTS_MEASUREMENT_TRIGGER_WIDE: enqueue_hcmd failed: -5
Jun 10 20:45:59 Fractal kernel: [ 6995.306728] iwlwifi 0000:05:00.0: Failed to get the temperature (err=-5)
Jun 10 20:46:01 Fractal kernel: [ 6997.335792] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
Jun 10 20:46:01 Fractal kernel: [ 6997.335799] iwlwifi 0000:05:00.0: Error sending CMD_DTS_MEASUREMENT_TRIGGER_WIDE: enqueue_hcmd failed: -5
Jun 10 20:46:01 Fractal kernel: [ 6997.335800] iwlwifi 0000:05:00.0: Failed to get the temperature (err=-5)
Jun 10 20:46:03 Fractal kernel: [ 6999.365298] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
Jun 10 20:46:03 Fractal kernel: [ 6999.365307] iwlwifi 0000:05:00.0: Error sending CMD_DTS_MEASUREMENT_TRIGGER_WIDE: enqueue_hcmd failed: -5
Jun 10 20:46:03 Fractal kernel: [ 6999.365308] iwlwifi 0000:05:00.0: Failed to get the temperature (err=-5)
Jun 10 20:46:05 Fractal kernel: [ 7001.394717] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
Jun 10 20:46:05 Fractal kernel: [ 7001.394725] iwlwifi 0000:05:00.0: Error sending CMD_DTS_MEASUREMENT_TRIGGER_WIDE: enqueue_hcmd failed: -5
Jun 10 20:46:05 Fractal kernel: [ 7001.394726] iwlwifi 0000:05:00.0: Failed to get the temperature (err=-5)
Jun 10 20:46:07 Fractal kernel: [ 7003.423809] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
Jun 10 20:46:07 Fractal kernel: [ 7003.423817] iwlwifi 0000:05:00.0: Error sending CMD_DTS_MEASUREMENT_TRIGGER_WIDE: enqueue_hcmd failed: -5
Jun 10 20:46:07 Fractal kernel: [ 7003.423819] iwlwifi 0000:05:00.0: Failed to get the temperature (err=-5)
Jun 10 20:46:09 Fractal kernel: [ 7005.453260] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
Jun 10 20:46:09 Fractal kernel: [ 7005.453267] iwlwifi 0000:05:00.0: Error sending CMD_DTS_MEASUREMENT_TRIGGER_WIDE: enqueue_hcmd failed: -5
Jun 10 20:46:09 Fractal kernel: [ 7005.453268] iwlwifi 0000:05:00.0: Failed to get the temperature (err=-5)
Jun 10 20:46:11 Fractal kernel: [ 7007.482595] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
Jun 10 20:46:11 Fractal kernel: [ 7007.482603] iwlwifi 0000:05:00.0: Error sending CMD_DTS_MEASUREMENT_TRIGGER_WIDE: enqueue_hcmd failed: -5
Jun 10 20:46:11 Fractal kernel: [ 7007.482606] iwlwifi 0000:05:00.0: Failed to get the temperature (err=-5)

...

(repeats forever until I hit the reset button on my computer)

Any help on how to resolve this would be much appreciated!
```

---

### Post by oldfred on 2018-06-17
Moved to Networking & Wireless sub-forum
See sticky on notes before posting. It wants you to run a script to have details on versions and configuration, so those that know wireless issues can make suggestions.

[SOLVED] Before posting in Networking & Wireless
	           	 		 			[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by satluri on 2018-06-18
Here is the pastebinit URL: [http://paste.ubuntu.com/p/zGFj8DnxQh/](http://paste.ubuntu.com/p/zGFj8DnxQh/)

---

### Post by satluri on 2018-06-18
I've disabled power management in /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

Will report back if that helps

---

### Post by oldfred on 2018-06-18
Are you using any Asmedia ports for drives?
That almost always causes issues.

       Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564)

---

### Post by satluri on 2018-06-18
No, I am not using any Asmedia ports for drives. The only drive I have is an NVME m2 SSD.

---

### Post by satluri on 2018-06-20
Things have been stable for a couple days since disabling WiFi power management. Will keep this thread open for a few more days to confirm

---

