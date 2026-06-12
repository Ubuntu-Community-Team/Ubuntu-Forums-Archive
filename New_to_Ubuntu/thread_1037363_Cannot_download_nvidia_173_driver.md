---
title: "Cannot download nvidia 173 driver"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by rojodojo on 2009-01-11
Hello,
I've recently upgraded my laptop from Xubuntu 8.04 to 8.10. However, the hardware driver will not download, and subsequently not install. The driver required for my graphics is the Nvidia v173 driver. I've tried downloading for the 'Hardware Drivers' in the menu as well as the synaptic packages manager.
Is there an alternate way that I could download and install the appropriate drivers?

---

### Post by avtolle on 2009-01-11
Said driver is not shown under System-->Administration-->Hardware Drivers?

---

### Post by jimmy the saint on 2009-01-11
This happened to me.  Open up synaptic (system>administration>"synaptic package manager" and under settings, select repositories.  Where it says "Download from" click the dropdown box and select "other..."

Click the Select Best Server button.

When it has completed the scan click the "choose server" button and close that dialog.  In synaptic, press the "Reload" button then try to get the drivers again.

Sometimes the servers get overwhelmed or are having issues and the driver cannot be downloaded.  This tests all the available mirrors for the best one available at the moment.

---

