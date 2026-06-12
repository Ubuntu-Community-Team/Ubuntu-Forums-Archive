---
title: "Printer producing blank pages"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by bwallum on 2011-04-08
I have suddenly found an HP Deskjet 845C printer, connected by usb, which worked fine a couple of weeks ago now produces a blank page. The printer appears to be making all the right physical movements as though it was printing but absolutely nothing comes out on the page, not even a broken line that normally indicates ink depletion.

The printer should work 'perfectly'
[http://www.openprinting.org/printer/HP/HP-DeskJet_845C](http://www.openprinting.org/printer/HP/HP-DeskJet_845C)

hplip is installed and the inks are full (ish). A test page can be produced but is completely blank.

Has anybody experienced similar issues? If so are there any fixes?

---

### Post by Paddy Landau on 2011-04-08
> **bwallum said:**
> A test page can be produced but is completely blank.
Do you mean that when you ask the printer via its control panel to print a test, the result is a blank page? If so, it's nothing to do with the computer settings, but a fault with the printer. How sure are you that the ink cartridges are full?

---

### Post by bwallum on 2011-04-09
Using 'Printer properties' and clicking on the print test page button produces an entirely blank sheet. Printing a text file makes the printer go through the motions one would expect for the text file, line by line, exact number of lines, eject at end of text etc but only produces a blank sheet.

I am currently working on the assumption that the printer driver is out of date following a distribution upgrade from Lucid to Maverick. The driver is hplip so when I next get to the machine using that printer I will try the latest hplip.

When ink cartridges fail on this machine it is a decline in quality mode, not an over the cliff mode such as working one day and then, (after the upgrade,) not working the next.

Upgrading hplip seems like a test I should do anyway and hope to report back soon.

Thanks for the response, keep 'em coming if you have any more insight please.

---

### Post by jim Kane on 2011-04-09
> **bwallum said:**
> I have suddenly found an HP Deskjet 845C printer, connected by usb, which worked fine a couple of weeks ago now produces a blank page. The printer appears to be making all the right physical movements as though it was printing but absolutely nothing comes out on the page, not even a broken line that normally indicates ink depletion.
hplip is installed and the inks are full (ish). A test page can be produced but is completely blank.

Has anybody experienced similar issues? If so are there any fixes?

What happens if you ask the printer to print a self text page
i.e not from the pc but from printer buttons i think from memory it's hold paper button and press X button.

jimK

---

