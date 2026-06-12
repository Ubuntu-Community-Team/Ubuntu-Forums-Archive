---
title: "NetworkManager fails to start"
date: 2021-02-16
forum: Networking &amp; Wireless
---

### Post by kmkwood on 2021-02-16
Ubuntu 20. Up until 06:18 EST on Feb 13, 2021, NetworkManager was running fine, getting an IP from DHCP on my router.  Here is output from journalctl for hostname coot

```

Feb 13 06:18:57 coot systemd[1]: NetworkManager.service: Main process exited, code=dumped, status=11/SEGV
Feb 13 06:18:57 coot systemd[1]: NetworkManager.service: Failed with result 'core-dump'.
Feb 13 06:18:57 coot systemd[1]: NetworkManager.service: Scheduled restart job, restart counter is at 1.
Feb 13 06:18:57 coot systemd[1]: Stopped Network Manager.
Feb 13 06:18:57 coot systemd[1]: Starting Network Manager...
Feb 13 06:18:58 coot NetworkManager[229188]: Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 541: elf_machine_rela_relative: Assertion
 `ELFW(R_TYPE) (reloc->r_info) == R_X86_64_RELATIVE' failed!
Feb 13 06:18:58 coot systemd[1]: NetworkManager.service: Main process exited, code=exited, status=127/n/a
Feb 13 06:18:58 coot systemd[1]: NetworkManager.service: Failed with result 'exit-code'.
Feb 13 06:18:58 coot systemd[1]: Failed to start Network Manager.
Feb 13 06:18:58 coot systemd[1]: NetworkManager.service: Scheduled restart job, restart counter is at 2.
Feb 13 06:18:58 coot systemd[1]: Stopped Network Manager.

```

 Every attempt to start NetworkManager since then has failed.  The next day, I noticed that the connection light on the ethernet switch was not lit for the cable to my machine.  I tried a usb-to-ethernet adapter and the switch port lit up just fine.  Without a NetworkManager, I still didn't have connectivity.

I bought a PCI ethernet card with an Intel chip.  Installed it, plugged in the cable and the port lit up as it should.  When I rebooted (approx. noon local time on Feb 15) I had no connectivity.  After some hours I saw an article describing how to run dhclient manually.  dhclient got the network going again, routes and all. My new card is working, and I'm online again.  I have rebooted several times since then, and I have repeatedly tried restarting NetworkManager with systemctl. BUT NetworkManager still won't start.  The same error message appears in journalctl output.  I have to run dhclient manually every reboot.

Do I need NetworkManager running?  My new ethernet card is visible in 'lshw' output, but dhclient doesn't start until I run it manually.

What do I do next?

---

### Post by chili555 on 2021-02-17
> Do I need NetworkManager running? Not really. There are other ways to configure networking. However, I'd recommend that we fix the underlying issue rather than devising an ugly work-around.

With the ethernet connected, please run:

```
sudo apt update
sudo apt  install --reinstall network-manager 
sudo service NetworkManager restart
```Any errors, warnings or mysterious clues??

---

### Post by kmkwood on 2021-02-18
The reinstall did the trick.  The NetworkManager is running again.  'apt update' showed 33 packages could be upgraded, so I ran 'sudo apt upgrade' to install them before I reinstalled NetworkManager.

Just to make sure the problem was fixed, I rebooted.  The network came up just fine, and NetworkManager is running.

Thank you very much, chili555.

---

