---
title: "Desktop Entry and this error."
date: 2009-03-11
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-03-11
There was an error creating the child process for this terminal

I got this while trying to run my desktop entry and then I tried to validate this and got this.

root@eric:/# desktop-file-validate '/home/eric/Desktop/Download' 
/home/eric/Desktop/Download: error: filename does not have a .desktop extension
root@eric:/# desktop-file-validate '/home/eric/Desktop/Download' 
/home/eric/Desktop/Download: warning: key "Encoding" in group "Desktop Entry" is deprecated
/home/eric/Desktop/Download: error: value ";" for key "MimeType" in group "Desktop Entry" contains value "" which does not look like a MIME type
/home/eric/Desktop/Download: error: filename does not have a .desktop extension


any ideas?

---

### Post by stanz on 2009-03-11
Is Download a folder or file?

I would say, do not include any quotes..and the dot needs to precede the filename:
> # desktop-file-validate /home/eric/Desktop/[COLOR=Red].[/COLOR]Download

---

### Post by ericeclifford on 2009-03-11
Ty man I got this solved, there was a problem with the actual filename wasnt showing up as desktop for some odd reason because of a previous file it was reading it as.

---

