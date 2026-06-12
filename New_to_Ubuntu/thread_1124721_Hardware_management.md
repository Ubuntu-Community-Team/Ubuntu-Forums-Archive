---
title: "Hardware management"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Darthpc on 2009-04-13
Is there a hardware manager in Ubuntu I have just installed a 4 port fire wire card but I don't have any devices to test it yet. How can I tell if the system knows it is there?

---

### Post by wilbbe01 on 2009-04-13
lspci at the commandline might show it.  That doesn't necessarily mean it is functioning though.

---

### Post by Darthpc on 2009-04-13
it said unrecognized command

---

### Post by Paqman on 2009-04-13
Hardinfo and sysinfo are two packages that will show your machine's hardware.

---

### Post by Darthpc on 2009-04-13
did i need to use sudo or some other command before the ispci

---

### Post by wilbbe01 on 2009-04-13
that is a lowercase "L" so "lspci"

---

### Post by Darthpc on 2009-04-13
Thanks Everyone the card is there and sorry about the confusion on the syntax i forgot to put on my glasses

---

### Post by Paqman on 2009-04-13
> **Darthpc said:**
> ispci

lspci

That's a lower-case L, not an i. The command ls means "list", so lspci shows all the pci gubbins in your machine.

---

