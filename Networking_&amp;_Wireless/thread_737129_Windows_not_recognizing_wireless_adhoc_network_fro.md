---
title: "Windows not recognizing wireless adhoc network from Ubuntu"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by goldark on 2008-03-27
Currently, I have a laptop with Ubuntu 7.1 on it broadcasting a wireless ad-hoc network I created using a USB Wifi adapter. I'm able to see it and connect to using another Ubuntu laptop. However, when I switch over to Windows, I can't even see the ad hoc network or ping it.

Does anyone know any issues surrounding Linux/Windows ad-hoc connections and what must be done to make this work?

Thanks to any replies!

---

### Post by goldark on 2008-03-27
I fixed it.

When doing **iwconfig DeviceName channel auto**, it didn't work.

It worked when I changed auto to something else, like 11.

---

### Post by goldark on 2008-03-27
However, I still can't ping it.


Hmmmm.

---

### Post by goldark on 2008-03-27
Solution: get rid of network keys altogether :)

---

