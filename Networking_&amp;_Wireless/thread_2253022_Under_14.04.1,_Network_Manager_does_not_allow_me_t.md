---
title: "Under 14.04.1, Network Manager does not allow me to save a &quot;Manual&quot; IP entry"
date: 2014-11-16
forum: Networking &amp; Wireless
---

### Post by cpbl on 2014-11-16
I've installed the latest 14.04.5 distribution, which strangely then told me to "Upgrade to 14.04" which involved downloading over a GB of stuff all over again ... but that is not my issue (I'm saying it only to try to identify what distribution I'm using):

When I try to add a "Manual" IPv4 entry into my network manager, as I always have done, the "Save" button becomes grayed out as soon as I choose "Manual" rather than DHCP.

If with all of the information correctly filled in, that save button stays grayed out and I eventually have to Cancel all my work.
 I cannot get my static-IP set up.

---

### Post by praseodym on 2014-11-16
Try starting it via
```

gksudo nm-connection-editor
```

---

### Post by luisa2 on 2015-04-10
I had the same problem under Ubuntu 14.04.2 LTS and solved it.

Try to do the following. 
When you add the first "Manual" IPv4 entry, then do not use the TAB key to move to the second entry: use instead the mouse 
to move the cursor into the appropriate box. The same holds for the following entries.
When all the information will be filled in, the "Save" button will no longer be grayed out and you will be able to save your 
static-IP set up.

---

### Post by prashant-kocherlakota7 on 2015-06-11
I have the same issue and I'm running Ubuntu Gnome 14.04.2. Is this a problem with Gnome? I had Unity until (4-5 days ago) it crashed and my network manager didn't present me with this issue. Things that don't work:

1. gksudo nm-connection-editor doesn't work.
2. Not making new additions to the list of static IPs under 'Manual' in IPv4.
3. Not using tab.
4. Not using enter after finishing typing out the details.
5. The save option remains grayed out even when I enter the right details.

I also tried using Wicd, but I couldn't get it to work properly.

Should I reinstall Unity on my laptop? I think it's just a network manager issue because DHCP and Automatic and all other options work just fine.

---

### Post by chili555 on 2015-06-11
Did you enter a static IP address, netmask, gateway *AND* DNS servers? If you set a static IP address, you are responsible for all of these details and Network Manager will not allow you to save a configuration that is incomplete and will not work.


[http://i.imgur.com/Sqh8P.png](http://i.imgur.com/Sqh8P.png)

---

