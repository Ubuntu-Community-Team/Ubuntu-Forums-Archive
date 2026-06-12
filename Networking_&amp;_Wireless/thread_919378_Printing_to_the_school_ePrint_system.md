---
title: "Printing to the school ePrint system"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by kenixkil on 2008-09-13
Hi, I'm a newbie to Ubuntu (have been using it for about a month) and I was just wondering how to send print commands to our school's ePrint server. They provide programs for Windows and Macs, but unfortunately only some instructions for Linux which I seem unable to implement. Here are the instruction they give:

add a new printer on your workstation with the following settings:

    * Queue type: choose LPR/LPD/Networked Unix
    * Server: [Server name]
    * Server-side queue name: ePrint-OIT
    * Workstation-side queue name: selected by user (OIT recommends ePrint-OIT)
    * Printer type: Use HP LaserJet 4100dtn (or closest equivalent)

When you send print jobs from your personal Unix or Linux system, you need to include your NetID as a parameter to the lpr printing command &#8211; both from the GUI and from the command line. To do so, add the -U flag followed by your username.

For example, to print foo.txt from the command line on your Linux system, a user with the NetID of john would enter lpr -P ePrint-OIT -U john foo.txt.

Thanks in advance!

Edit: I installed some package called ePrints 3 for Debian/Ubuntu, and I'm also wondering if the package is relevant to this issue? Thanks.

---

### Post by todreich on 2011-02-22
You might want to try these instructions:

[https://www.dunk.duke.edu/rkm/viewdoc.jsp?doc=4656&sid=303546&type=Published&terms=quick_searchTerms&user=Self](https://www.dunk.duke.edu/rkm/viewdoc.jsp?doc=4656&sid=303546&type=Published&terms=quick_searchTerms&user=Self) Help

Let me know if they work for you.

If the link fails go to [https://www.dunk.duke.edu/rkm/home.jsp?user=Self%20Help](https://www.dunk.duke.edu/rkm/home.jsp?user=Self%20Help) and search for article 4656

Thanks! :)

---

