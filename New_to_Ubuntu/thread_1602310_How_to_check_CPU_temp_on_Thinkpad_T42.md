---
title: "How to check CPU temp on Thinkpad T42"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by maja_z on 2010-10-21
Hi! I've just 'refurbished' my old T42 (spilled one whole cup of coffee (200ml!!) into it) and installed 10.10. Works amazingly well! But I don't trust it completely (rather my reassembly skills) and would like to keep an eye on the cpu temp. 

Now from what I understand lm-sensors won't work. I've done

sudo apt-get install acpi

But that's as far as I got :???: What do I do now? 

I don't need it to be monitored constantly, on my desktop I just type 'sensors' to see what's going on, what would be the equivalent with acpi? 

I just got kind of freaked out reading about all the dangers of lm-sensors on a thinkpad - obviously I read that after I ran sensors-detect (!) although it all seems fine?

---

### Post by Hippytaff on 2010-10-21
You can either install something like conky, or 
 
```

acpi -V

```
 
will display stats like temperature but not constantly

---

### Post by maja_z on 2010-10-21
That's the one! Thanks!

---

