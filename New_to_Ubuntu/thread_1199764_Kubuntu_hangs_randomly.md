---
title: "Kubuntu hangs randomly"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by ythaaa on 2009-06-29
Hi all,

I am relatively new to kubuntu.

Recently my kubuntu kdm hangs randomly. It happen so randomly. 

When it hangs, everythings does not work except the mouse. I can move my mouse but cannot click anything. I cannot also ctrl+alt+F1 to switch to terminal mode. 

Can anyone help me with this. I cannot reproduce the hang exactly. Sometimes it happens when i do only small things.

THanks.

---

### Post by cmnorton on 2009-06-30
When you reboot, you'll need to look at the your logs under /var/log (probably using  sudo tail /var/log/syslog and sudo /var/log/messages). Also look at the output from dmesg | less. You may see a message indicating what was going on at the time of the hang, and you can start trouble-shooting from there.

If you can post what was running at the time of the hang, that would also help. Which version of Kubuntu is this?

---

### Post by milton1 on 2009-06-30
This is a big and well known problem in 9.04. I am guessing you have an intel integrated graphics card? Kernel updates have improved the issue somewhat, but it is still an issue, and still has open bugs associated with it. Best option is to disable desktop effects and hope they fix it soon.

---

