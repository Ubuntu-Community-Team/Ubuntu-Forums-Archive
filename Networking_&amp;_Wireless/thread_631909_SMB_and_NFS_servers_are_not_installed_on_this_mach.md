---
title: "SMB and NFS servers are not installed on this machine"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by Trebacz on 2007-12-04
Brand new install of Gutsy Kubuntu 7.10 64 bit version. When I go to to configure Samba shares under systems I get:

Under File Sharing "SMB and NFS servers are not installed on this machine, to enable this module the servers must be reinstalled"

A message also says that changes in this section requires root access. Click on the "Administrator Mode" button to allow modifications.

Unfortunately this button is grayed out.

On this same hardware it worked perfectly from the live CD. After the install of a disk version -I can't see the rest of my network.

I've used Samba previously for Windows sharing with no problems. Suggestions?

---

### Post by Trebacz on 2007-12-04
I found a fix but I'm still not sure why I had to use it.

Do the following on the machine that has the files to be shared:

Install Samba

sudo apt-get install samba

On my installation 1 new package was installed -even though Adept reported it as fully installed before.

Add current user to Samba:

sudo smbpasswd username

(replacing username with your login username)

After this process I could configure Samba through the standard KDE K Menu>System Settings>File Sharing -now I could enter my password.

---

