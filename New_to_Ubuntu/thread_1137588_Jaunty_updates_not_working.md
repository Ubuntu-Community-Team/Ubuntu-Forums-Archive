---
title: "Jaunty updates not working"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by urvaksh on 2009-04-25
Upgraded to Jaunty. But when I run a check for updates, I get a "Not all updates can be installed.Run a partial update..." When I try to run a partial update, the update manager disappears
I also see two updates - one for Brasero and the other for liblucene2.java. Neither updates can be checked for installation.
Any help would be appreciated. Thanks

---

### Post by 73ckn797 on 2009-04-25
Try opening terminal and ruinning these commands:

```
sudo apt-get update
```

Then:
```
sudo apt-get upgrade
```

See how that works.

Did you install with the final release or a beta release?

---

### Post by urvaksh on 2009-04-26
final release

---

### Post by urvaksh on 2009-04-26
I tried the terminal commands and the issue still remains. the brasero and liblucene updates didn't go through.

---

### Post by organicanagram on 2009-04-26
Press alt+f2 then type 
sudo synaptic package manager 
to open it with administrative privilages. press alt-c then select "upgradable (upstream) from the menu. the packages should be listed, click the boxes next to them and select "mark for upgrade". Then click the apply button at the top.

---

### Post by urvaksh on 2009-04-26
Thanks, Organicanagram. Your instructions worked :)

---

### Post by DeadMetal on 2009-04-26
Thanks, that also solved it for me, I had the same problem after upgrading to Jaunty.

---

### Post by warren94 on 2009-04-26
My update manager only allows the 'check' button to be used, after i have checked, the same occurs :S
should i do the above?

---

### Post by warren94 on 2009-04-26
So I did the synaptic route and it worked.
Thanks organicanagram.

---

### Post by talsemgeest on 2009-04-26
> **warren94 said:**
> My update manager only allows the 'check' button to be used, after i have checked, the same occurs :S
should i do the above?
Same problem here, and a ```
sudo apt-get update
``` ```
sudo apt-get upgrade
``` ```
sudo apt-get dist-upgrade
``` did the trick.

---

