---
title: "64bit memory"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by dimitriv on 2009-03-06
hi 
my machine has 4gb RAM.
32bit Intreprid reported only 2.8gb, it was suggested the 64bit processor was the issue and recommended i upgrade to 64bit Ubuntu
64bit Intrepid is now installed and reports only 3.7gb
while i'm not panicked (should i be?!), is there anything else i need do?
thanks

---

### Post by Vince4Amy on 2009-03-06
Do you have shared graphics memory, for example an onboard graphics processor instead of a separate card.

---

### Post by dimitriv on 2009-03-06
i hadn't thought of that, yes, it has Integrated Geforce®7 Series graphics. is that where the unaccounted 300mb is being used?

thanks

---

### Post by ClaytonOT on 2009-03-06
Post the results of;

> dmesg | grep -i memory

---

### Post by saigadu on 2009-03-06
No need to be worried. The missing memory is used by the On-Board-Graphics controller.

---

### Post by dimitriv on 2009-03-06
> **ClaytonOT said:**
> Post the results of;

hi Clayton

dmesg | grep -i memory

[    0.000000] init_memory_mapping

[    0.000000] init_memory_mapping

[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000

[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000

[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000

[    0.000000] PM: Registered nosave memory: 00000000b7fa0000 - 00000000b7fae000

[    0.000000] PM: Registered nosave memory: 00000000b7fae000 - 00000000b7fe0000

[    0.000000] PM: Registered nosave memory: 00000000b7fe0000 - 00000000b7fee000

[    0.000000] PM: Registered nosave memory: 00000000b7fee000 - 00000000b7ff0000

[    0.000000] PM: Registered nosave memory: 00000000b7ff0000 - 00000000b8000000

[    0.000000] PM: Registered nosave memory: 00000000b8000000 - 00000000fec00000

[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000

[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000

[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fef00000

[    0.000000] PM: Registered nosave memory: 00000000fef00000 - 00000000fff00000

[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000

[    0.004000] Your BIOS doesn't leave a aperture memory hole

[    0.004000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000

[    0.004000] Memory: 3917524k/5242880k available (3116k kernel code, 144872k reserved, 1575k data, 540k init)

[    0.004221] Initializing cgroup subsys memory

[    1.143899] Freeing initrd memory: 8453k freed

[    1.265965] Freeing unused kernel memory: 540k freed



Thank you

---

