---
title: "how to access thunderbird in ubuntu"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Jack Shankle on 2009-01-15
I think I have download Thunderbird into Ubuntu and I think I have compiled it. Not sure of either. Now How do I access it????
Been trying for hours to do this.

Thanks for any help
1% Ubuntu working on 2% ubuntu

---

### Post by Ewingo401 on 2009-01-15
Firstly did you install Thunderbird from add/remove programs under the applications tab or from the website?  If you installed it from add/remove programs (which is recommended) you should just be able to click application, internet, thunderbird to access it.

---

### Post by clive littlewood on 2009-01-15
Hi

If you could tell us how you "installed" Thunderbird perhaps we can help you      :D


All you needed to do is use add/remove programs and searce for mozilla then thunderbird.

Clive

---

### Post by LowSky on 2009-01-15
if installed form add/remove or synaptic

applications> internet> thunderbird

compiled by hand
open a terminal and type
/*the file you installed it to*/thunderbird

---

### Post by stchman on 2009-01-15
> **Jack Shankle said:**
> I think I have download Thunderbird into Ubuntu and I think I have compiled it. Not sure of either. Now How do I access it????
Been trying for hours to do this.

Thanks for any help
1% Ubuntu working on 2% ubuntu

Thunderbird is available in the repositories.

```
sudo apt-get install thunderbird
```

After that it will be under Applications--->Internet.

That is all.

The Thunderbird you download from Mozilla is a precompiled binary and not source.  You would have needed to go into Mozilla's development section to get Thunderbird source code.

---

### Post by Jack Shankle on 2009-01-15
Thanks for replying.
I think I downloaded Thunderbird from the Mozilla web site.
I will try to delete all my errors. Some are in the Trash and won't
delete. Then I will use "add" or the "sudo" command by stchman to load
Thunderbird.

1% Ubuntu working on 2% Ubuntu

---

### Post by Jack Shankle on 2009-01-15
Thanks for all help.
Got Thunderbird installed and the profile from windows Thunderbird
installed. Another wrinkle appeared. Can't run Thunderbird because another
instance of thunderbird is running. I have checked the profiles.ini
and it looks correct.

1% Ubuntu working on 2 % Ubuntu

---

