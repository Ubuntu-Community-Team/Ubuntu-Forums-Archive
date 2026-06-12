---
title: "Compatibility with Windows Remote Desktop? What about 32-bit vs. 64-bit?"
date: 2024-11-16
forum: Networking &amp; Wireless
---

### Post by vector3 on 2024-11-16
I have a need for a portable platform (that is, think Chromebook, netbook, tablet. etc.,) that will permit me to 'listen' to a host Windows PC. Is there any OS that can permit me to accomplish this? If yes, can this also be extended to a 64-bit host communicating with a 32-bit listener?

For example, I have a pair of 32-bit netbooks that I might be able to use for this purpose despite the fact that support for this architecture is nearly gone. The reason that makes this idea legitimate is that I am referring to communication among instrumentation systems and these are most often prohibited from accessing the Internet to ensure functionality remains intact.

Regardless of the nature of this inquiry and any response it might bring are you able to refer to a known means for me to accomplish this task. By this I mean that if you know of any highly portable hardware that will permit me to communicate with 'Remote Desktop' for this purpose please let me know.

---

### Post by vector3 on 2024-11-16
This discussion topic indicates rather strongly that Chromebooks are not likely to be a preferred choice but I'll look into MrChromebox's List anyway. Identifying useful candidates may be a research project I do not need...

[https://ubuntuforums.org/showthread.php?t=2480320&highlight=linux+chromebooks](https://ubuntuforums.org/showthread.php?t=2480320&highlight=linux+chromebooks)

---

### Post by TheFu on 2024-11-16
pi-kvm?  It shouldn't care what the OS is.[https://docs.pikvm.org/v4/](https://docs.pikvm.org/v4/) $150-ish

There are other, similar, options.  Saw a cheap KVM for $60 a few days ago that a few people are loving, but it takes a month to get on a slow boat from China.
[https://wiki.sipeed.com/hardware/en/kvm/NanoKVM/introduction.html](https://wiki.sipeed.com/hardware/en/kvm/NanoKVM/introduction.html)  [https://www.aliexpress.us/item/3256807610991631.html](https://www.aliexpress.us/item/3256807610991631.html)  $52 today, is seems.

And a more "finished", professional, easy to use option: [https://tinypilotkvm.com/product/tinypilot-voyager2a/](https://tinypilotkvm.com/product/tinypilot-voyager2a/) $400

These don't use remote desktop protocols. They connect directly as fake keyboards, mice, and video, then transmit that **view** over their ethernet connection to a logged in client system.

---

### Post by vector3 on 2024-11-16
This is quite useful and may help me solve other communication problems but my current need, which I now realize I did not explain clearly, is for a wireless communication because the 'listener' will be carried around while tasks are performed. Hence, my mention of tablet, netbook, compact all-in-one or other lightweight hardware with a monitor.

---

### Post by TheFu on 2024-11-16
> **vector3 said:**
> This is quite useful and may help me solve other communication problems but my current need, which I now realize I did not explain clearly, is for a wireless communication because the 'listener' will be carried around while tasks are performed. Hence, my mention of tablet, netbook, compact all-in-one or other lightweight hardware with a monitor.
 

 The proposed KVMs provide remote access into the system they connect to.  The clients can be anything with a reasonable web browser.

---

### Post by vector3 on 2024-11-16
Thank you for the clarification.

---

