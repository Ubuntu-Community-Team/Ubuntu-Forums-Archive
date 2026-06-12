---
title: "Just Installed 11.04, But OS Selector At Startup (grub?) Does Not Show"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by unknowngal on 2011-04-29
Hello! I just installed 11.04 as my title says, but my OS selector at startup doesn't show. All that shows up is a box on my monitor that moves around, saying "Input Not Found" or something similar. I hit enter and Ubuntu starts to load, I can hear the computer loading it. Then the box disappears and the Ubuntu login screen comes up. 

So far, the new Ubuntu seems to work fine, but I'm guessing the thing called grub (is that the OS selector at startup?) didn't install right. When I was installing the new Ubuntu, I selected to keep the local settings (I wish I could remember but I don't), though there were other settings regarding grub that I could have chosen but didn't, just that default setting.

Thanks for any help sent my way! Much needed and much appreciated!

---

### Post by wilee-nilee on 2011-04-29
Since you can get in run in the terminal
sudo update-grub

---

### Post by unknowngal on 2011-04-29
Thanks for your speedy reply! :) I actually saw that someone else posted the same issue during this time, and followed the instructions there.

[http://ubuntuforums.org/showthread.php?t=1742553](http://ubuntuforums.org/showthread.php?t=1742553)

Though perhaps just following the line of code you gave me would have worked too. :) In any case, thank you for replying! :D

---

### Post by wilee-nilee on 2011-04-29
> **unknowngal said:**
> Thanks for your speedy reply! :) I actually saw that someone else posted the same issue during this time, and followed the instructions there.

[http://ubuntuforums.org/showthread.php?t=1742553](http://ubuntuforums.org/showthread.php?t=1742553)

Though perhaps just following the line of code you gave me would have worked too. :) In any case, thank you for replying! :D

Cool I actually wondered if the fix wasn't there. The update-grub updates grub.:)

So if you edit grub with the default grub file, you run update-grub to apply the changes to grub.

---

### Post by Hedgehog1 on 2011-04-29
> **wilee-nilee said:**
> So if you edit grub with the default grub file, you run update-grub to apply the changes to grub.

Wait a minute; this all sounds a little too logical...  


***The 'Grubby' Hedge***

:KS

---

### Post by wilee-nilee on 2011-04-29
> **Hedgehog1 said:**
> Wait a minute; this all sounds a little too logical...  


***The 'Grubby' Hedge***

:KS

How much would grub update grub, if grub could update grub?

---

