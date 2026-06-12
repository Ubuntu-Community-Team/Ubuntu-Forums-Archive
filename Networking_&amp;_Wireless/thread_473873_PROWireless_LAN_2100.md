---
title: "PRO/Wireless LAN 2100"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by Woody@N87 on 2007-06-14
I'm trying to get a HP tablet computer up and running on a wireless internet connection and I'm having some trouble.  First of all I tried the gui interface, the wireless connection is grayed out and doesn't respond when clicked on.

I've searched the other posts for sometime and it appears that the installed card is supported without using the NDISWrapper(s) I've read about;

```
lspci  
02:05.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04) 
```

but the card seems to be turned off or something....
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:off   
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:

sudo iwlist eth1 scan
No Scan results
```

  Any ideas what the next step would be?

---

### Post by jtp51 on 2007-06-15
I am having the same issue with the exact Network controller - Intel Corp. PRO/Wireless LAN 2100 3B Mini PCI Adapter.

Did you find a solution?

Thanks,

---

### Post by Woody@N87 on 2007-06-15
Not yet, you're the only responder so far and i haven't found anything on my own yet.:confused:

---

### Post by Woody@N87 on 2007-07-04
Just in case anyone was following this, the issue it seems that the problem is the method that the tablet uses to turn the wireless card on and off.  It is apparently a little unusual.  The options it seem are to either download a linux patch and re-compile your linux kernal (I may have said this incorrectly but you get the idea) way over my head.

The other option, that I went for and it worked perfectly, was to re-load Windows XP tablet edition then load ubuntu leaving only about 7 gig for the Windows partition.  After completely loaded I opened windows and turned the card on with the "Q" menu, I then re-booted into ubuntu and the card worked perfectly as advertised on other forums.  No NDIS wrapper needed.  I now have a 50 gig ubuntu tablet working great and also have the small windows partition should I need it for something.

  now if I could only get this battery to charge correctly.......

    Good luck with your tablet.
          Mike

---

