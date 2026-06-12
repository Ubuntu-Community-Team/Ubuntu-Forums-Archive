---
title: "How do I remove an entry from the Grub menu?"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by bamim2 on 2010-08-17
I updated my kernel & my system wouldn't boot up, so I had to remove  the kernel from the Package Manager. Now Grub shows a version of the  kernel that I don't have. How do I remove that version of the kernel  from showing up in Grub when my system boots up?

---

### Post by howefield on 2010-08-17
Did you try the solution in your other thread ?

> **drs305 said:**
> Does running "sudo update-grub" do it?

If not, go into synaptic, do a search for the kernel that is showing up which you want removed (such as 2.6.32-22) and remove the associated files (linux-headers-2.6.32-22, etc) then rerun update-grub.

---

### Post by bamim2 on 2010-08-17
Yes, that resolved the Grub problem & created a whole new problem. Now when I boot up my desktop has lost all of the changes I've made for the passed several months & my system has lost all of the updates I've installed for that period of time. 

Any thoughts or help?

---

### Post by howefield on 2010-08-17
> **bamim2 said:**
> Any thoughts or help?

Yes, just one thought.

updating Grub isn't to blame.

---

### Post by bamim2 on 2010-08-17
I know Grub isn't to blame. I know it's me. I'm just not doing something correctly. Or maybe lots of somethings.

I just rebooted & Grub still shows the old version of the kernel even though when I ran the command it showed that it removed it. Plus, all of the updates to my desktop are back & so are the updates that I installed over the passed month. 

When I look in PM, it shows 2.6.31.22 is installed again! 

How can I either get .22 to work correctly or remove it correctly & still keep everything else working in version .21?

---

