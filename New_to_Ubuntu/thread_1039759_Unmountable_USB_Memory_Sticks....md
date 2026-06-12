---
title: "Unmountable USB Memory Sticks..."
date: 2009-01-14
forum: New to Ubuntu
---

### Post by uk_freelancer on 2009-01-14
Hi,

A few days ago I installed Ubuntu 8.10 for the first time on my pc and encountered a number of problems, one of which was that Ubuntu would not mount my 4GB USB memory stick.

To cut a long story short...

The 'problem' in my case was that it was last used in Windows (vista in this case) and while you can plug and unplug the memory stick all day long in Windows and still be read correctly the next time you use it this is not the case in Ubuntu.

Sometimes when Windows closes it doesnt manage to complete all its housekeeping tasks and while it may 'appear' to close down normally, this isnt always the case. If you have, as have, a USB Memory stick, windows will sometimes forget to mark the USB device as 'closed', but which it will still be able to access the next time its booted up.

However, in Ubuntu and probably in other versions of Linux the OS checks to see what 'state' the memory stick is in, i.e whether it is closed or open. If the memory stick was last used in Windows and it didn't correctly close the memory stick then Ubuntu wont be able to mount it, even if you use Terminal to try and forceably mount it. 

So if you suddenly find your USB Memory Stick being unmountable in Ubuntu and its been used on a PC running Windows (perhaps you have a duel boot system as I have), chances are, you need to fire up Windows and use Safely Remove device in order to set it back to closed again. I have tested this twice now and both times have worked. 

Had I known about this from the start it could have saved me many hours of searching the web for possible answers and spending some time in Terminal trying out different mount commands trying to access my memory stick.  

Hope this is of use to someone :-)

---

