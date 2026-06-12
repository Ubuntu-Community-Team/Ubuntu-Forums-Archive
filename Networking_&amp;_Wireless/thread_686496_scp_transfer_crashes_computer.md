---
title: "scp transfer crashes computer"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by jessej on 2008-02-03
Hello everyone.

I was trying to transfer a file from my wireless laptop over my local network to my desktop using scp, and before 250kb out of around 20mb was transfered the laptop froze.   Both computers are using 7.10.  I'm puzzled.

jessej

---

### Post by jessej on 2008-02-05
I also tried to just set up Apache on the laptop to try to move files that way and that freezes everything up as well.

---

### Post by jessej on 2008-02-21
?

---

### Post by dmizer on 2008-02-21
this is very strange.

did your wireless disconnect during the transfer?

is there anything in the ssh logs?

---

### Post by jessej on 2008-02-21
I know that the wireless isn't disconnecting, and I did search through the logs a bit, but there's nothing that particularly jumps out at me.

Another peculiar thing is that the computer will also crash if I try to pull a file from it from another computer.  I can still use scp to bring files in though, just can't send them out locally or remotely.

jessej

---

### Post by dmizer on 2008-02-21
same symptoms with other transfer protocols?  samfs, nfs, ftp ...

are you sure the computer is actually "crashing"?  it's possible that the transfer could be hogging so much memory that the computer can no longer function (though this should not happen), but that the transfer is actually still continuing.  i would start with watching some system monitoring meters during a transfer.

---

