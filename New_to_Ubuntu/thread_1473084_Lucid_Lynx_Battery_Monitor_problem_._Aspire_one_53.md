---
title: "Lucid Lynx Battery Monitor problem . Aspire one 532h"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by sharan.kevryn on 2010-05-04
Ive installed the lucid lynx netbook remix on my acer aspire one 532h netbook. The battery monitor seems to behaving funny. it doesnt seem to be able to tell the correct amount of charge left. It suddenly become 0% and the system hibernates. but when i restart it becomes normal and the level would return to 50% or so ( the correct amount ) . is there a way this can be solved?? or can i change the inbuilt battery monitor applet with another battery monitor applet?? will that solve it?

---

### Post by Chrissss on 2010-05-29
Someone reported here something similar... [http://forum.ubuntuusers.de/topic/acer-aspire-one-532-akku-anzeige-komisch/](http://forum.ubuntuusers.de/topic/acer-aspire-one-532-akku-anzeige-komisch/) (Sorry, it's german) The reason was hddtemp, as soon as it was removed, the problem was gone.

---

### Post by levhita on 2010-06-02
Same problem here, But i doesn't have hddtemp installed...

---

### Post by natacho on 2010-06-04
same problem :-(

---

### Post by EricBellavance on 2010-06-11
I reported the bug here

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/592908](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/592908)

Eric

---

### Post by iLag!!!!! on 2010-06-11
I'm using Kubuntu on a 532h, and I'm having the same problem as above, as well as another one:
When I first startup, the battery indicator can't even detect that there's a battery installed; I have to suspend and resume the computer for it to even detect there's a battery, and then is has the OP's problem.
I'm sure this is because the battery monitor daemon isn't loading correctly and a simple console command can fix this.

---

### Post by Knowsnothing on 2010-11-23
How can I go about disabling hddtemp?

Cheers

---

