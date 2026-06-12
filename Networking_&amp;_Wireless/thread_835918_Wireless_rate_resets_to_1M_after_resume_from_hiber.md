---
title: "Wireless rate resets to 1M after resume from hibernate"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by Hooya on 2008-06-20
So I have the typical issue that my wireless rate is set at 1M on boot.  I have fixed this by putting "post-up iwconfg wlan0 rate 54M" in /etc/network/interfaces.  The problem I have now is that I like to use hibernate with this laptop and after coming out of hibernate it resets to 1M.  I can fix it with the iwconfig command, but it's annoying and seemingly unnecessary.  

Is there a way to set the rate to 54M automatically after coming out of Hibernate?

---

### Post by Arcadian on 2008-07-02
Aren't there scripts under /etc/acpi/resume.d that get run when the session is resumed? Try adding a line to 62-ifup.sh & see if that helps. Just a stab in the dark!

P.s. Thanks for sharing the post-up iwconfig trick, it helped with my 1Mb/s wifi startup speed! :)

---

