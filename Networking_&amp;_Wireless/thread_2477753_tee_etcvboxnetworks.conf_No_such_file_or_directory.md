---
title: "tee: /etc/vbox/networks.conf: No such file or directory"
date: 2022-08-05
forum: Networking &amp; Wireless
---

### Post by chat-4432 on 2022-08-05
i want to setup minimal EPC
i can't use magmacore [https://docs.magmacore.org/docs/basics/quick_start_guide](https://docs.magmacore.org/docs/basics/quick_start_guide)
i have meet prereq but i skip install deployment tooling
when i try 
[COLOR=#397300][FONT=SFMono-Regular]echo[/FONT][/COLOR][COLOR=#880000][FONT=SFMono-Regular]"* 192.168.0.0/16"[/FONT][/COLOR][COLOR=#444444][FONT=SFMono-Regular] | sudo tee -a /etc/vbox/networks.conf
it show 
[/FONT][/COLOR]```
tee: /etc/vbox/networks.conf: No such file or directory
* 192.168.0.0/16

```what should i do ??
[COLOR=#444444][FONT=SFMono-Regular]
[/FONT][/COLOR]

---

### Post by TheFu on 2022-08-06
That is a very common error.
It means that the file doesn't exist and cannot be appended
OR
that the parent directory doesn't exist.

If virtualbox hasn't been installed (vbox), I suspect that is the problem.  I have no idea what the other things are. Too specific.  EPC? Huh?  Are you Presbyterian or creating power grid systems?

This is a virtualization question based on the vbox error alone. Not general networking.

Best to assume we don't know anything about your environment or computer(s).  It is often best to start from a very high level for what the final goal to be achieved is. There are usually 20 better solutions, but not always.

---

### Post by chat-4432 on 2022-08-06
oh i forgot install vbox
i want to setup private 5g but i lack of knowledge, idk how to use they tool [https://ubuntu.com/blog/introduction-to-open-source-private-lte-and-5g-networks](https://ubuntu.com/blog/introduction-to-open-source-private-lte-and-5g-networks)

---

