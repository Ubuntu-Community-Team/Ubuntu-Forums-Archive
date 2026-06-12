---
title: "Setting Default Wireless Network"
date: 2014-11-25
forum: Networking &amp; Wireless
---

### Post by rbscairns on 2014-11-25
I have two available wireless networks, both of about equal strength and always using the same wireless channel. My PC OS is Ubuntu 14.04 system and it is currently set up to automatically connect into either wireless network. When I log in with my personal account, my PC connects randomly to either network "A" or "B" (however I believe that my system is really connecting to the strongest wireless signal at the time).

My network "A" in Ubuntu is set up to:

[INDENT]YES, "Automatically connect to this network when it is available" and
NO, "All users may connect to this network"
(this network "A" is for my personal account).[/INDENT]

 My network "B"  in Ubuntu is set up to:

[INDENT]YES, "Automatically connect to this network when it is available" and
YES, "All users may connect to this network"
(this network "B" is for my personal account and the Guest account).[/INDENT]

What I want to do is have my personal account automatically connect to network "A" when I log in, but still allow my to manually connect to network "B" when I want to. I also want the Guest account to only be able to connect to network "B" and not be able to connect to network "A".

How can I achieve what I want?

---

### Post by matt-concretecomputing on 2014-12-01
This will achieve the first (i.e., connecting correctly under your account):

1. under your own account from a terminal, run

nm-connection-editor

2. Under your own account, uncheck the "connect automatically" option for network B. You'll still be able to connect manually when you need to. I.e., you're not setting network A as the default per se, but you're setting network B as a manual-only option.

I'm not clear on how the "all users may connect" option works, so I'm not sure about how to achieve your second desire. It doesn't make sense to me that as an unprivileged user I have an option to say that not all other users may connect to a network. But maybe somebody else can help there.

---

### Post by rbscairns on 2014-12-09
Thank you matt-concretecomputing. the first part of my problem is solved.

Now, can anyone help with the second part " I also want the Guest account to only be able to connect to network "B" and not be able to connect to network "A"."

---

