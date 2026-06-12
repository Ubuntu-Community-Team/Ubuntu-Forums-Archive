---
title: "Removing programs"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by Moriarty123456 on 2010-09-10
Hi Peeps,

Having a minor issue with removing programs. Through the Software centre I choose 'uninstall' and the progress bar indicates I've removed the program. Then I look in applications and it's still there..

Some programs delete, but not all. Specifically Opera, Galeon, Epiphany, Adobe Reader don't. Anything to stop me just going to the directory where the programs are and deleting them?

Cheers.

---

### Post by 73ckn797 on 2010-09-10
You can open terminal and enter:
```
sudo apt-get purge "program name"
```cgange "program name" to whatever it is, without the quotes. 
There will be elements remaining so you could enter:
```
sudo apt-get autoremove "program name"
```

Sometimes I have found that a reboot will clear up any residual menu items or you can go to System/Preferences/Main Menu and delete the menu entries from there.

---

### Post by arochester on 2010-09-10
Open a Terminal and issue the command: sudo apt-get remove [name of program]

---

### Post by 73ckn797 on 2010-09-10
> **arochester said:**
> Open a Terminal and issue the command: sudo apt-get remove [name of program]
This too.

---

### Post by Moriarty123456 on 2010-09-11
Thanks all. Much appreciated.

---

### Post by gandaran on 2010-09-11
> **Moriarty123456 said:**
> Hi Peeps,

Having a minor issue with removing programs. Through the Software centre I choose 'uninstall' and the progress bar indicates I've removed the program. Then I look in applications and it's still there..

Some programs delete, but not all. Specifically Opera, Galeon, Epiphany, Adobe Reader don't. Anything to stop me just going to the directory where the programs are and deleting them?

Cheers.
software center doesn't remove programs completely, you should use synaptic package manager to remove applications and always mark for complete removal.

---

