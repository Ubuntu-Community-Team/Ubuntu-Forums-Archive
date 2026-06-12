---
title: "Displaying IE pages"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by nayeret43 on 2009-01-03
What do I do when I need to display internet pages which can only be displayed using Internet Explorer?  

I know of a IE plugin for Firefox, but it is not available for Linux (which is very ironic in my opinion).

So, how do I solve this problem?? What should I do?

---

### Post by Farmer of Bricks on 2009-01-03
Th IE plugin just opens a new tabwith IE running inside the tab, displaying the page. If the site isn't essential, you might try finding a replacement site that offers the same services. If you *have* to use the page, try installing IE in WINE or complaining to that website's webmaster.

---

### Post by bump_ on 2009-01-03
Download the user agent switcher

```
https://addons.mozilla.org/en-US/firefox/addon/59
```

Download the xml import file (right click-> save link as)

```
http://techpatterns.com/forums/about304.html
```

In firefox, go to Tools->User Agent Switcher->Options->Options

Click Import and import the xml file. You can now change what websites see you broswer and operating system as. Just go to Tools->User Agent Switcher and choose an IE from the list and all should be well.

Edit: I just tested it on update.microsoft.com and it works fine.

---

### Post by binbash on 2009-01-03
you should use a browser agent switcher addon like mentioned above.

---

### Post by nayeret43 on 2009-01-03
> **bump_ said:**
> Download the user agent switcher

```
https://addons.mozilla.org/en-US/firefox/addon/59
```

Download the xml import file (right click-> save link as)

```
http://techpatterns.com/forums/about304.html
```

In firefox, go to Tools->User Agent Switcher->Options->Options

Click Import and import the xml file. You can now change what websites see you broswer and operating system as. Just go to Tools->User Agent Switcher and choose an IE from the list and all should be well.

Edit: I just tested it on update.microsoft.com and it works fine.

I did what you said, all those options showed up, and I first chose the IE 7 (Windows Vista) option, which didn't work, and then I tried the MSIE 6 (Win XP) option, which didn't work either.

There are two types of Internet Explorer pages I need to see:
1. Pages that just look and run better in IE
2. Pages that **require** Internet Explorer to run (such as my college library page).

What should I do now that the previous option didn't work?  Or, is it a possibility that I configured it wrong?

---

### Post by HotShotDJ on 2009-01-03
> **nayeret43 said:**
> What should I do now that the previous option didn't work? Give this a try: [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by bump_ on 2009-01-03
Thats odd. I am using linux and firefox and it let me on IE only sites fine with the user agent switcher. 

Try going to [http://whatsmyuseragent.com/](http://whatsmyuseragent.com/) to make sure it changed. It should look something like

Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0)

for IE7 on Vista.

---

### Post by bpalone on 2009-01-03
Another option is to install a virtual machine running a Windows version of your choice.  Of course you have to have the Windows CDs to install it.  I have two sites that I have to use ie6 or above on and my solution is to use the virtual machine.  I just tried the agent switcher and got further on one than I could before, but it failed in the end.

That is the best I can offer for a suggestion.  You should probably complain to the sites, but it will probably fall on deaf ears.

---

