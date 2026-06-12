---
title: "Firefox Bug"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by txwooley on 2009-01-19
My Firefox 3 suddenly went nuts.  When I open it it goes to a blank page.  the refresh, back and forward buttons don't work, and I have no home page even though settings says I do (Firefox goes to Firefox/Google page whenI click home icon).  I have seen many posts with this exact problem and quite a few suggested solutions.  I have completely uninstalled Firefox and deleted the Firefox folder from /usr/lib.  I then re-installed using synaptic package manager.  I re-installed sqlite and sqlite3, checked for updates for sqlite.  Still no fix.  Firefox reports the following errors:

Error: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: file:///usr/lib/firefox-3.0.5/components/nsBrowserGlue.js :: bg__initPlaces :: line 449"  data: no]
Source File: file:///usr/lib/firefox-3.0.5/components/nsBrowserGlue.js
Line: 449

Error: uncaught exception: [Exception... "Component returned failure code: 0x8007000e (NS_ERROR_OUT_OF_MEMORY) [nsIDocShellHistory.useGlobalHistory]"  nsresult: "0x8007000e (NS_ERROR_OUT_OF_MEMORY)"  location: "JS frame :: chrome://browser/content/browser.js :: prepareForStartup :: line 763"  data: no]

I don't want to switch to Netscape, but I can't bookmark anything or open pages in a new window.  Please help!

---

### Post by txwooley on 2009-01-19
Anyone?

---

### Post by txwooley on 2009-01-20
Not a lot of help here, but I did find the solution in case anyone else has similar problems.  I read where someone else with the exact same problem ran Firefox as root and the problemd were gone.  I did the same and now everything works just like it did before!  Now it works fine just clicking on the quick-launch icon!  I still don't know what caused the problem, but running as root seems to be the solution.

---

### Post by blueridgedog on 2009-01-20
Well done...I was watching the thread, but had no suggestion.

---

