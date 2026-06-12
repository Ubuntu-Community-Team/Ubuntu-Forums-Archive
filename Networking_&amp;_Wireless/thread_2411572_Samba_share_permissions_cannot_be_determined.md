---
title: "Samba share: permissions cannot be determined"
date: 2019-01-31
forum: Networking &amp; Wireless
---

### Post by Dondermans on 2019-01-31
Hello,

I have got a laptop. OS is Ubuntu 18.04 LTS and Windows 10 in Dual Boot. There is another computer in the network with the Daphile OS.

I have got a 1Tb USB harddrive. I used Ubuntu to format it to NTFS. When the harddrive is connected directly to my laptop I can see the permissions in the properties (I removed my username from both screenshots below):
[[IMG]https://i.ibb.co/bFKtR21/Screenshot-from-2019-01-31-23-04-16.png[/IMG]]("https://ibb.co/bFKtR21")[[IMG]https://i.ibb.co/t8VPd83/Screenshot-from-2019-01-31-23-04-21.png[/IMG]]("https://ibb.co/t8VPd83") 

If I connect the harddrive to another computer in my network (w/ the Daphile OS), I can see the Samba share and I can access it. However, Ubuntu cannot determine the permissions:
[[IMG]https://i.ibb.co/tPqpphD/Screenshot-from-2019-01-31-23-07-33.png[/IMG]]("https://ibb.co/tPqpphD")   [[IMG]https://i.ibb.co/q7JDhhM/Screenshot-from-2019-01-31-23-07-38.png[/IMG]]("https://ibb.co/q7JDhhM")

I would like to ask two questions please:
1. Why can Ubuntu not determine the permissions of the harddisk when I access it using Samba?
2. How can I configure Samba and/ or the harddisk, so that I can read and write to it?

Up until a week ago, I could access the harddrive, using Samba. It was also possible to read and write to the drive. I tried to enable the local network share, but it does not work. Using Windows, I can see the Samba share and I do have read and write access.

Thank you for your time.

---

### Post by Dondermans on 2019-02-02
It looks like reinstalling Samba and a reboot fixed the issue.

---

