---
title: "swap constantly running at 20%"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by cooper104 on 2011-05-25
Whenever I have a browser open (Firefox 4.01 or latest chromium) and I open the Ubuntu software centre on 10.10 normal release the swap jumps up to 20% immediately, even if there is free memory and computer becomes almost unusable. Even after shutting down software centre, the swap still stays at 20% and only a reboot frees up this and returns back to using just the memory. The hardisk in this laptop is quite slow, so I can understand why the swap is slow, but why does it stay using it?

---

### Post by wojox on 2011-05-25
Try adjusting your [Swapiness]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?")

---

### Post by zealibib slaughter on 2011-05-25
Here is the documentation on swap [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
It should explain why swap is being used with some programs and how to tweak your swap usage.

---

### Post by cooper104 on 2011-05-25
> **zealibib slaughter said:**
> Here is the documentation on swap [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
It should explain why swap is being used with some programs and how to tweak your swap usage.

Thanks zealibib slaughter, I'll give it a read over and see what I can learn!

---

### Post by cooper104 on 2011-05-25
Thanks guys for the link, I've adjusted my swappiness to 10 (temp) and it has definitely helped, I'll play around with different settings to see what the best one is before writing it permanently!

---

