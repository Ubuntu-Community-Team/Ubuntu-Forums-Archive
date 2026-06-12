---
title: "Guarddog and DHCP"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by rickbeton on 2008-08-13
Hi,

I'm new to Guarddog so forgive me if this is a dumb question.

I could not get my eth0 to connect after enabling the firewall using Guarddog. I enabled most of the 'Network' protocols on the Guarddog Internet services panel. I enabled the DHCP tickbox on the 'Advanced' tab. But still the network failed to acquire any DHCP information.

Then I looked in the system logs and noticed that a lot of port 67 packets were being dropped (Bootp & Dhcp). So I added a user-defined port for UDP 67:68 and allowed that also. Fortunately this worked and means I can now connect eth0 happily and safely, as a travel around with my laptop.

What puzzles me is why I had to do this and why it was so difficult. Can anyone explain?

Rick

---

