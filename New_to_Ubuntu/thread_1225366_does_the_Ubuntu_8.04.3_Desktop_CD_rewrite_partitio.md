---
title: "does the Ubuntu 8.04.3 Desktop CD rewrite partitions?"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by grikdog on 2009-07-28
I've downloaded the ubuntu-8.04.3-desktop-i386.iso (and will shortly burn the CD), to have ready in case of problems when I upgrade from Hardy to Ibex or Jaunty later next month.  If necessary, I could also download the Dell Ubuntu 8.04 reinstall iso, but I'd rather not do that, because it will destroy my current partition table.

My question is, does the Ubuntu 8.04.3 Desktop CD rewrite partitions, or can I trust it to do the right thing?

---

### Post by jocampo on 2009-07-28
> **grikdog said:**
> I've downloaded the ubuntu-8.04.3-desktop-i386.iso (and will shortly burn the CD), to have ready in case of problems when I upgrade from Hardy to Ibex or Jaunty later next month.  If necessary, I could also download the Dell Ubuntu 8.04 reinstall iso, but I'd rather not do that, because it will destroy my current partition table.

My question is, does the Ubuntu 8.04.3 Desktop CD rewrite partitions, or can I trust it to do the right thing?

what you mean with rewrite, if you run the Live CD option? ... or, if you decide to upgrading using the CD? If you use the CD to upgrade, is going to detect whatever you have there and will respect that, unless you specifically tell, "format partition".

Did you put /home on its own partition? If not, you should, that way is easier to re-install or recover data

---

### Post by nhasian on 2009-07-28
it wont change any data on your hard disk if you just boot from the liveCD to get to the ubuntu livecd desktop.  if you plan on using it to install ubuntu onto a computer, then yes it can potentially change the partitions on your hard disk and destroy all the existing data.  during the partitioning section during installation take your time and pay close attention to what you choose and where you choose to install ubuntu.  I always prefer to use the manual partitioning option so i have full control over where i put the root and home partitions.

---

### Post by grikdog on 2009-07-28
> **jocampo said:**
> what you mean with rewrite, if you run the Live CD option? ... or, if you decide to upgrading using the CD? If you use the CD to upgrade, is going to detect whatever you have there and will respect that, unless you specifically tell, "format partition".

Did you put /home on its own partition? If not, you should, that way is easier to re-install or recover data
Thanks.  Yes, I meant install from CD, not run LiveCD.  It's good that Ubuntu respects my existing partitions.  But it's bad, because you've given me a good reason to repartition anyway, just to get /home isolated.  I may have to do it that way.

Thanks, again.
d

---

