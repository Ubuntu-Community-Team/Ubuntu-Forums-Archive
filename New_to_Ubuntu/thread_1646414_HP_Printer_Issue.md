---
title: "HP Printer Issue"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by Thelasko on 2010-12-15
My HP 950C no longer prints text. When I try to print a text document, I get a blank page. I believe this is due to a recent update to the hplip driver, as it worked before the update.

The printer works fine in Windows, so it's not a hardware issue.

I'm including a test page I printed.  Notice how the word "Ubuntu" is missing from the top.

---

### Post by Thelasko on 2010-12-15
I've been trying to revert back to the previous driver, but synaptic won't let me.

---

### Post by sydbat on 2010-12-15
Have you tried going to the [HPlip site]("http://hplipopensource.com/hplip-web/index.html") and getting the most recent drivers?

---

### Post by Thelasko on 2010-12-16
> **sydbat said:**
> Have you tried going to the [HPlip site]("http://hplipopensource.com/hplip-web/index.html") and getting the most recent drivers?

No, it's in a run format, which worries me for some reason.

---

### Post by sydbat on 2010-12-16
> **Thelasko said:**
> No, it's in a run format, which worries me for some reason.Nothing to worry about. I always get the latest HP drivers for my printers from there and never had a problem. They have a bang on installation guide there too.

---

### Post by Thelasko on 2010-12-21
The installation guide doesn't seem to be there.  The installer requested a bunch of dependencies and then said it couldn't connect to install them.

---

### Post by khelben1979 on 2010-12-22
Have you tried to print pages using different software? Just in case the bug is in that software and not in the HP driver.

---

### Post by Thelasko on 2010-12-22
After examining some of the printouts that were performed on my wife's Windows machine, I noticed that text was not true black. Apparently, something in Windows tells the printer to print black text with the color cartridge when the black ink runs out. Linux doesn't do this, hence the odd behavior.

I've replaced the black cartridge, and now everything works fine!

---

