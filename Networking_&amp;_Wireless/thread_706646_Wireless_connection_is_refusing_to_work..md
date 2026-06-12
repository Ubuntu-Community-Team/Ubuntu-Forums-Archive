---
title: "Wireless connection is refusing to work."
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by ccase2k on 2008-02-24
Hey guys, I just installed Hardy Heron and it is really good but I can no longer connect to the internet. After failures in the past with the Wireless I decided to use the wired, and that worked fine until I upgraded last night. When I started up 8.04 for the first time I was prompted with an install network device thing. I did install it, and now when I go to System-> Administration->Networking, it shows Wired with a check mark and Wireless with a subtraction sign saying "enabled roaming" anytime I try to change it, it says something like " you are not allowed to modify the system settings" but I am the only user on the computer. Please help if you can, anything is appreciated :):KS

---

### Post by Sam Lars on 2008-02-24
Roaming is for Network Manager to automatically manage your wireless.
Try running
```
sudo gnome-network-preferences
```
even though it should run as sudo anyway... that's the root administrator that technically isn't a user but you have to provide the password for any admin tasks (like network settings).

---

