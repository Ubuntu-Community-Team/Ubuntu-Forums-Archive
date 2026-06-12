---
title: "disable network for stadard usesrs"
date: 2014-09-13
forum: Networking &amp; Wireless
---

### Post by sn0m on 2014-09-13
Hi
I created a standard account for my son. I do ot want him to be able to browse internet if I'm not present.
How can I disable the wireless option for his account?
I have unchecked available to all users in the network manager but it dosent seem to do the job as the wireless is available for him when he logs onto his account?
Thaks
sn0m

---

### Post by elico on 2014-09-13
You can use iptables for the task using output rules to match a user or group id.
Another solution will be to force a local proxy such as squid with authentication\authorization.
And you can combine both of these combined together... squid as intercept proxy and iptables to intercept traffic into it.
Also you can create a whitelist of sites which you can allow your son to surf while you are not attended such as school, goverment or any others.

---

