---
title: "Won't restart, how to fix?"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by shelbyvision on 2010-09-22
I installed Ubuntu 10.04 on my HP Compaq nc6220 laptop a couple months ago, and it works great! Just one minor problem I'd like to fix: restart doesn't work. It worked fine on the same machine with 9.04. Now when I try to restart, it goes to the black screen with the Ubuntu logo with the row of dots under it, and a couple of the dots turn red, and then it just stops. I have to shut it down and restart it manually. Is there a fix for this?
Thanks,
Steve

---

### Post by zeroseven0183 on 2010-09-22
Try ```
sudo reboot 
``` in the Terminal and see if the same thing happens.

---

### Post by shelbyvision on 2010-09-22
That produces the same result.

---

### Post by linux-hack on 2010-09-22
try ```
sudo init 6
```

---

### Post by Soul-Sing on 2010-09-22
acpi=force may be an idea.

/etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

---

### Post by shelbyvision on 2010-09-22
OK, I tried all the suggestions, no luck.

---

### Post by Soul-Sing on 2010-09-22
> **shelbyvision said:**
> OK, I tried all the suggestions, no luck.

post #5 I missed the sudo update-grub....
please give that a try after the suggestion(s) in #post 5

---

### Post by shelbyvision on 2010-09-22
> **leoquant said:**
> post #5 I missed the sudo update-grub....
please give that a try after the suggestion(s) in #post 5

I was really hoping that was the answer, but it's not.

---

### Post by TCHebb on 2010-09-22
IIRC pressing spacebar during shutdown gets rid of the nice splash screen and shows you the console output. It may shed some light on what's happening if you can post the last few lines before it hangs.

---

### Post by Flos Headford on 2010-09-22
Pretty much the same problem as the Original Poster, so I'll be following this one.
I can restart with
```
sudo shutdown -r now
```
but it doesn't look too good if a Windozer is looking.
And I'm interested in why the button stopped working.
Kind regards,
Flos

---

### Post by shelbyvision on 2010-09-22
Still, nothing that has been suggested so far works.

---

### Post by Soul-Sing on 2010-09-23
```
sudo poweroff
```

---

### Post by zeroseven0183 on 2010-09-24
Check if you have ACPI standby state options in the BIOS. That could be one cause.

---

### Post by shelbyvision on 2010-09-24
> **zeroseven0183 said:**
> Check if you have ACPI standby state options in the BIOS. That could be one cause.

The BIOS is completely separate from the operating system, right? I haven't touched the BIOS, and restart worked fine before I switched to 10.04.

---

### Post by adwhitenc on 2010-09-24
for good measure, i would go into ctrl+f2 and then use shutdown -h now

---

