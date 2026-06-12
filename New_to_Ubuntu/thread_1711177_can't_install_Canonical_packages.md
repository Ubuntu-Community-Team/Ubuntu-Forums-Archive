---
title: "can't install Canonical packages"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by solutionorppt on 2011-03-20
Just installed NBR 10.10 on an old Acer One Aspire after XP crapped the bed... 

I can't get it to install the Canonical package - it asks me to insert the cd-rom whenever I press 'Add Volume' under "Software>Edit>Software sources", which is not physically possible for the obvious reason that I am using a netbook...

Can I just do this directly from terminal?  It worked for the flash player installation when I ran "sudo apt-get install  flashplugin-nonfree"...

Now I love me some Linux (my desktop has been in dual-boot for the last 2 years), but if we knew this was a netbook remix, why are we still looking for software in the one place no netbook has?

---

### Post by 5149.5 on 2011-03-21
Update Manager>Settings>Ubuntu software>uncheck the CD_ROM box

---

### Post by solutionorppt on 2011-03-21
> **5149.5 said:**
> Update Manager>Settings>Ubuntu software>uncheck the CD_ROM boxI did this immediately upon installation.

---

### Post by ankspo71 on 2011-03-21
Hi,
Clicking on 'Add Volume' in this case is has the same meaning as 'Add a CD'. I think this is why you are prompted to insert a CD.

What Canonical package are you referring to? Do you mean you want to enable the "Canonical Partners" repository? There should be a listing already there in your Software Sources list, but it is disabled. To enable them, simply add a checkmark in front of Canonical Partners by clicking on the little box (it might take a few seconds for it to apply), then click on the close button when you are done.

Hope this helps.

---

