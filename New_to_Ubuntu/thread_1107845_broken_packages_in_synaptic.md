---
title: "broken packages in synaptic?"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by ami_nakata on 2009-03-27
hi -

In the Synaptic package manager there's a "Custom Filters" button at the lower left which, when pressed, allows one to select the "Broken" filter.  When I view my packages via that "Broken" filter I see ... well, everything; I see just the same thing using that filter that I see when I use the "All" filter.  Does that mean all my packages are broken?

Also, does anyone know what the "Package with Debconf" filter does?  Couldn't find any of this in the meager documentation for Synaptic. Was I looking in the wrong place?

thanks, 

- ami

---

### Post by cariboo on 2009-03-27
I don't get anything when using the custom broken packages filter. I would suggest you opn an Apllications-->Accessories-->Terminal and type:

```
sudo apt-get install -f
```

to make sure you have all the needed dependencies installed, then run:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

to make sure you are completely up to date.

Jim

---

### Post by bapoumba on 2009-03-27
Please make sure that Synaptic > Settings > Filter > Broken is set to show broken packages.
debconf is a package that handles questions to the user when configuring a package during install process (the kind you can get with dpkg-reconfigure).

---

### Post by ami_nakata on 2009-03-27
Thanks!  That solved it.  I don't know why, but my "Settings > Filters > broken" checkboxes were *all* checked.  I wouldn't have understood as easily without the screenshot, btw; nice. ( OT/IMO/@bapoumba/noflamesplease: French is the most beautiful language I've ever heard; I hope they speak it in heaven. Thanks again for your help! XD )

---

### Post by bapoumba on 2009-03-27
Glad you got it to work :)
And you are welcome!

---

