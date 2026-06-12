---
title: "error connecting"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by grado on 2006-10-21
Hi,

I am unable to connect to any service other than those on port 80 and the https port. My ISP is not blocking these connections. Is there anything on my machine that could be preventing this connection from happening?

I am new to ubuntu/linux. Pls help.

Thanks!

---

### Post by handy on 2006-10-21
So web browsing is ok, but the Repositories, Gaim, Automatix download, & the like are not?

Find out what your ISP's DNS IP addresses are (there are usually 2).  If you don't know them, you should be able to find them by looking into your router/modem's firmware via a web browser.  You will need to know the router's IP address to put it in the browser's address field.  You will also need a (usually the default for the hardware) username & password to access the firmware.

Failing that you should be able to find the DNS's on the ISP's website, documentation or by directly contacting them.

Once you know what these addresses are, go to ***Menu:* System / Administration / Networking -  *DNS Tab***

Check the number(s) against your known correct DNS.  I suspect that you will have the router's address in there & not the DNS addresses that are required to do any more than browse the web.

If your DNS number's are incorrect, or if they are correct but the router's address is first in the list? 

Then I suggest that you go to the pretty simple walk through ***[Edit:]*** [I made a more straight forward one here.]("http://ubuntuforums.org/showthread.php?t=282034")

Let us know how you go... :)

Of course all the above is useless if you are on dialup!!! :confused:

---

