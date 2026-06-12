---
title: "firefox woes"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by mwv on 2009-01-30
My mozilla firefox will only boot properly in the terminal.  If I click on the icon, or the shortcut on the panel it will bring up a mozilla window, but it will not go to my homepage and it will not load my bookmarks. Also, it will not perform let me click on any buttons (i.e. "search" on Google, or "Sign In" in Gmail.  Java problem maybe? )  I have checked the permissions of the .mozilla folder, as well as the firefox and firefox-3.0, and it made no difference what they were set to.

I would like it to run normally from the panel or shortcut, without having to boot from the terminal everytime.

Here is what comes up in my error box if I run Firefox from the panel:

First Error:

Error: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: file:///usr/lib/firefox-3.0.5/components/nsBrowserGlue.js :: bg__initPlaces :: line 449"  data: no]
Source File: file:///usr/lib/firefox-3.0.5/components/nsBrowserGlue.js
Line: 449

Second Error:

Error: uncaught exception: [Exception... "Component returned failure code: 0x8007000e (NS_ERROR_OUT_OF_MEMORY) [nsIDocShellHistory.useGlobalHistory]"  nsresult: "0x8007000e (NS_ERROR_OUT_OF_MEMORY)"  location: "JS frame :: chrome://browser/content/browser.js :: prepareForStartup :: line 763"  data: no]


Sorry, I am new to Linux.  I tried searching but I could not find anything that would fix this problem.

---

### Post by Branimir on 2009-01-30
Increase your swap file or by more memory, or free some memory
whatever.

Greetsa, Branimir.

---

### Post by buffy^ on 2009-01-30
Have you updated firefox but not updated the shortcut with in the menue to reflect this?

I am KDE users and so gnome is not my strong point.

---

### Post by mwv on 2009-01-30
> **Branimir said:**
> Increase your swap file or by more memory, or free some memory
whatever.

Greetsa, Branimir.

I have plenty of free memory.  I my swap is decently sized and I have yet to dip into it.  

> **buffy^ said:**
> Have you updated firefox but not updated the shortcut with in the menue to reflect this?

I am KDE users and so gnome is not my strong point.

I will look into it but I am pretty sure that is not the case.  It shouldn't matter because in the panel shortcuts you just set them to execute firefox.  

I have also tried reinstalling several times.

---

### Post by timcredible on 2009-01-30
i just checked the properties on mine, you might want to make sure yours is set the same.

---

### Post by mwv on 2009-01-30
> **timcredible said:**
> i just checked the properties on mine, you might want to make sure yours is set the same.

That is what mine looks like.  I am getting sooo frustrated.

---

### Post by harshpkaria on 2009-01-30
Go to Browse, and navigate to /usr/bin/ and search "firefox - 3.0" That is the executable if u are using firefox 3.0 and above, otherwise the "firefox" only.... Also, firefox uses plenty of memory. 256MB and above is considerable according to me. Do the above settings, and close the thread if the problem is solved.

---

### Post by ugm6hr on 2009-01-30
Post your command and what happens when launched from Terminal.

Then try Alt+F2 and type the same command as you have been using in Terminal and tell us what happens.

---

### Post by mwv on 2009-02-01
> **ugm6hr said:**
> Post your command and what happens when launched from Terminal.

Then try Alt+F2 and type the same command as you have been using in Terminal and tell us what happens.


Ok, here is what happens when I run it from the Applications menu, the icon in the panel, and when I ran it in alt-f2.

[IMG]http://i43.tinypic.com/9fs49e.jpg[/IMG]

Here is what happens if I run "sudo firefox"

[IMG]http://i42.tinypic.com/qmyzw9.jpg[/IMG]

sorry for the late responses guys.

---

### Post by ugm6hr on 2009-02-01
Looks like "root" has a firefox profile, but there is a problem with yours.

I'd suggest just deleting your profile and starting again:
```
rm -rf ~/.mozilla
```

---

### Post by mwv on 2009-02-01
> **ugm6hr said:**
> Looks like "root" has a firefox profile, but there is a problem with yours.

I'd suggest just deleting your profile and starting again:
```
rm -rf ~/.mozilla
```

That worked.  I have to reset my homepage and stuff, but other than that it is great.  

Luckily I use Foxmarks, because I had no clue it would delete my bookmarks.

Thank you very much.

Matt

---

### Post by ugm6hr on 2009-02-01
> **mwv said:**
> Luckily I use Foxmarks, because I had no clue it would delete my bookmarks.

Sorry - should have explicitly warned you about that!

Glad there was no disaster :)

---

### Post by mwv on 2009-02-01
> **ugm6hr said:**
> Sorry - should have explicitly warned you about that!

Glad there was no disaster :)

No worries!

Now I just have to learn how to network my linux and windows machines.  :popcorn:

Matt

---

