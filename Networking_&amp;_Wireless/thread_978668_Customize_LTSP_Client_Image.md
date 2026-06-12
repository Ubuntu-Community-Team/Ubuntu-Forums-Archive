---
title: "Customize LTSP Client Image"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by saythein on 2008-11-11
Sorry if this is in the wrong section. I am using Edubuntu as a classroom server and I have LTSP setup and it is working. But my client image seems to be an exact mirror of my servers desktop. How can I customize the menus in the client image without modifying the menus on my server? Thank you all in advance for your help.

---

### Post by wirelessben on 2009-01-19
One simple way is to use the kiosk option of ltsp-build-client.

In a terminal window, run "sudo ltsp-build-client --kiosk"

This will give the user a Firefox browser and nothing more. No login screen either.

To write LTSP plugins, go to [https://wiki.edubuntu.org/HowtoWriteLTSP5Plugins]("https://wiki.edubuntu.org/HowtoWriteLTSP5Plugins")

---

