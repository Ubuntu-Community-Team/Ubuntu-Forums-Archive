---
title: "Error SIOCGIFFLAGS: No such device"
date: 2005-11-29
forum: Networking &amp; Wireless
---

### Post by aesux on 2005-11-29
Hi,

Any idea about that error message. My lan works fine, over eth0, it is configured with DHCP. All works fine, but, when I start network monitor applet I see it with and error icon, and it give me the title error message (Error SIOCGIFFLAGS: No such device), it seems network monitor applet coun not monitor the eth0 interface. If I go to configure button, ofcourse I can configure everything over that interface, and all continues working well, but the messages is there.

Using 2.6.12-9-amd64-generic kernell.

Thanks in advance,

Aesux,

---

### Post by MakubeX on 2005-11-29
I'm not really sure but this might be caused by some setting in the BIOS.

---

### Post by aesux on 2005-11-29
I don't know, but this same machine, has had another working Ubuntu installation without that problem.

Of course the Ethernet card is motherboard integrated, so, sould be possible that the BIOS cause that, but any idea about with BIOS parameter?

Thanks again,

Aesux,

---

### Post by aesux on 2005-11-30
[QUOTE=aesux]Hi,

Any idea about that error message. My lan works fine, over eth0, it is configured with DHCP. All works fine, but, when I start network monitor applet I see it with and error icon, and it give me the title error message (Error SIOCGIFFLAGS: No such device), it seems network monitor applet coun not monitor the eth0 interface. If I go to configure button, ofcourse I can configure everything over that interface, and all continues working well, but the messages is there.

Using 2.6.12-9-amd64-generic kernell.

Thanks in advance,

Aesux,[/QUOTE]


Solved.

I don't know why, but network monitor don't recognize eth0, but when i explicitily write it so it could monitor, it take it, and all go fine.

It seems it need anyother identify for him which networtk interface to monitor. It only knows about lo.

Thanks,

Aesux

---

### Post by otake-tux on 2006-03-02
how  did you exactly fix it?

---

### Post by John.Michael.Kane on 2006-03-05
Wrong section sorry

---

### Post by vkm on 2006-10-02
Hi, (first sorry for my poor English)
I had the same problem with the network monitor applet because i tried to rename the eth0 conexion to another more readable so the applet stop working, i couldn`t open the monitor normaly and the error "SIOCGIFFLAGS: No such device" appears, so i solve it right button --> propeties  and renaming again the conexion so it work fine again.

I hope this help you,
Good Luck

Victor

---

