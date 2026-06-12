---
title: "Network Manager Applet Missing"
date: 2017-10-02
forum: Networking &amp; Wireless
---

### Post by Daniel_Devor on 2017-10-02
Network Manager Applet seems to be missing from Ubuntu 16.04. I have been unable to recover or install the "nmManager Applet" and would appreciate any help or useful suggestions.

---

### Post by Frogs Hair on 2017-10-04
Install the following ,open the application, and navigate to the indicator and make sure it's enabled . I can't provide the location due to being on a different desktop environment.  ```
sudo apt-get install dconf-tools
```

---

### Post by gurdenite on 2017-10-04
Having done a search with the ever useful Synaptic Package Manager it appears there isn't a package "nmManager Applet" or "nm-applet" in the 16.04 repositories, but there is a "network-manager-gnome" and according to the description published in Synaptic this package includes the systray applet.

Presuming you still have a working internet connection...

```
sudo apt-get install network-manager-gnome
```

should hopefully get you sorted.

---

### Post by wildmanne39 on 2017-10-04
*Thread moved to **Networking & Wireless for a better fit**.*

The command in the post above should restore nm-applet if there is not something else going on.

---

