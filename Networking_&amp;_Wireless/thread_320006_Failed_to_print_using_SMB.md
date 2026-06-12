---
title: "Failed to print using SMB"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by alex1973 on 2006-12-16
I have ubuntu 6.10 on my laptop. I am trying to print to a network printer Konica Minolta Di1611 using SMB. I have installed the drivers on both, a Win2003 and a WinXPpro system. I've also installed "Print services for unix".
I have tried all Generic printers and Raw. For some of them, like PCL6, the request gets to Windows (I can see the jobs in the list for a few seconds) but it does not reach the printer. I could not find any errors in Windows or in Ubuntu. I find it strange that in the job list, on Windows side, on the "Pages" columns, it specifies "N/A" while the size varies between 1 and 2 MB.

Thanks for your help.

---

### Post by alex1973 on 2007-02-27
I have found a workaround. It seems like a generic approach to windows printers (GDI). The drawback is that you need a Windows system in your network.
The idea is to create a virtual Postscript printer in Windows which is a bridge between the linux client and the actual printer:
linux (with generic postscript driver) -> virtual printer on windows (postscript driver to ghostscript using Redirection Port Monitor) -> printer using manufacturer's driver on windows  -> actual printer (without linux support :( )

I have followed the instructions at [http://www.stat.tamu.edu/~henrik/GSPSprinter/GSPSprinter.html](http://www.stat.tamu.edu/~henrik/GSPSprinter/GSPSprinter.html) and [http://iharder.sourceforge.net/current/macosx/winmacprinter/#step1](http://iharder.sourceforge.net/current/macosx/winmacprinter/#step1)

Make sure to enable spooling in the virtual printer on windows.


Good luck.

---

