---
title: "wake on lan after shutdown"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by amautsch on 2006-10-21
hello there,
i've got a little problem, 
that seems to be discussed a lot in the forums,
but i haven't found a solution yet :(

After Upgrading from debian (kernel 2.4)
to kubuntu 6.06, my wake on lan does not work anymore.
TO be specific, it does not work,
after shutting down linux.

If you pull the power plug for 2 seconds and reconnect,
wake on lan will work.

It won't after shutdown in kubuntu is called.

I allready tried to :

- disable acpi and apic in grub
- to call ethtool before shutdown

The lights of the nic, are btw. always lit.

Any solution to this ?

thanx in advance

---

### Post by ariek on 2006-10-22
I'm having the same situation here.
Anyone?

---

### Post by ariek on 2006-10-22
After reading [http://ubuntuforums.org/showthread.php?t=250034&highlight=wake+on+lan](http://ubuntuforums.org/showthread.php?t=250034&highlight=wake+on+lan) I figured that an upgrade could be the solution. So I upgraded my Dapper server to Edgy. The problem is solved now.

---

### Post by amautsch on 2006-10-25
great .. good that i installed dapper just 2 weeks ago :)
But thanx for the answer.
How can you upgrade dapper to edgy ?
Not via apt-get ?

---

### Post by ariek on 2006-10-26
check out [http://ubuntuforums.org/showthread.php?t=227052](http://ubuntuforums.org/showthread.php?t=227052) for upgrade info.

---

### Post by amautsch on 2006-10-27
thanks for the info ...

i upgraded to edgy,
but that did not solve my problem :(

---

### Post by GuillemVTR on 2006-12-08
Hi,

Today I installed "Ubuntu 6.10 Server (Edgy Eft)" on an old "Dell Optiplex G1" and I've got the same problem.

Any idea?

Thanks!

---

