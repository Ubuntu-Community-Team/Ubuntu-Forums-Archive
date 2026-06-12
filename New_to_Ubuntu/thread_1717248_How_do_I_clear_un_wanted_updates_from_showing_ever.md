---
title: "How do I clear un wanted updates from showing everytime?"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by BigCityCat on 2011-03-29
Thanks

---

### Post by mcduck on 2011-03-29
> **BigCityCat said:**
> Thanks

Uninstall the programs you don't want to keep updated. ;)

Ubuntu only provides security updates and fixes for more serious bugs, so in general you really just should install all available updates.

If there's a specific package that is causing you troubles and you can't update it because of that, you can pin the version using Synaptic Package Manager (Select a package, then from the menu Package->Lock Version). But I wouldn't recommend doing that unless you *really* have to.

---

### Post by BigCityCat on 2011-03-29
Okay thats cool. It's just a feanza icon update but I removed that folder and it wants to update but fails because I manually removed it. Honestly I don't remember exactly.

---

### Post by BigCityCat on 2011-03-29
Not sure why I didn't think about using synaptic to remove the package. Thanks.

---

### Post by mcduck on 2011-03-30
> **BigCityCat said:**
> Okay thats cool. It's just a feanza icon update but I removed that folder and it wants to update but fails because I manually removed it. Honestly I don't remember exactly.

In that case you could just remove or disable the PPA repository where those icons come from (as I'm pretty sure they aren't in the offical repositories).

Although I'd probably try to fix the icon install and then remove them again using the package manager just to keep things nice and clean... ;)

---

