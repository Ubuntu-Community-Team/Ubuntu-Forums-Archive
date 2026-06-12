---
title: "Add VPN Button is Disabled"
date: 2024-07-12
forum: Networking &amp; Wireless
---

### Post by tagadvance on 2024-07-12
When I try and add a Cisco Compatible VPN (vpnc) it lets me enter the VPN information; however, the "Add" button in the top-right is disabled. There is no form feedback indicating that any of the fields are invalid. The button briefly turns green until I switch the `Group password` field to `Store the password only for this user`. The button remains disabled if I switch back to the default `Ask for this password every time`. Clicking the Add button while it's green closes the window but does not store the VPN information. The Network manager says "Not set up" under the VPN header.

I tried searching for an existing issue but the results are all from 2008. Was a regression introduced recently?


Currently running 22.04 6.9.3-76060903-generic with all available updates applied as of the date of this post.

---

### Post by #&amp;thj^% on 2024-07-12
What Version and Desktop of Ubuntu???
Details Matter.

---

### Post by tagadvance on 2024-07-12
Apparently this is a well known bug. Was finally able to get is fixed using this method:
[https://askubuntu.com/a/1404609/112389](https://askubuntu.com/a/1404609/112389)

---

### Post by #&amp;thj^% on 2024-07-12
Same advice I was about to offer, Good Detective work.

---

