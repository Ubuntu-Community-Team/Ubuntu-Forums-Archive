---
title: "ubuntu forgets network settings after reboot"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by nish_lal on 2006-12-20
i installed unbutu 6.06 yesterday ..
i m facing a problem now.. ubuntu dosent seem to remember my network settings..
so i have to set up network settings every time i reboot...
i use dhcp so i just need to enter the dns to make internet work.. but cant i make ubuntu remember it?

---

### Post by acturneruk on 2006-12-20
You need to edit the file /etc/network/interfaces and add you network config there. Ask if you need specific help with a particular interface.

HTH

---

### Post by nish_lal on 2006-12-20
thax for replying..
i m totally new to linux so i dont understand much by what u say... how do i go about editing /etc/network/interfaces???

---

### Post by acturneruk on 2006-12-20
Open a terminal (Applications --> Accessories --> Terminal), and type:-

```
sudo nano -w /etc/network/interfaces
```

and enter your password. See [https://help.ubuntu.com/community/NetworkConfigurationCommandLine]("https://help.ubuntu.com/community/NetworkConfigurationCommandLine") for more details.

HTH

---

### Post by handy on 2006-12-20
> **nish_lal said:**
> i installed unbutu 6.06 yesterday ..
i m facing a problem now.. ubuntu dosent seem to remember my network settings..
so i have to set up network settings every time i reboot...
i use dhcp so i just need to enter the dns to make internet work.. but cant i make ubuntu remember it?

If the settings you are talking about are your isp's DNS settings then have a look at [**_this how-to_**]("http://ubuntuforums.org/showthread.php?t=282034"), following it may very well be all you need to do.

---

