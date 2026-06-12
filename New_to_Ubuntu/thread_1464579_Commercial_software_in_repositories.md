---
title: "Commercial software in repositories"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by RTrev on 2010-04-28
I was notified in Synaptic that new in the repository was an editor called "uex" which sounded interesting.  Installed it, fire it up, and was met with something I haven't seen for years: a thirty day trial period.  Eeek!

I knew the software store would be handling commercial software, but I'm running Lubuntu and only use Synaptic or the command line.  From these, there is no indication I can find that this was a commercial program with a built-in time bomb for deactivation.

Maybe such programs could have some additional indicator icon in Synaptic?

I'm not opposed to people selling software, of course, but it would be good to know in advance if that isn't what we're interested in.

---

### Post by SnickerSnack on 2010-04-28
Did you add additional repositories?

---

### Post by Temposs on 2010-04-28
Wow, I've never seen that before! I don't think most people know this is in the repository! It's in Ubuntu 9.10 as well. I agree that this ought to be marked as non-free software.

---

### Post by RTrev on 2010-04-28
> **SnickerSnack said:**
> Did you add additional repositories?

Yes, I did, BUT this package is in Lucid/Main.

---

### Post by sisco311 on 2010-04-28
uex is in the Canonical Partner Repository. The partner repository offers access to proprietary and closed-source software.

But, I do agree with you, they should indicate the license in the description. 

Perhaps you would find *apt-cache madison packagename* useful, it prints the repository from where the package is available.

---

### Post by Temposs on 2010-04-28
> **SnickerSnack said:**
> Did you add additional repositories?

Check Synaptic for yourself. It's in the default repositories...specifically it's in "archive.canonical.com/main"

So, it seems like they've separated out the commercial software into a separate repository that doesn't have the ubuntu label. But this is not apparent to the normal user in the Ubuntu Software Center.

The key is to notice the "License" near the bottom of the description in the UltraEdit entry in Ubuntu Software Center. The "License" says "Unknown". 

So, I suppose if you want to make sure you're only downloading free software, make sure it has a free software license before you download it(GPL, BSD, MIT, Apache, etc)

---

### Post by Temposs on 2010-04-28
Here's a listing of the apps in this commercial repository, for future reference:

[http://www.ubuntu.com/products/SoftwareCatalogue](http://www.ubuntu.com/products/SoftwareCatalogue)

---

