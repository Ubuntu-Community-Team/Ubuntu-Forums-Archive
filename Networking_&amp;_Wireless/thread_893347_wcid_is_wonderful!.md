---
title: "wcid is wonderful!"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by hise0001 on 2008-08-18
I have a laptop with an ipro wireless adaptor and a desktop with an edimax adaptor using the rt2500 driver.

I have a WPA secured router and have had problems connecting.  I had never successfully connected to the router from my edimax-based desktop.  I had managed to connect with the ipro-based laptop, only after turning off network manager and managing the interfaces file manually, and even then I had to restart networking before connecting to the internet.  I also had a weird problem when browsing to Places->Network->Windows Network->Workgroup I could not see the other computers in my workgroup.

wcid fixed all of this for both machines... oh happy day!:guitar:

It was effortless too!

I....
* went to wcid.sourceforge.net and followed instructions to add their repository to synaptic.
* complete removal of network manager from synaptic
* installed wcid from synaptic
* launched Applications->Internet->Wcid and supplied my router information.

Just passing this on in case it could help someone else.

---

