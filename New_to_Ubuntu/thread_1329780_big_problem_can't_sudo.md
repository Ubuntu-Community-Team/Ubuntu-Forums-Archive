---
title: "big problem can't sudo"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by cmcanulty on 2009-11-17
I can't update, run synptic or do any admin or do gksudo when I try any of above nothing happens here is what I get when I try to chown a file to set it back OK I mistakenly edited the sudoers file wrong in  /etc/ have no idea how to fix
```
cmcanulty@Gateway:~$ sudo chown -R cmcanulty /etc/sudoers
sudo: /etc/sudoers is mode 0640, should be 0440
Segmentation fault
```

---

### Post by MonoDeem on 2009-11-17
Recovery mode / drop to root shell prompt.

---

### Post by cmcanulty on 2009-11-18
Dumb question but how doI do that? I already tried sudo su

---

### Post by drs305 on 2009-11-18
> **cmcanulty said:**
> Dumb question but how doI do that? I already tried sudo su

Reboot. From the grub menu, choose the recovery mode (single-user mode). If you don't normally see a menu, hit ESC early in the boot process (or hold SHIFT in Karmic).  After you select the recovery mode, you will eventually be given a menu. Select the option to boot to a root prompt

Once you get there, run this command:
```

chmod 0440 /etc/sudoers

```

---

### Post by cmcanulty on 2009-11-18
Whew thanks! I really wish Ubuntu had a system restore like windows. Without it one typo and it's a big problem. Your root prompt boot fixed it all up.

---

### Post by spikyjt on 2009-11-18
er... it does have a system restore - you just used it. It even has a "Repair a broken system" mode on the CD.

Do you mean system restore points, the service that slows down your Windows machine all the time? It's called backing up!

---

### Post by Cheesemill on 2009-11-18
How did you edit your sudoers file?
You should always use the visudo command to edit it as it checks the file for any errors before saving it.

---

### Post by cmcanulty on 2009-11-18
Thats what I used and checked very carefully but it messed everything up, back to normal now.

---

### Post by cmcanulty on 2009-11-18
I back up regularly, I meant a misstep on a command that causes big problems. Sys restore is not a backup but a return to a previous condition of system itself.

---

### Post by przarnke on 2011-02-23
i went to root shell prompt and try to reset sudos
type in chmod 0440/etc/sudoers
and got no operand after /etc/sudoers 
i'm lost  at what to do next

---

### Post by jwcalla on 2011-02-23
> **przarnke said:**
> i went to root shell prompt and try to reset sudos
type in chmod 0440/etc/sudoers
and got no operand after /etc/sudoers 
i'm lost  at what to do next

You need a space between 0440 and /etc/sudoers.

---

