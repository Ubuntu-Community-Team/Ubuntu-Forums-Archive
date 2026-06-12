---
title: "Clearning History in Unbuntu Firefox"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by Bluespoet on 2009-05-21
I have the latest versions of  Unbuntu and Firefox. I have gone to tools like when I use firefox in windows and cleared the history, but it still pops up in the address line, then I went to edit and changed my preferences. I have a website that I need to delete from the address saving of websites, but all the history is still there . I tried removing firefox thinking I could reinstall it, so I download Chrome as a browser and went to the add remove and remove firefox, but now it is still there, still with history and uses Mozilla as a home page.
I love Unbuntu and downloaded the free guide, but short of deleting Ubuntu and doing a format on my hard drive and a reinstall. I cannot kill the history in Firefox
Help

---

### Post by taurus on 2009-05-21
How about just deleting ~/.mozilla instead of reinstalling Ubuntu?

---

### Post by eeeandrew on 2009-05-21
In firefox click tools->clear private data

If this doesn't work. Go to your home folder, click "show hidden files and folders" in the view menu. find the folder labelled .mozilla and then delete the enclosed folder called "firefox" this will clear all personal settings permanently.

Hope this helps,
Andrew

---

### Post by mprince on 2009-05-21
> **Bluespoet said:**
> when I use firefox in windows and cleared the history, but it still pops up in the address line, then I went to edit and changed my preferences. I have a website that I need to delete from the address saving of websites, but all the history is still there

If you just want to remove one address.

Go up to the address bar... Highlight the address you want to get rid of and press **Shift+Delete**

---

### Post by Bluespoet on 2009-05-22
clearning private data doesnt do anything, it goes thru the typical firefox routine, but the info remains and ctr delete doesnt accomplish anything as well.

---

### Post by Bluespoet on 2009-05-22
> **mprince said:**
> If you just want to remove one address.

Go up to the address bar... Highlight the address you want to get rid of and press **Shift+Delete**

I have tried all the suggestions made so far, I have Chromium browser to use. None of them have worked for me. I have deleted the firefox folder, found home places in Places and done the shift delete, tried control delete and alt delete and so far Firefox is still working and not deleting my history. I have gone into firefox tools and deleted history, but nothing works in unbuntu yet. I hope I dont have to delete unbuntu and re install, but will try anything to get history cleared

---

### Post by Celauran on 2009-05-22
> **taurus said:**
> How about just deleting ~/.mozilla instead of reinstalling Ubuntu?

This works.

---

### Post by eeeandrew on 2009-05-22
Ok, lets confirm your private data settings are set correctly and try again. Although I don't see why deleting the settings folder didn't work...

In firefox go to edit->preferences->privacy tab. At the bottom of the tab is the private data settings. so click the settings button and check everything. Then accept those changes and back in the privacy tab click the "clear now" button. 

If this fails, I suggest you try to delete the .mozilla folder from your home directory as taurus suggested. To do this go to your home folder, press ctrl+h to view hidden files and folders. Find the folder .mozilla and delete it. Then empty the trash. You can press ctrl+h again to hide the folders if you wish.

Hope this helps,
Andrew

---

### Post by Niniel on 2009-05-22
Could you be dealing with 2 different versions of FF? As in FF2 and FF3?

---

### Post by luvinit on 2009-05-22
I can't remember exactly but I think if you set 

browser.urlbar.maxRichResults;-1

in advanced settings i.e. enter "about:config" as a url in the browser address bar, it might be what you are looking for.

---

### Post by Niniel on 2009-05-22
Oh, something else - I think whatever bookmarks you have also appear in the address box. That has nothing to do with history and is a feature, not a bug.

---

### Post by mprince on 2009-05-22
[I]Edit>Preferences>Privacy tab
[/I]
'Keep my history for at least 0 Days' 

Set it to zero days, and then exit firefox. That is another way you can delete the history.

---

### Post by richg on 2009-05-22
I posted this question here some months ago. Here was the reply someone sent me.

From what I can tell it is not a real bug but a regression that's
part of a new feature RichResults. The browsing history does
not erase RichResults anymore. If you don't want RichResults
keep track of where you went, in Firefox you need to enter
about:config
and then scroll down to:
browser.urlbar.maxRichResults
and change the default. The default setting is 12 and if you
want nothing, you enter 0.

This works for Ubuntu and Mint. It also works for my stepson who use Firefox with Vista Basic.

Rich

---

