---
title: "SSSD buggy ?"
date: 2021-04-15
forum: Networking &amp; Wireless
---

### Post by w-kovacs on 2021-04-15
Hello,

I made a clean new installation of ubuntu 20.04 and joined them to our domain. Then I logged in with my domain credentials. Logged out. Disconnect the LAN cable and tried to log in again. Which was denied.
Some digging in the logs showed me that sssd not enter the offline mode an therefore will not use the offline credentials.

I tried these multiple times and it happened every single time.

At this point I can either wait a seriously long time until sssd finally decide to go into offline mode or I place the IP of our domain controller in /etc/hosts. I would consider none of these options a valid solution. Hardcoding the IP will bite us in our behinds down the line because wel have upcoming changes in our server infrastructure ahead.

Right now my guess is, because the IP of our DC is not cached yet the resolve "error" is handled wrong and cause of delaying the switch to offline mode. As soon as the IP is locally known (resolvable - either through /etc/hosts or dns cache) offline credentials are usable.

At this point I am not sure if I missed a setting or if it is a actual bug.

Is there a solution to this I am not seeing right now?

Regards

w-kovacs

PS: I installed an Ubuntu 18.04 and there sssd works as intended in this situation

---

### Post by w-kovacs on 2021-05-11
Problem still present. I made some changes in my settings but then it was always offline except while directly connected. Because we need VPN I had to role it back

---

