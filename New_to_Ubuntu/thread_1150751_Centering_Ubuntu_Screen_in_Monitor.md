---
title: "Centering Ubuntu Screen in Monitor"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Bezmotivnik on 2009-05-06
For some reason, Ubuntu always seems to be off-center in my monitors, to the left or right.

In that I am using this monitor for two systems via a KVM switch, I can't correct Ubuntu's error with the monitor because the other system will be off center when I switch over to it.

Is there a way to tune Ubuntu's display position *within* Ubuntu so it centers normally on my monitor?

Thanks for any help with this.

---

### Post by NightwishFan on 2009-05-06
;/ If your other OS is Windows, it is Windows that is off center. :popcorn:

Is there a settings reset button on the monitor? Perhaps that would help.

---

### Post by mick8985 on 2009-05-06
I think there are settings to adjust this depending on which video driver you are using.

---

### Post by Bezmotivnik on 2009-05-06
> **mick8985 said:**
> I think there are settings to adjust this depending on which video driver you are using.
I'm using the nVidia driver.

I think there's a way to do this, too, I've just forgotten how.

---

### Post by mick8985 on 2009-05-06
I checked for the Nvidia driver I thought it was something like:

```
Option "Hpos" "+2"
Option "Vpos" "-3"
```

but I can't see anything in the documentation [here]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html")
Perhaps I missed it.

---

### Post by Bezmotivnik on 2009-05-06
> **mick8985 said:**
> I checked for the Nvidia driver I thought it was something like:

```
Option "Hpos" "+2"
Option "Vpos" "-3"
```

but I can't see anything in the documentation [here]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html")
Perhaps I missed it.
I'm virtually positive there's a way to do this, too. :-k

I'll keep looking.  Resetting the monitor every time I switch out between running systems is a non-starter, though.

---

### Post by utnu on 2009-06-19
my display was too far right, covering up most of the Trash icon.

i clicked System / Preferences / Appearance /  Visual Effects / Extra.

it downloaded a better driver than original; now the display is Centered

---

