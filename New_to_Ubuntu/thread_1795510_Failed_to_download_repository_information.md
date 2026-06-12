---
title: "Failed to download repository information"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by colio on 2011-07-02
Need some help on a problem I've been having for a couple of weeks.  Whenever I run the update manager, I get a msg saying Failed to download repository information.  When I click the detail button, I get this:

W:Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I looked in Synaptic for these items and could not find them.  I changed servers and it still happens.  I'm out of ideas.  Please, please dumb down any suggestions as much as possible, especially if it involves the command line.  I'm not very familiar with generic commands.

thanks-

---

### Post by Bucky Ball on 2011-07-02
Have you recently upgraded to a newer release? These items are in your sources list (rather than Synaptics). Open update manager then 'Settings' in the bottom left corner and that will show you your software sources. In the second tab (third party or something like that) you should find that source.

You can disable that source and that will fix your issue for now but then Open Office will not be updated.

---

### Post by _0R10N on 2011-07-02
Those ppa may not longer be available since openoffice turned into libreoffice.

---

### Post by Bucky Ball on 2011-07-02
Open Office turned into LibreOffice??? Since when? Got a link?

---

### Post by colio on 2011-07-03
> **Bucky Ball said:**
> Have you recently upgraded to a newer release? These items are in your sources list (rather than Synaptics). Open update manager then 'Settings' in the bottom left corner and that will show you your software sources. In the second tab (third party or something like that) you should find that source.

You can disable that source and that will fix your issue for now but then Open Office will not be updated.

That fixed it, thanks so much for the help-

---

