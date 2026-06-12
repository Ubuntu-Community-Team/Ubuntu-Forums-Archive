---
title: "Mobile broadband via USB only works if inserted at computer startup, why?"
date: 2014-07-18
forum: Networking &amp; Wireless
---

### Post by Jan_Jansson on 2014-07-18
I had trouble setting up my mobile internet. I am using a USB dongle. I pressed "Edit connections" and filled in ISP, APn etc but could not connect.
Then I tried via the Network manager and now at least the "Enable mobile broadband" was shown and so waas the connection but still no internet.

This morning I started the computer and had left the dongle in the computer and it worked! I tried disconnecting the dongle and connecting again but then I had no contact again. So I restarted the computer with the dongle in it again and it worked.
So my USB mobile broadband only works if I start the computer with the dongle connected. So I guess some routine is just run at startup and then never again?

Here is some basic info:

Info:
OS: Ubuntu 14.04 LTS
ISP: Comviq
Device: Mobile internet USB dongel. Only supported for Windows and maybe MAC, not Linux.
APN: data.comviq.se

What more do you need?

What can I do to fic this problem? Add some script? I don't know what happens now if I loose connection, if it auto reconnects or if I have to restart the computer.

---

### Post by grahammechanical on 2014-07-18
Do you have the connection set up to automatically connect? If you do then that is what will happen as Ubuntu loads. But it cannot happen if the device is not attached at the time Ubuntu is loaded because the Nework Manager scrips have all ready been run.

You can try this. Open the Network Manager icon menu and disable Networking and then enable it again. That will trigger Network Manager into doing its stuff. It will detect the existence of the device and run its connection scripts.

Regards.

---

