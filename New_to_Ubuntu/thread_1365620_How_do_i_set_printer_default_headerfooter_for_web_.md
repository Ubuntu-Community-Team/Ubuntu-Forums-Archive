---
title: "How do i set printer default header/footer for web pages?"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by entropy1 on 2009-12-27
When I print a web page, the dialog box has an Options tab with a section called "Header and Footer".  The default has the title in the upper left, the URL in the upper right, Page # of # in the lower left, and the Date/Time in the lower right.  How do I change these defaults, for example, to make them all blank?

---

### Post by gsmanners on 2009-12-27
Sadly, Firefox doesn't have that in the Page Setup (where it should be) in Linux just yet. Instead, you need to go to the "about:config" page in Firefox and put "print_head" and "print_foot" into the filter and change the following preferences:

print.printer_PostScript/default.print_headerleft
print.printer_PostScript/default.print_headerright
print.printer_PostScript/default.print_footerleft
print.printer_PostScript/default.print_footerright

---

### Post by entropy1 on 2009-12-27
gsmanners,

Thank you for the tip.

There were several print.printer_headerxxx and print.printer_footerxxx entries.  After changing several of them,
I got what I wanted.

---

