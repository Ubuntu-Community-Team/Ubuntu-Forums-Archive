---
title: "Wireless not working"
date: 2021-05-12
forum: Networking &amp; Wireless
---

### Post by piyush0074 on 2021-05-12
How do i claimed my wireless controller..
When i run a command "sudo lshw - class network"
They shows me my both wireless and ethernet controller is unclaimed, and i have to download lightdm because i am in cli.
Thanks in advance.&#128522;

---

### Post by The Cog on 2021-05-12
Welcome to the forum.

The controllers are "claimed" by the appropriate network driver. If this has not happened then I presume the required network driver has not been installed/loaded. Please post the output from "sudo lshw - class network" here (use code tags (the # symbol in the advanced editor) to preserver formatting. People may then be able to advise what driver you need.

---

