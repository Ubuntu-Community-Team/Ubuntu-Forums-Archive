---
title: "xsane scanning"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by expatCM on 2010-07-05
I am scanning an A4 color photograph to tiff at 600dpi using xsane.  The main panel in xsane indicates that this will result in a file of about 95.6MB.  The result is a file of about 3.2MB

All settings left as default except the dpi and the tiff format.

That seems a bit odd.  Does anyone know what is wrong?

---

### Post by mike2357 on 2010-07-05
I don't think there is anything wrong with your settings or anything you've done.  Whenever I've scanned in any type of document using xsane, the estimated size is always a good bit larger than what the actual size ends up being.  I always assumed it was just an error in the algorithm the program uses to estimate file sizes.

---

### Post by expatCM on 2010-07-06
Ok ...  found this .....  it is in the settings.

The default settings provide for compression which is a pity.  I would have been inclined to have made the default without compression and then let the user select.

If you go to Preferences / Setup / File Type and then select No Compression, the scanned image is the same size as indicated in the program window.

---

### Post by mike2357 on 2010-07-06
Thanks, that's good to know.  Mystery solved!

---

