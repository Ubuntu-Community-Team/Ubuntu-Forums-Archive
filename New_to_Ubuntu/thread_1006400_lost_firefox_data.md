---
title: "lost firefox data"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by Benbow on 2008-12-09
After yesterdays update (Intrepid), I closed down my pc. This morning I restarted as usual and found that my entire Firefox data, bookmarks, saved tabs, had gone. This is the first time I have had this problem after an update, is there any way of getting my data back?
It is also impossible to use firefox as the bookmark function does not work in fact the whole of firefox seems to be unusable. The rest of my programmes seem to be ok.

---

### Post by hyper_ch on 2008-12-09
> **Benbow said:**
> is there any way of getting my data back?
Restore it from your backups.

---

### Post by Malta paul on 2008-12-09
Firefox keeps it data in your home directory under a hidden directory.
Press Ctl + H to obtain the hidden directory's and files.
check:  home/.mozilla/ you will find a directory named by some letters and numbers and also a file called profiles.ini
check to see if you have two directory's and check their date using your mouse, right click and select properties.
Back up the profiles.ini file and also make a copy. Now with a text editor change the profile number to the number of your of your oldest directory. Restart Firefox it will then use the new profile. 
Hope you can make this out? :cool:

---

### Post by Benbow on 2008-12-09
Firefox has ceased to function. I have tried reinstalling, did not work then uninstalling and reinstalling but no luck. As I mentioned earlier this is since I updated last night. Can anyone help?

Iam getting the following error plus a stack of others (too many to post)

Error: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: file:///usr/lib/firefox-3.0.4/components/nsBrowserGlue.js :: bg__initPlaces :: line 465"  data: no]
Source File: file:///usr/lib/firefox-3.0.4/components/nsBrowserGlue.js
Line: 465

---

### Post by lilas1024 on 2009-01-14
I had the same issue as Benbow, except firefox still functions. It just lost my bookmarks and saved passwords. When I tried Ctrl-H as you said, it only opened internet history. Can you help me? If I can locate the previous profile info that would save me a lot of rebookmarking. Especially since some of the bookmarks I don't know the addresses for.

---

