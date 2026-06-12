---
title: "How to use wget to download a web page with not the default value"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by say2sky on 2009-08-25
Using wget, it is easy to download web page or even a web site
but it is all the default content on the downloaded page.
Now some web page can show different content through dropdown list.

my question is:
How I can download by using wget the undefault content which show when user select different value in dropdown list on web page. thanks!

---

### Post by say2sky on 2009-08-25
Your help is important to me. 
Any suggestion or idea are greatly appreciated.

---

### Post by amac777 on 2009-08-25
I guess you'd need to research the web site in particular to find out how the menu system works. Do the drop down menus go to other url pages? If yes, then you can use wget to download the other urls instead of the main page. But if the menu works using flash or some other method, you might have to do more research.

But the first step is to understand how the dropdown list works.

---

### Post by say2sky on 2009-08-26
> **amac777 said:**
> I guess you'd need to research the web site in particular to find out how the menu system works. Do the drop down menus go to other url pages? If yes, then you can use wget to download the other urls instead of the main page. But if the menu works using flash or some other method, you might have to do more research.

But the first step is to understand how the dropdown list works.

thanks a lot for your info.

what I want to is that dropdown list selection by user will not change the address of this web page showing in browser's address bar. ie it is not related with a new address, if yes I know user can have wget + new address.

here is something use to change selection value used in web page
```
<select name='applicationId' onchange="reloadStatistics(this, 22, 'itemFamilyId')" size='1'><option value='1'>item1</option><option value='2'>item2</option><option value='3'>item3</option><option value='4'>item4</option><option value='5'>item5</option><option value='6'>item6</option><option value='7'selected='selected'>item7</option><option value='8'>item8</option><option value='9'>item9</option><option value='10'>item10</option></select>
```

total 10 item, now item 7 is selected. 
But that any item is selected the web page will have same address in browser's address bar but show some different content.

---

### Post by say2sky on 2009-08-26
More suggestion is needed.

Please give your idea. Thanks a lot.

---

### Post by brunogirin on 2009-08-26
From the code you posted above, the page you want to download uses AJAX to update its content, which makes it very difficult to reproduce with wget because wget is a non-interactive tool whereas AJAX is designed to be used with an interactive front-end. To understand what the page is doing, you need to understand what the javascript function reloadStatistics does. It probably dynamically fetches data from a different URL than the main page's one and inserts the result inside that main page, which is why the URL in the browser doesn't change even if the data changes.

To find out what's happening, you'll have to check the <script> tags that are in the page and if those reference external javascript, you'll need to have a look at those javascript files and find the reloadStatistics method.

---

### Post by say2sky on 2009-08-26
> **brunogirin said:**
> From the code you posted above, the page you want to download uses AJAX to update its content, which makes it very difficult to reproduce with wget because wget is a non-interactive tool whereas AJAX is designed to be used with an interactive front-end. To understand what the page is doing, you need to understand what the javascript function reloadStatistics does. It probably dynamically fetches data from a different URL than the main page's one and inserts the result inside that main page, which is why the URL in the browser doesn't change even if the data changes.

To find out what's happening, you'll have to check the <script> tags that are in the page and if those reference external javascript, you'll need to have a look at those javascript files and find the reloadStatistics method.
Your info is very helpful, it indeed is AJAX
Now I found
```

<script language="javascript" type="text/javascript" src="/js/aforms.js"></script>
<script type="text/javascript" src="/js/btype.js"></script>
<script type="text/javascript" src="/js/ajaxtags-1.2.js"></script>	

```

But I am not sure if these xxx.js files under /js/ directory is open for user to access.
I will try.

any web tool other than wget is suitable for get this kind of web data?  curl will be better or not?

---

### Post by brunogirin on 2009-08-26
So the function you are looking for should be in one of those 3 files. curl won't help because it is a non-interactive tool like wget and is not able to run javascript.

In practice, what you need is an automated tool that understands and runs javascript and can simulate user interaction. You could try using the iMacros extension for Firefox: [https://addons.mozilla.org/en-US/firefox/addon/3863](https://addons.mozilla.org/en-US/firefox/addon/3863)

---

### Post by say2sky on 2009-08-26
> **brunogirin said:**
> So the function you are looking for should be in one of those 3 files. curl won't help because it is a non-interactive tool like wget and is not able to run javascript.

In practice, what you need is an automated tool that understands and runs javascript and can simulate user interaction. You could try using the iMacros extension for Firefox: [https://addons.mozilla.org/en-US/firefox/addon/3863](https://addons.mozilla.org/en-US/firefox/addon/3863)
Great! Thank you very much.

I will try it. 
is it possible for firefox be run in background to download needed webpage?  I have check the command line option for firefox. Not so many.

---

