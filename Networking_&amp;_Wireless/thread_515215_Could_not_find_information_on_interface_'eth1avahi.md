---
title: "Could not find information on interface 'eth1:avahi' in /proc/net/dev"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by mseeba on 2007-08-01
Today I was trying to configure my wireless interface at a hotel using the standard task bar icon that is included with Feisty. Out of the blue the signal strength bar disappeared from the bar and when I click I get:
Could not find information on interface 'eth1:avahi' in /proc/net/dev

I cannot configure my wireless at all now. It is totally broken. I can get to it through System / Administration / Network but any updates done here seem to just be ignored by the system. I am down. Help! 

thanks!

-Mark.

---

### Post by lucky7 on 2007-08-02
I also had this problem, in my case the error message completely prevented me from doing anything with that app, so I edited the file /proc/net/dev, just copying and pasting the line for eth1 and changing the interface name to eth1:avahi.  I think after that I was at least able to use the app.  Warning: I don't really no what I'm doing though so that solution might not be completely safe.

---

### Post by kevdog on 2007-08-02
Anything with the avihi extension is not an error.  This only comes up when you are not connected, its not causing your problems, its a symptom.  Once you get connected back to the internet it will go away.  Id look at how you are connecting, configuration, driver, etc.

---

### Post by ubunutgoz on 2008-01-06
That last piece of advice was spot-on, thanks.  

All you have to do is <right-click> on the n etwork icon in the top panel, select **Properties** and then either add a new connection, or reselect a previous one that was working.

I encountered this whilst travelling and thought that I would have a lot of trouble finding a file that I had somehow accidentally erased... not so.

I do think that this aspect of the user-interface is a bit lacking.  OSX and WinXP do seem more intuitive.

Anyway, thanks for the post and giving me just a little more knowledge than I had before!

Alan

---

### Post by NotoriousMOK on 2008-01-29
thanks ubuntugoz and kevdog -- i got this error fiddling around with my wireless and you got me back in shape -- thanks again

---

