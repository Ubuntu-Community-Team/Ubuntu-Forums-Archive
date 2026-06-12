---
title: "MAC Adress"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by m0nstter on 2007-01-05
hello, i am a new user of linux and special of ubuntu. i need to know how i can change the MAC adress of my network card. please help me if you can. i wil be mutch in gratitude if you can send me an email at [email]m0nstter@yahoo.com[/email]

Thanks you very mutch

---

### Post by kingmonkey on 2007-01-05
```

ifconfig eth0 down hw ether 00:00:00:00:00:01
ifconfig eth0 up

```

Where 00:00:00:00:00:01 is ur spoofed mac address.

---

### Post by Mr Smith on 2007-01-29
Hello,
      I wanted to change my mac address also, but the ifconfig command did nothing. I then went into the iftab file and modified the eth0 mac address to the one I want. Rebooted. Now the ethernet connection is using a different interface eth1 with the old mac address. eth0 says there's some problem 'check that you entered the name right'. How can I enter the mac address so it sticks? Thank you.

---

