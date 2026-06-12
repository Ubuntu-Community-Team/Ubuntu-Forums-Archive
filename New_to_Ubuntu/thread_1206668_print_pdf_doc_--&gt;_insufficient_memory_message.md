---
title: "print pdf doc --&gt; insufficient memory message"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by knomaly on 2009-07-07
Printer: hp business inkjet 2300 w. 64MB memory
 OS: Ubuntu 9.04; 7GB linux swap space
 Example PDF document properties: File size: 140KB; 14 pages, primarily text
 PDF Viewer: Document Viewer 2.26.1
 

 Objective: Print PDF document. All pages. Use standard "Ctrl + P > Enter" key combination or File > Print menu options
 

 Issue: PDF print job will not print. "Insufficient Memory" message displayed on printer's LCD interface. Document can be printed, but printing must be segmented / broken into parts.  
 

 Note: This is a new issue; i.e., I have never previously had trouble printing out PDF docs of any reasonable length using Ubuntu 9.04.

---

### Post by pizza-is-good on 2009-07-07
I would start by uninstalling the printer, reseting it (That has to be in your printer manual), then intalling again...
 
Good luck.

---

### Post by LowSky on 2009-07-07
why not try a different program like acrobat?

its in the medibuntu repos

---

### Post by knomaly on 2009-07-07
Turned printer off. Removed non-system memory. 
Turned printer on. Ran PDF doc print test. Doc printed. 
Problem resolved: corrupt memory module.

---

### Post by LewRockwell on 2009-07-07
> **knomaly said:**
> Turned printer off. Removed non-system memory. 
Turned printer on. Ran PDF doc print test. Doc printed. 
Problem resolved: corrupt memory module.

if you wanted to you might just plug and unplug the memory a dozen times or so

while unlikely, it is theoretically possible that your failure might be the result of poor connections

.

---

