---
title: "wireless problem"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by tocilog on 2008-05-17
ok so my wireless adapter was working on and off so i decided to fix it...the wrong way. i used [this thread]("http://ubuntuforums.org/showthread.php?t=684495") even though i had network manager to try it out, but that actually killed the little connection i had.

so i started out doing this:
```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

it didnt work, then after that i tried changing the essid so i went through the whole thing again, but after entering the last "sudo dhclient..." line this error came up

```
SIOCSIFFLAGS: Input/output error
```

if anyone knows how i can somehow magically undo everything i did that would be swell.

sidenote: 

I did find [this thread]("http://ubuntuforums.org/showthread.php?p=4732883"). i figure it will work since my wireless card uses rt73 driver. so i plan on doing that OR upgrading to Hardy. probably both since i would need to download it.

---

