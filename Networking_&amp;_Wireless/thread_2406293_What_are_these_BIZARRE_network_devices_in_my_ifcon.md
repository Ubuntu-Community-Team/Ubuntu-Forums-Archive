---
title: "What are these BIZARRE network devices in my ifconfig?"
date: 2018-11-18
forum: Networking &amp; Wireless
---

### Post by jklarson on 2018-11-18
I have a linode running Ubuntu LTS  18.04.1. It was updated from 14.04 LTS recently. Upgrade went fine a  couple of months ago, and everything works. 
 
I just checked ifconfig -a, and found literally DOZENS of network  devices in there, 57 in total. 17 type AX25 and 20 are ROSE, which I  looked up, both seem to be some sort of software controlled radio. Then a  bunch are link type "generic", some ipip, void, etc. All of these  devices are DOWN, but my question is why do they exist? I certainly  didn't install software defined radio. Was I hacked?

I have another Ubuntu linode on 18.04.1 with none of these weird devices, so it doesn't appear to be a normal linode thing.

Thanks for any assistance!

 Output of ip a:
[https://dpaste.de/oSNf](https://dpaste.de/oSNf)

Output of ifconfig -a:
[https://dpaste.de/BzNh](https://dpaste.de/BzNh)

---

### Post by QIII on 2018-11-18
Are you an amateur radio operator?  Do  you have any HAM radio software installed?

---

### Post by jklarson on 2018-11-19
No, like I said, I did not install any type of software defined radio.

---

### Post by jklarson on 2018-11-21
So has anyone seen anything like this? It's really weird!

---

### Post by SeijiSensei on 2018-11-22
I manage three Linodes. Never saw anything like that.

I use CentOS on these servers though.

---

### Post by jklarson on 2018-11-22
Any ideas what could have created those devices, if they're innocuous? Like, does some user-defined radio package make them?

---

