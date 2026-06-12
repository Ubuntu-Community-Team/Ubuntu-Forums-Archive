---
title: "ubuntu log into terminal. No gui"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by e.jejcic on 2011-01-10
I-m running Ubuntu 10.04, last friday I made an update and since it logs directloy into terminal mode, I guess. It happened before and I manage to return to GUI interface with Ctrl Alt F7 but,now does-nt work. I am wondering if there is another key combination to do the same work. I will appreciate any comments or help. Thanks you all for your attention. Thanks again from Eduardo.

---

### Post by oldos2er on 2011-01-10
After you login, run **startx**

---

### Post by e.jejcic on 2011-01-10
Well. Thanks for the repply.I used an old distro (9.10)to ask for help, and when I come back to 10.04 it logs in beatifully.I didn't have a chance to try it (your sugestion) but I'll remember for next time. I appreciate tour feedback.
I used to watch on TV a serie called "el hombre del rifle" and the actor called "Cheyene Body"  (1960). Thank you very much for your help.
Regards from Eduardo, Buenos Aires, Argentina Cheeee.

---

### Post by oldos2er on 2011-01-10
You're welcome.

---

### Post by elkinsj2 on 2011-01-15
Ann,
Is this a long term solution?  This fix has worked, but as it is not my computer, the owner will be very annoyed if she has to do that every time.

Thanks for your help.

---

### Post by Kaplan Crunch on 2011-01-15
[elkinsj2]("http://ubuntuforums.org/member.php?u=780683"):

It's not a permanent fix (or at least its not for backtrack and most other distros)
I pretty sure you can make it stick by changing permissions or something of the sort.



(Sorry I'm not more helpful)

~KC

---

### Post by elkinsj2 on 2011-01-16
Thanks.  I will keep trying.

---

### Post by oldos2er on 2011-01-16
> **elkinsj2 said:**
> Ann,
Is this a long term solution?  This fix has worked, but as it is not my computer, the owner will be very annoyed if she has to do that every time.

Thanks for your help.

Is GDM installed? If so, perhaps it needs to be reconfigured. **sudo dpkg-reconfigure gdm**

---

