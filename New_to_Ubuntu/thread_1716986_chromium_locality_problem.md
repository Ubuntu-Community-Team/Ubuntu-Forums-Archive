---
title: "chromium locality problem"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by trbone on 2011-03-29
Hi guys.

Whenever I run a search in chromium by just typing the search query into the address bar it defaults to using google.co.th to answer it! 

This is happening currently with lubuntu, but it was also happening with ubuntu netbook edition on the same computer on a previous install...

I have tried going into preferences and changing the google default search page that way, but this didn't change anything. In the preferences/manage search engines box the google address is listed as google.com, but still whenever I do a search it gives me the results in Thai! This is very frustrating!

Oh yea. When I first installed ubuntu (and chromium) I was in Thailand, which I guess led to this problem... But I'm not there any more!

---

### Post by rburkartjo on 2011-03-29
trb have you tried clicking on the wrech icon on the rightside of the tool bar,the preferences, then change the default search to whatever

---

### Post by jtarin on 2011-03-29
1. kill 'google-chrome' or 'chromium' (whichever you are using): '$ pkill chrome' or '$ pkill chromium'
2. Navigate to this directory (this is relevant to Ubuntu/Kubuntu distros): '$ cd ~/.config/google-chrome/' or '$ cd ~/.config/chromium/'
3. Open the file 'Local State' in vim or your preferred plain text editor: '$ vim Local\ State'
4. Search for the strings 'last_known_google_url' and 'last_prompted_google_url' adn replace their values to your preferred Google base URL, which in my case was google.com (as I am in Russia and it defaults to .ru) and I had a hard time to set as default following the previous suggestions.
5. Save the file and exit
6. Should do the trick.

---

### Post by computerandu on 2011-03-29
Go in to the Preferences -> Basics -> Search -> Manage Search Engines -> Set the default value to Google.com/ncr

---

### Post by jtarin on 2011-03-29
> **computerandu said:**
> Go in to the Preferences -> Basics -> Search -> Manage Search Engines -> Set the default value to Google.com/ncrIf I'm not mistaken that only works for that session.:confused:

---

### Post by trbone on 2011-04-03
Thanks Jtarin. That worked a treat! :)

---

### Post by jtarin on 2011-04-03
Your welcome! Might mark the thread as solved.

---

