---
title: "update mgr doesnt?"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by stevek123 on 2010-08-04
I am running a fresh install of 9.10. I installed all the updates except for several that didnt go thru. Now it gives me an open Update Mgr _every day_ with several items that dont install. This is irritating also because I have the UpMgr set to notify Every 2 Weeks! not every day.
 
 FWIW, Firefox Stuff is not updating
"Changes for the versions:
3.5.3+build1+nobinonly-0ubuntu6
3.6.7+build2+nobinonly-0ubuntu0.9.10.1

Version 3.6.7+build2+nobinonly-0ubuntu0.9.10.1: ..."

Error Msgs are these..
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-3.5-gnome-support_3.6.7+build2+nobinonly-0ubuntu0.9.10.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-3.5-gnome-support_3.6.7+build2+nobinonly-0ubuntu0.9.10.1_all.deb)
  404  Not Found [IP: 91.189.88.37 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-gnome-support_3.6.7+build2+nobinonly-0ubuntu0.9.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-gnome-support_3.6.7+build2+nobinonly-0ubuntu0.9.10.1_i386.deb)
  404  Not Found [IP: 91.189.88.37 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-3.5-branding_3.6.7+build2+nobinonly-0ubuntu0.9.10.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-3.5-branding_3.6.7+build2+nobinonly-0ubuntu0.9.10.1_all.deb)
  404  Not Found [IP: 91.189.88.37 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-branding_3.6.7+build2+nobinonly-0ubuntu0.9.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-branding_3.6.7+build2+nobinonly-0ubuntu0.9.10.1_i386.deb)
  404  Not Found [IP: 91.189.88.37 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-3.5_3.6.7+build2+nobinonly-0ubuntu0.9.10.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-3.5_3.6.7+build2+nobinonly-0ubuntu0.9.10.1_all.deb)
  404  Not Found [IP: 91.189.88.37 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox_3.6.7+build2+nobinonly-0ubuntu0.9.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox_3.6.7+build2+nobinonly-0ubuntu0.9.10.1_i386.deb)
  404  Not Found [IP: 91.189.88.37 80]

If they are not available why does my Mgr still want them???

---

### Post by cariboo on 2010-08-07
Try a different mirror. Go to System->Administration->Software Sources, Clicj the Download From drop down, and select a different server.

---

### Post by stevek123 on 2010-08-16
Switched from USA server to main server -> problem solved.
Thank you

---

