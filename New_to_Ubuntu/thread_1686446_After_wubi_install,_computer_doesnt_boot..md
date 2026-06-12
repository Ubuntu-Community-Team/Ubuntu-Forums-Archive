---
title: "After wubi install, computer doesnt boot."
date: 2011-02-12
forum: New to Ubuntu
---

### Post by Heavenborncaptain on 2011-02-12
I was very intruiged as to try linux, so I downloaded wubi and installed it, after rebooting and selecting it from my boot menu, it installed itself. Now my computer doesnt show anything when I start it. my harddrive also doesnt seem to spin, but I don't think its a dead HDD because I had no indications of it dying previous to this. My thoughts are that its a graphics driver problem. I'm thinking that if I boot into Ubuntu from a live cd, then uninstall it from there, but I'm not sure of the exact steps how to do that. Any help would be greatly appreciated.

---

### Post by Rubi1200 on 2011-02-12
Hi and welcome to the forums :-)

Does Windows still boot normally?

After starting the Wubi process in Windows and rebooting, did Ubuntu install completely and then restart? Was it after this point that the problems occurred? I just want to be clear on the process.

What graphics card do you have installed?

---

### Post by Heavenborncaptain on 2011-02-12
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Does Windows still boot normally?

After starting the Wubi process in Windows and rebooting, did Ubuntu install completely and then restart? Was it after this point that the problems occurred? I just want to be clear on the process.

What graphics card do you have installed?
Hello and thank you for the welcome,

No, windows 7 does not boot at all. I do not see anything when I start my computer, this happend after I had selected ubuntu from the bootmenu and it had installed itself, I'm currently using a nvdia 470 graphics card.

---

### Post by Rubi1200 on 2011-02-12
Okay, so here is what you need to do please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Hopefully, the results will tell us what is going on so we can help you resolve this quickly.

---

