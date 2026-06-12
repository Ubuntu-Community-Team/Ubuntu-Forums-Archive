---
title: "ftp or http?"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by Wake Rider on 2008-02-29
When selecting a mirror for linux download files, is it better to select an http or a ftp server?:confused:

---

### Post by Mr. C. on 2008-02-29
Each has pros and cons.  Pick what works best for you for that mirror.  Some FTP servers have resumable downloads, so if the download fails, and the FTP client allows resumption, you can pick up where you left off.

FTP has been around for ages, and was the de-facto standard for file transfer.  But its command set is simplistic and rudamentary.

With the advent of the web as most know it today, FTP required users to enter ftp:// vs. http:// which they are more accustomed to.  Early on, there was a lot of confusion about file types of downloaded data, and how the browser should deal with the data.  As HTTP and browsers matured, downloads via HTTP have become well behaved, but it wasn't always so.

There is additional meta-data that can accompany the transfer in HTTP, and this allows some browser conveniences.

Pick the one that works best in your case, for your client.

---

