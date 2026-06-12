---
title: "Reading Battery information (acpi -i)"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by audit on 2010-05-01
When I entered ```
acpi -i
```

I received this information:
```
Battery 0: Charging, 100%, charging at zero rate - will never fully charge.
Battery 0: design capacity 4400 mAh, last full capacity 2973 mAh = 67%
```

Is this telling me that my battery can now only hold 67% of it potential?

Any insight appreciated.

---

### Post by Jon Monreal on 2010-05-02
Yes; 2973 is 67% of 4400. This means that the based on how much your battery charged to full capacity and how much it was designed to charge to, it can only hold 67% of its design charge.

You can see the same information by clicking on the battery icon in your Indicator Applet, clicking on "Laptop battery......", and scrolling down on the listing until you get to "Capacity".

---

### Post by isbiyanto on 2010-05-18
> **Jon Monreal said:**
> Yes; 2973 is 67% of 4400. This means that the based on how much your battery charged to full capacity and how much it was designed to charge to, it can only hold 67% of its design charge.

You can see the same information by clicking on the battery icon in your Indicator Applet, clicking on "Laptop battery......", and scrolling down on the listing until you get to "Capacity".

thanX 4 share

---

