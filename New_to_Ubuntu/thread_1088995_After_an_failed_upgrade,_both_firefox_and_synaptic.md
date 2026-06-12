---
title: "After an failed upgrade, both firefox and synaptic package manager don't work now"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by yujiao on 2009-03-06
Hi, 

I am a new user of Ubuntu. This morning i just clicked the update icon, and there were 8 items to be upgraded: firefox, firefox-3.0, firefox-3.0-branding, firefox-3.0-gnome-support, firefox-gnome-support, libpng12-0, xulrunner-1.9.  I click the "install updates" icon, and then the update manager gave me an warning window saying that the software can't be authenticated, i neglected the warning and try to update these items. But It said that some of the packages could not be retrieved from the servers. 

After that i found my fierfox can't connect to the internet anymore.

So my thinking was to install another web browser, but it happened that the synaptic package manager can't retrieve any packages from the repository now. 

Does anyone has an idea on this problem? Any help will be appreciated. Thanks!

---

### Post by sneeks on 2009-03-06
is there any broken packages???

---

### Post by taurus on 2009-03-06
What are the outputsof these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

