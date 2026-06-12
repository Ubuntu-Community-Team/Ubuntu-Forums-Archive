---
title: "how to uninstall pclinux os"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by mafaldaspeaks on 2010-05-16
I was dual booting between windows 7 and pclinux. I realized I didn't really like pclinux so I decided to install kubuntu side by side with windows 7. However, I didn't know how to install kubuntu in such a way that it would install over pclinux too, so what I now have are win7, pclinux and kubuntu. How do I uninstall or delete pclinux so I can use the space it's using?

---

### Post by lkraemer on 2010-05-16
You could use something like Supergrub to replace the MBR in Win 7
or do it from within Windows Recovery Console, but I'd just:
1.  Save any DATA from Kubuntu
2.  Save any Data from PCLinuxOS
3.  Boot Ubuntu LiveCD, Make sure everything works as expected,
    and make sure you know which partition is for each specific OS.
4.  Run Gparted and Delete the Partitons for Kubuntu & PCLinuxOS
5.  Install Ubuntu 10.04
6.  Then ~6-8 Months down the road Delete Win 7.  :~)  
Then, you have the PERFECT COMPUTER with the PERFECT OS!

lk

---

### Post by mafaldaspeaks on 2010-06-22
> **lkraemer said:**
> You could use something like Supergrub to replace the MBR in Win 7
or do it from within Windows Recovery Console, but I'd just:
1.  Save any DATA from Kubuntu
2.  Save any Data from PCLinuxOS
3.  Boot Ubuntu LiveCD, Make sure everything works as expected,
    and make sure you know which partition is for each specific OS.
4.  Run Gparted and Delete the Partitons for Kubuntu & PCLinuxOS
5.  Install Ubuntu 10.04
6.  Then ~6-8 Months down the road Delete Win 7.  :~)  
Then, you have the PERFECT COMPUTER with the PERFECT OS!

lk
 Great, thanks so much!

---

