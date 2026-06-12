---
title: "WiFi Hotspot not working in 22.04"
date: 2023-02-01
forum: Networking &amp; Wireless
---

### Post by meetdilip on 2023-02-01
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291701&stc=1[/IMG]

The WiFi hotspot option is greyed out for me in 22.04, HP laptop. Works fine on the 23.04 daily build. Any way to make it work? Thanks.

---

### Post by molgra on 2023-02-02
Hi
I have a similar problem in that Hotspot is no longer working on wifi connection.
It appears be from an update on the ubuntu base and not a security update. Which update this is  I do not know

---

### Post by molgra on 2023-02-02
Solution :P
Had uninstall wpa and re-install 
See below

sudo apt remove wpasupplicant 
sudo apt install wpasupplicant

---

### Post by molgra on 2023-02-04
I had to find another solution because of updates of wpasupplicant 2:2.10-6ubuntu2 allows internet but not printer access(?)

sudo apt remove wpasupplicant

download wpasupplicant_2.10-6_amd64.deb 

sudo apt install /path-to-Downloads/wpasupplicant_2.10-6_amd64.deb
sudo apt-mark hold wpasupplicant

---

