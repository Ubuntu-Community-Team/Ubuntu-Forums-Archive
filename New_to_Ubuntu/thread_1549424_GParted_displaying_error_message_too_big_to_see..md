---
title: "GParted displaying error message too big to see."
date: 2010-08-09
forum: New to Ubuntu
---

### Post by Dovdimus Prime on 2010-08-09
I tried to follow some instructions from the pdf guide Getting Started With Ubuntu 10.04. I'm trying to install Ubuntu as dual boot on my Windows XP laptop. In the installation wizard, in the bit about partitioning, I'm supposed to see an option called 'Install them side by side choosing between them each startup', but it's not there. I only have 'Erase and use the entire disk' (which is the default, a little sneakily) and 'Specify partitions manually'. I chose 'Specify partitions manually, but I couldn't work it out.

I decided to exit the wizard and try to create a new partition for the install using GParted instead. When I select the existing partition and double click it, I get an information dialogue box with a grave warning: 'ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE! The usage of the /f parameter is very IMPORTANT! No.....'

But the dialogue is too tall for the screen, and I can't read the rest. I don't appear to have a way to move the box upwards past the top of the screen, or to resize it in any way.

So, anyone know a) Why the standard dual boot partitioning option isn't available in the installer wizard, b) what Ubuntu thinks is wrong with my Windows partition, or c) what the rest of the error message should be?

Thanks

David

---

### Post by Mark Phelps on 2010-08-10
> **Dovdimus Prime said:**
> So, anyone know a) Why the standard dual boot partitioning option isn't available in the installer wizard,
Not with the little info you provided.  Could be that your drive already has the maximum number of partitions, thus, a new one can not be created.  Open a terminal and run "sudo fidsk -lu" (that's a lowercase L, not a one)
>  b) what Ubuntu thinks is wrong with my Windows partition,
It believes your NTFS partition is "dirty" and is telling you to run chkdsk to fix it.  IT will keep doing that until you fix it.
>  or c) what the rest of the error message should be?
Don't know.

See the MS page below for details on using chkdsk:

[http://support.microsoft.com/kb/315265]("http://support.microsoft.com/kb/315265")

---

