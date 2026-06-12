---
title: "Wireless disconnects while using Software Center."
date: 2011-01-12
forum: New to Ubuntu
---

### Post by Leprkan on 2011-01-12
[FONT=Arial]Hey Folks

Got a fresh installation here, but when I try to download stuff my wireless disconnects.  Any help?

Using a Rosewill RNX-N1MAC card and a Linksys WRT160N router.

Note: I would've posted this in the Networking/Wireless section, but I guess I don't have permission.[/FONT]

---

### Post by hansolo4949 on 2011-01-12
Perhaps you have some compatability issues with Ubuntu and your wireless. Does the wireless work fine in windows/os-x? If it doesn't you might have a failing wireless card.

hansolo4949

---

### Post by lbarnes on 2011-01-12
Some users have better luck with wicd than with network manager.
sudo apt-get install wicd

---

### Post by Leprkan on 2011-01-12
@hansolo4949 Works okay on other operating systems.  Worked on Arch Linux.

@lbarnes I'll try that as soon as I get home :)

Thanks both.

---

### Post by Leprkan on 2011-01-12
Well.  I tried wicd, and got the same results.  I observed that I could download about 5kB before being disconnected.  

Any other guesses?

---

