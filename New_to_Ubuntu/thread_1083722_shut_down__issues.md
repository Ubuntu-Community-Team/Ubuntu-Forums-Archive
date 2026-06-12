---
title: "shut down  issues"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by amd 64 x2 overclocked on 2009-03-01
i have reflashed my bios and now it hangs on shut down the only way to shut down is to hold down the power button.

---

### Post by lukjad on 2009-03-02
What happens when you go to System->Shutdown?

---

### Post by amd 64 x2 overclocked on 2009-03-03
it does the same thing. hangs up after saying message from robert@root to kill then starts to boot down and then freezes.

---

### Post by lukjad on 2009-03-04
Okay, try this. Go to the terminal (*Applications-Accessories->Terminal*) and type:

```
sudo halt
```

This should work, at least as a temporary fix.

---

### Post by amd 64 x2 overclocked on 2009-03-05
same thing sudo halt system freezes then i have to turn off with powerbutton. I think the new flash doesn't support acpi.

---

