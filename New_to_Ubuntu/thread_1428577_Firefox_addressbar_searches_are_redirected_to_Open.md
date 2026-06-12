---
title: "Firefox addressbar searches are redirected to OpenDNS"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by _sphinx_ on 2010-03-13
Can I make some changes so that if I make some search through the address bar in firefox (for example: "ubuntu wiki"), it provide me the page of google search or the "I am feeling lucky" page from the google, like it used to do before?

---

### Post by tshrinivasan on 2010-03-13
To change the Firefox option is very simple, as follows:-

   1. At Firefox address bar, enter about:config and press ENTER.
   2. At Filter: field, type keyword.url
   3. You should see a Preference name of keyword.URL in the list. Double click it, a “Enter String Value” input box will appear.
   4. Replace the string with:
      [http://www.google.com.my/search?q=](http://www.google.com.my/search?q=)
      Click “OK” button and done!

from
[http://www.liewcf.com/archives/2005/01/modify-firefox-address-bar-search/](http://www.liewcf.com/archives/2005/01/modify-firefox-address-bar-search/)

---

### Post by lovinglinux on 2010-03-13
[http://www.labnol.org/software/browsers/prevent-opendns-google-redirects-firefox-address-bar-ie/2662/](http://www.labnol.org/software/browsers/prevent-opendns-google-redirects-firefox-address-bar-ie/2662/)

---

### Post by _sphinx_ on 2010-03-13
Thanks for your help folks. It worked. Closing the thread.

---

### Post by aeronutt on 2011-03-27
Thanks!! (For the fix for opendns search problem)

---

