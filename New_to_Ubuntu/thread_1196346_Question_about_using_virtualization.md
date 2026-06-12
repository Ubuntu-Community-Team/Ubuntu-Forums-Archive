---
title: "Question about using virtualization"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by ubunt22rock on 2009-06-24
Hi

I have been using ubuntu since Gutsy release. I have enjoyed using the virtualization software like virtual box.

Now I am going to replace my laptop and the new one I am eyeing has a p7450 intel processor.

It says it doesnt support intel's virtualization technology. Would I still be able to use software like virtual box? or I need to upgrade to a processor which supports this?

I know this is a bit off topic, but I posted this in hardware&laptop section about 3 days back and dint get any reply

hope someone notices this.

Cheers

---

### Post by SunnyRabbiera on 2009-06-24
Yes dont worry, it will work.

---

### Post by Bachstelze on 2009-06-24
> **ubunt22rock said:**
> It says it doesnt support intel's virtualization technology. Would I still be able to use software like virtual box?

Yes. Hardware virtualization support is only required in a limited number of cases, for example to run unmodified guest OSes in the Xen hypervisor. Full virtualization solutions like VMWare or VirtualBox don't require such things.

---

### Post by Sef on 2009-06-24
For future reference, there is Virtualization subforum under Other Community Discussions.

---

### Post by Old_Grey_Wolf on 2009-06-24
> **ubunt22rock said:**
> 
It says it doesnt support intel's virtualization technology. Would I still be able to use software like virtual box? or I need to upgrade to a processor which supports this?

You can still use Virtual Box; however, if you want to take advantage of type 1 hypervisors (bare metal) you really need the Intel or AMD virtualization technology. For example, the Xen hypervisor used by Red Hat or CentOS can work as a type 1 or type 2 hypervisor. For a description of type 1 or 2 you can read this [http://en.wikipedia.org/wiki/Hypervisor](http://en.wikipedia.org/wiki/Hypervisor).

---

### Post by ubunt22rock on 2009-06-25
Thank you all. Not only did I get my doubts cleared but I also learnt something I dint know about :)

---

