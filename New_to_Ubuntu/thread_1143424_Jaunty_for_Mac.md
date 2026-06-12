---
title: "Jaunty for Mac"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Kale Good on 2009-04-29
Looking for some clarification on Ubuntu and PowerPC. Specifically, I would like to update to Jaunty but can't find a download. I understand that powerpc is no longer a supported architecture, does that mean that it will take the community some time to get around to making a powerpc version (or that they might not get around to it)?

Part of my confusion stems from the fact that I installed the release candidate of Jaunty on my powerpc. I ended up deleting it and going back to Intrepid for reasons I can't remember. Why could I install the release candidate but not the actual release?

note: there is a possibility that the update was only partial. Everything visual appeared to be jaunty-ized.

---

### Post by fdrake on 2009-04-29
1.

      Install update-manager-core if it is not already installed:

      ```
sudo apt-get install update-manager-core
```

   2.

      Launch the upgrade tool:

     ```
 sudo do-release-upgrade
```

   3. Follow the on-screen instructions.

---

### Post by llamabr on 2009-04-29
Though ppc is no longer supported, there's community support.

Instead, I installed debian lenny on my ibook.  No complaints, as the setup recognized my screen resolution, configured x, and even saw my airport card.

---

