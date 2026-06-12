---
title: "Get iface name with only pci location"
date: 2019-10-23
forum: Networking &amp; Wireless
---

### Post by arcad31a on 2019-10-23
I have an Dell E6400 running Kubuntu 18.10. This machine has an expresscard slot to which I currently have a wireless card connected. I know the "address" so to speak of the card. it is 0000:0e:00.0 The vendor ID is 168c:0024. I'm writing a script that tries to detect the presence of this card connected to the expresscard slot. if the device is connected the script is supposed to launch hostapd. I have not gooten tot eh hostapd portion of this little project so I will consider it out of scope for my question.

my question, therefore, is how do I find the interface name with just the "address", 0000:0e:00.0? I know systool -c net will list all iface names and their respective locations. but I want to list the one iface that's connected to address 0000:0e:00.0.

Does any body have any suggestions?

P.S. Let me know which is the best place for this thread, if posting to this division is inappropriate.

Thanks!

---

### Post by chili555 on 2019-10-23
What does this tell us?

```
dmesg | grep 0e:00 | grep wlp
```

---

### Post by arcad31a on 2019-10-23
the command you supplied show nothing in Konsole. Literally nothing

[IMG] file:///home/diagnostics/Pictures/Screenshot_20191023_163244.png[/IMG]

I don't think that screenshot showed. but let me know either way. I don't really want to startup a cloud share just to be able to post screenshots to forums.

---

### Post by arcad31a on 2019-10-23
Right now the best I've got is a C++ function that reads stdout from "systool -c net" searches through for "0000:0e:00.0", then parses out the iface name based on the position of "0000:0e:00.0" in the stdout dump.

I'm looking for a command line tool that lets me print to stdout just
```
  Class Device = "wls1"
    Device = "0000:0e:00.0"
```

Instead of the full

```
diagnostics@diagnostics-Latitude-E6400:~$ systool -c net
Class = "net"

  Class Device = "enp0s25"
    Device = "0000:00:19.0"

  Class Device = "enx001de11bc5eb"
    Device = "2-5:1.0"

  Class Device = "lo"

  Class Device = "wlp12s0"
    Device = "0000:0c:00.0"

  Class Device = "wls1"
    Device = "0000:0e:00.0"
```

---

