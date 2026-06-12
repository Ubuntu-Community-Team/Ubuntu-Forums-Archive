---
title: "Configuring wifi on Ubuntu Server 20.04 without other connections"
date: 2020-05-18
forum: Networking &amp; Wireless
---

### Post by porkpiehat2 on 2020-05-18
I'm trying to set up a wireless network connection with Ubuntu Server 20.04, after a failed attempt with ethernet (issue with the ethernet adapter). The wifi adapter works, I tested it before installing Ubuntu.
All tutorials on this say it is a matter of configuring the netplan .yaml-file, apply, reboot and presto. They easily forget to mention that it seems to require *wpa_supplicant -* and that's where my catch-22 starts.

The syslog error shows it requires *wpa_supplicant*. Without active connection to use apt-get, I downloaded *wireless-tools* and *wpasupplicant* as tarball. However, these cannot install because *make* is not installed. I tried installing *build-essential* or *make* package, but that requires... internet!

Am I missing something, or is Ubuntu Server not equipped for wifi out-of-the-box, thus always requiring an active ethernet connection? Any way I can get it to work still?

syslog section:
```

May 18 11:37:13 prometheus systemd[1]: Started WPA supplicant for netplan wlp2s0.
May 18 11:37:13 prometheus systemd[1]: Stopping Network Service...
May 18 11:37:13 prometheus systemd[1137]: netplan-wpa-wlp2s0.service: Failed to execute command: No such file or directory
May 18 11:37:13 prometheus systemd[1137]: netplan-wpa-wlp2s0.service: Failed at step EXEC spawning /sbin/wpa_supplicant: No such file or directory
May 18 11:37:13 prometheus systemd[1]: netplan-wpa-wlp2s0.service: Main process exited, code=exited, status=203/EXEC
May 18 11:37:13 prometheus systemd[1]: netplan-wpa-wlp2s0.service: Failed with result 'exit-code'.
May 18 11:37:13 prometheus systemd[1]: systemd-networkd.service: Succeeded.
May 18 11:37:13 prometheus systemd[1]: Stopped Network Service.
May 18 11:37:13 prometheus systemd[1]: Starting Network Service...
May 18 11:37:14 prometheus systemd-networkd[1148]: Enumeration completed
May 18 11:37:14 prometheus systemd[1]: Started Network Service.

```


'ip a' shows the interface is up, but no connection is made (DOWN):
```

3: wlp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether e4:f8:9c:02:9b:c1 brd ff:ff:ff:ff:ff:ff

```

01-config.yaml (modified from the netplan examples)
```
network:
  version: 2
  renderer: networkd
  wifis:
    wlp2s0:
      dhcp4: yes
      optional: yes
      access-points:
        "SSID":
          password: "mypassword"

```

---

### Post by chili555 on 2020-05-18
Rather than compiling the tarballs, similar to getting a cube of stainless steel and carving away everything that isn't a Rolex watch, I strongly suggest that you instead get the Ubuntu packages here:

[https://packages.ubuntu.com/eoan/wpasupplicant](https://packages.ubuntu.com/eoan/wpasupplicant)

[https://packages.ubuntu.com/eoan/wireless-tools](https://packages.ubuntu.com/eoan/wireless-tools)

Download the deb files on a USB key or similar and transfer them to the desktop of your Ubuntu computer. Install them with:

```
cd Desktop
sudo dpkg -i *.deb
```

If it complains that there are missing dependencies, get them at the same location and try again.

---

### Post by porkpiehat2 on 2020-05-18
Thanks for the reply. After some digging I just solved it with a similar approach. I found that .deb-files are much easier indeed.
I didn't see the .deb-files directly on the website though. Instead I did obtained the URLs of the packages and dependencies via apt and downloaded them on a thumbdrive.

Most importantly, it worked! Still surprises me that Ubuntu Server does not come with wifi capability built-in.

---

### Post by chili555 on 2020-05-18
> Still surprises me that Ubuntu Server does not come with wifi capability built-in.I suspect it's because most servers are set up with ethernet. Even home servers can usually be located almost anywhere, within an ethernet cables distance from the router. 

Unlike the desktop edition, server edition doesn't try to be all things to all people all of the time. I know, crazy!

Glad it's working.

---

### Post by peterchibunna on 2020-07-27
This thing really dealt me a blow. I was frustrated for more than 12 hours trying to figure out why the `netplan apply` wasn't working. It all boils down to the wpa_supplicant that's not available on a freshly installed server. A lot of things are not available.

Anyway I screwed up my system while I tried to manually install the dependencies of the packages wpa_supplicant and wireless-tools.

I've given up and installing desktop version. Canonical keeps creating difficulties in the name of simplifying things.

---

