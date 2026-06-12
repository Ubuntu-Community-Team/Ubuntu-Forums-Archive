---
title: "Re: Webdav failure to sharepoint"
date: 2016-06-01
forum: Networking &amp; Wireless
---

### Post by ben-fluidlogic on 2016-06-01
Hi - 
I know this thread is a year old, but I thought it'd be worth adding some additional info. We're a shop with a mix of Windows, Mac and Linux clients. We use Office365. I'm running 64-bit Xubuntu Wily 15.10. Here's what my attempt to connect to Sharepoint using davfs looks like:

```
 $  **sudo mount -t davfs -o ro https://obfuscatedcorpname.sharepoint.com/sites/foo/dev/ /home/ben/Sharepoint**
Please enter the username to authenticate with server
https://obfuscatedcorpname.sharepoint.com/sites/foo/dev/ or hit enter for none.
  Username: ben@obfuscatedcorpname.com
Please enter the password to authenticate user ben@obfuscatedcorpname.com with server
https://obfuscatedcorpname.sharepoint.com/sites/foo/dev/ or hit enter for none.
  Password:  
/sbin/mount.davfs: Mounting failed.
403 FORBIDDEN

```

---

