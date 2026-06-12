---
title: "auto highlight all of text in search box?"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by nachos99 on 2009-02-28
when i click on the search box in the right top corner of firefox, whatever text was all ready in the box doesnt get highlighted. i have to manually delete or highlight and then type in the new search.

is there a way to set it so that when i click inside the search box, text will all be highlighted.
this applies to the url box as well.  

thanks for any suggestions.

---

### Post by Zill on 2009-02-28
Not sure if this is what you are after but if you double-click in these boxes, rather than single-click, this highlights the contents.

---

### Post by kaibob on 2009-02-28
Change the following Firefox about:config setting to true:

```
browser.urlbar.clickSelectsAll
```

If you are not familiar with about:config settings, let us know.

---

### Post by nachos99 on 2009-02-28
thanks for the tips.

first, im unfamiliar with about:settings. more info would be great if that's all right.

second, the double clicking works fine for one word, but if i have several words, the double clicking seems to just highlight the single word you click on.

---

### Post by Xiong Chiamiov on 2009-02-28
Triple-click.

---

### Post by kaibob on 2009-02-28
> **nachos99 said:**
> ...first, im unfamiliar with about:settings. more info would be great if that's all right....

Do the following:

1) Start Firefox and type about:config in the address bar then press Enter. 

2) After Filter: type clickselectsall.

3) Double-click on the word browser.urlbar.clickSelectsAll. This will change the value from false to true.

4) Exit then start Firefox and you're done.

I have included a screenshot below.

---

### Post by nachos99 on 2009-03-02
hello kaibob,

thank you for the explanation.

---

### Post by bilbs84 on 2012-10-11
This was annoying me too, i changed the address bar issue, but was still annoyed with the search bar behavior, however, i found an acceptable solution.
[https://addons.mozilla.org/en-us/firefox/addon/clear-search-2/](https://addons.mozilla.org/en-us/firefox/addon/clear-search-2/)
this addon will clear the search bar with every search, so its always empty when you click into it, hope this help you as much as it did me :)

---

