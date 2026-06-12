---
title: "open hardcoded intanet links to Windows network shares including &quot;\&quot; back slashes"
date: 2015-08-18
forum: Networking &amp; Wireless
---

### Post by will79 on 2015-08-18
I think this is more related to the OS than the internet browsers.  But I have a couple Ubuntu computers on a Windows network.  They access an INTRAnet page that has thousands of links directly to the local file shares located on Windows network.  

Accessing from ubuntu's version of explorer works fine, it accesses windows network paths (\\server\folder\) I believe because fusesmb is installed.  

But the issue is when clicking on the links on the intranet, the coded links on the intranet page look like this file://server/folder/file.pdf but Ubuntu reads it like File:///\server\folder\file.pdf and so it goes nowhere.  Windows computers open the links just fine.  

I don't know where to start for the issue.  I have tried using an addon called filesystem links for mozilla firefox but it does not work.  

Perhaps if there is a way for Ubuntu to covert those backslashes to forward slashes?  

Open to any suggestions.

---

