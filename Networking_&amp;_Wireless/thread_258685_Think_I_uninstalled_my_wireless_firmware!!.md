---
title: "Think I uninstalled my wireless firmware!!"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by QwUo173Hy on 2006-09-16
I suddenly have no wireless connectivity on my laptop. I did only two things on my last login

1) Edited menu.lst to tell grub to pick the kernel I have always used (instead of having to press ESC all the time). uname -r confirms that this worked.

2) I uninstalled the only NVIDIA related package in my system. It was a kernel module. I dont have an nvidia card and I was having issues so I removed this package.

Now I dont have internet.

I am running the kubuntu dapper live cd for the mean time (although I have to go through a lengthy routine to get the acx firmware working each time).

If I did uninstall something I shouldn't have, how can I get this back on my system even though there is no connection? I can't get a wired connection.

Perhaps buying a more recognised wireless nic would be the best way to go?

---

### Post by meng on 2006-09-16
I don't see how this would have uninstalled the firmware. Buying another card is an option, but if you have a bit of time to try and get the current one working again, then why not give it a try?

---

### Post by QwUo173Hy on 2006-09-16
There are two lights on the card. One to indicate the device is being powered (red) and one to show transmission (green).

At the moment, neither lights are lit. This is unusual because even before I installed the firmware, I at least had the power light.

Any ideas what could be the cause?

Thanks,
jarlath

---

### Post by QwUo173Hy on 2006-09-16
I'm astonished, I actually managed to fix this myself. I had a look through /var/log/messages and found a comment that 'acx/1.2.1.34/tiacx111c16 was not provided. Check your hotplug scripts'

So I went looking and found that the mentioned directory was no longer present. I have no idea how it got deleted, but I do know that the file that was in that directory was just a symlink to another file. So I recreated the folder and the link.

Very happy with myself :)

Thanks meng,

Jarlath

---

### Post by meng on 2006-09-16
Don't thank me, since I didn't do anything except advise you to wait a little longer before parting with your hard-earned cash.

---

