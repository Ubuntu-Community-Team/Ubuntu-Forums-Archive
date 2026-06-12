---
title: "Using Backspace-Button to go one page back"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by Just-me on 2009-11-06
Hi Guys  another simple question about my newly installed 9.1 In my previus system it was possible in the Firefox webbrowser to use the backspace button to go back to the previus page. As I can do if I browse through my folders and files. I still use the firefox but in this Ubuntu version I can't do this anymore. But for me it would be great to use this key for supporting my browsing.  Any idea how to switch this on?  Thanks for help!

---

### Post by Byrd740 on 2009-11-06
I don't know about pressing backspace, but you can press Alt+Left/Alt+Right to go Left/Right, respectively.

---

### Post by dasunst3r on 2009-11-06
1. Open up Firefox, and go to about:config
2. Promise to be careful
3. Set browser.backspace_action to 0

Also, if you dislike double-clicking on the URL bar to select all items, you can set browser.urlbar.clickSelectsAll to true (as opposed to false).

---

### Post by Just-me on 2009-11-06
great, i just found it:  about:config  browser.backspace_action  I set the value to zero and everything works fine.   Thanks for help

---

