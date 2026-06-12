---
title: "Firefox drives my friend to lunacy"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by abrianb on 2010-04-18
I recently convinced a friend of mine to remove windows and install Ubuntu. He says that Ubuntu is faster, less buggy, he likes Gnomes clean desktop. It would seem to be love at first boot, but no. A quirk in firefox drives him crazy. What is it that makes a life of shuffling along to the thorazine beat or worse yet reverting to windows seem likely? When he uses the back button, firefox does not return to the same place he had previously scrolled to. I don't know how to turn this function on. It just started doing it on its own on my machines. I know that very old versions of firefox did not have this feature. Firefox added it years ago. He has the latest greatest firefox. I tried reinstalling firefox but it did not work. Can anyone tell me how to turn this feature on?

---

### Post by Gone fishing on 2010-04-18
I know this doesn't answer the question, but there is Google Chrome.

---

### Post by coffeecat on 2010-04-18
> **abrianb said:**
> Can anyone tell me how to turn this feature on?

Yes. 

It's turned on by default in the Windows version of Firefox, but off in the Linux version. Which is #**&#%# ridiculous! :wink:

Type 'about:config' in the address bar. OK the nonsense that comes up next and then type 'back' in the filter. Look for the line 'browser.backspace_action' and change the numerical value to zero. Restart Firefox. Use backspace key to your heart's content.

> **abrianb said:**
> It just started doing it on its own on my machines.

Hmmm. Are you sure? :p

---

### Post by lovinglinux on 2010-04-18
> **coffeecat said:**
> Yes. 

It's turned on by default in the Windows version of Firefox, but off in the Linux version. Which is #**&#%# ridiculous! :wink:

Type 'about:config' in the address bar. OK the nonsense that comes up next and then type 'back' in the filter. Look for the line 'browser.backspace_action' and change the numerical value to zero. Restart Firefox. Use backspace key to your heart's content.

For more info about the above recommendation and other options see [http://kb.mozillazine.org/Browser.backspace_action](http://kb.mozillazine.org/Browser.backspace_action)

> **coffeecat said:**
> Hmmm. Are you sure? :p

If the buttons suddenly doesn't do anything, then it could be [this problem/solution](http://lovinglinux.megabyet.net/?page_id=220#Back-and-forward-buttons-are-greyed-out-or-doesn%27t-work-2).

---

### Post by abrianb on 2010-04-18
Thanks for the responses so far. The problem is not with the "Backspace key" on the keyboard. The problem is with the "Go back one page" Button on the firefox browsers upper left corner. It goes back one page, it just does not return to the same place he had scrolled to when he was last on the page. To demonstrate, google something, scroll to the middle of the page and click the link. Once the link has opened click the "go back one page button". Firefox takes me back to the middle of the google search page. Firefox takes my friend to the [COLOR=Red]TOP [COLOR=Black]of the google search page. How do I make his Firefox work like mine?[/COLOR][/COLOR]

---

### Post by lovinglinux on 2010-04-18
> **abrianb said:**
> Thanks for the responses so far. The problem is not with the "Backspace key" on the keyboard. The problem is with the "Go back one page" Button on the firefox browsers upper left corner. It goes back one page, it just does not return to the same place he had scrolled to when he was last on the page. To demonstrate, google something, scroll to the middle of the page and click the link. Once the link has opened click the "go back one page button". Firefox takes me back to the middle of the google search page. Firefox takes my friend to the [COLOR=Red]TOP [COLOR=Black]of the google search page. How do I make his Firefox work like mine?[/COLOR][/COLOR]

Do what cofeecat suggested. Firefox comes with value 2 for that setting by default. Changing to 0 will allow you to go back to same page scrolling location.

---

### Post by shae on 2010-04-18
That is working properly for me.  You should check to see if you changed something by renaming your mozilla profile and trying it with a clean one.

```
mv ~/.mozilla ~/.mozilla-backup
```

---

### Post by lovinglinux on 2010-04-18
> **shae said:**
> That is working properly for me.  You should check to see if you changed something by renaming your mozilla profile and trying it with a clean one.

```
mv ~/.mozilla ~/.mozilla-backup
```

That is extreme for this situation. Just need to change the setting suggested by cofeecat.

BTW, you don't need to change the ~/.mozilla folder, since Firefox profiles are stored under ~/.mozilla/firefox.

---

### Post by abrianb on 2010-04-18
I tried setting the value to 1,2,3,4,5 it had no effect on the "go back one page" button in the upper left hand corner of firefox. It does change the behavior of the backspace button on my keyboard.

---

### Post by lovinglinux on 2010-04-18
> **abrianb said:**
> I tried setting the value to 1,2,3,4,5 it had no effect on the "go back one page" button in the upper left hand corner of firefox. It does change the behavior of the backspace button on my keyboard.

It's 0, not 1 or 2 or 3...

---

### Post by prenoob on 2010-04-18
I do strongly recommend coffeecat's solution.

Trevor (long time Firefox user)

---

### Post by lovinglinux on 2010-04-18
I think something is wrong indeed. I was able to change the behavior once, but now it always go to the scrolled location, no matter which value I use for that setting.

---

### Post by abrianb on 2010-04-18
Sorry I tried 0 as well . I checked Mozilla out for a definition of the function of "browser.backspace_action" it is all about the backspace button on the keyboard. not clicking on the browsers back one page button/arrow. When I changed the integer to 0 it changed how my backspace key function as a keyboard shortcut. My problem is with using a mouse to click on the go back one page button in the upper left of the firefox browser.

---

### Post by roger_1960 on 2010-04-18
Hi

The "back one page" works as it should ie going to the right place on the previous page with the browser.backspace value set to 0, 1 or 2.  This does not seem to be the right setting - it just affects the backspace button behaviour.  Must be something else!

---

### Post by barney385 on 2010-04-18
> **coffeecat said:**
> Yes. 

It's turned on by default in the Windows version of Firefox, but off in the Linux version. Which is #**&#%# ridiculous! :wink:

Type 'about:config' in the address bar. OK the nonsense that comes up next and then type 'back' in the filter. Look for the line 'browser.backspace_action' and change the numerical value to zero. Restart Firefox. Use backspace key to your heart's content.



Hmmm. Are you sure? :p

That's weird. On mine, the value is set at 2 and it works fine...?

:popcorn:

---

### Post by -humanaut- on 2010-04-18
simple solution sudo apt-get install chromium-browser && sudo apt-get install epiphany

Epiphany is Gecko based just like firefox I think it has the sane defaults your looking for and chromium is good to have.

---

### Post by barney385 on 2010-04-18
> **abrianb said:**
> Thanks for the responses so far. The problem is not with the "Backspace key" on the keyboard. The problem is with the "Go back one page" Button on the firefox browsers upper left corner. It goes back one page, it just does not return to the same place he had scrolled to when he was last on the page. To demonstrate, google something, scroll to the middle of the page and click the link. Once the link has opened click the "go back one page button". Firefox takes me back to the middle of the google search page. Firefox takes my friend to the [COLOR=Red]TOP [COLOR=Black]of the google search page. How do I make his Firefox work like mine?[/COLOR][/COLOR]

Mine works fine on default...


Might be a local issue...

---

### Post by abrianb on 2010-04-18
bump

---

### Post by barney385 on 2010-04-18
> **abrianb said:**
> I recently convinced a friend of mine to remove windows and install Ubuntu. He says that Ubuntu is faster, less buggy, he likes Gnomes clean desktop. It would seem to be love at first boot, but no. A quirk in firefox drives him crazy. What is it that makes a life of shuffling along to the thorazine beat or worse yet reverting to windows seem likely? When he uses the back button, firefox does not return to the same place he had previously scrolled to. I don't know how to turn this function on. It just started doing it on its own on my machines. I know that very old versions of firefox did not have this feature. Firefox added it years ago. He has the latest greatest firefox. I tried reinstalling firefox but it did not work. Can anyone tell me how to turn this feature on?

Obviously it's not the backspace issue. After installing did your friend update firefox?

Has he updated anything?

---

### Post by abrianb on 2010-04-18
He has updated.

---

### Post by takisan on 2010-04-18
> **Gone fishing said:**
> I know this doesn't answer the question, but there is Google Chrome.
NO! FIREFOX IS THE MOST AWESOME BROWSER EVER! However, I have no problem using Firefox. I've used a bunch of other browsers and see no reason for your friend to be driven to lunacy over it.

---

### Post by J V on 2010-04-18
Have you tried the suggested deleting firefox config files?

---

### Post by abrianb on 2010-04-18
I have not tried deleting config files. What is done to replace them?

---

### Post by MattTastic on 2010-04-18
Hey guys, thanks for the suggestion, I hadn't given it much thought as to why firefox didn't go back to a certain point on a page, but now that I changed the setting it does.

Cool beans.

---

### Post by barney385 on 2010-04-18
> **MattTastic said:**
> Hey guys, thanks for the suggestion, I hadn't given it much thought as to why firefox didn't go back to a certain point on a page, but now that I changed the setting it does.

Cool beans.

Uhmmm...what exactly did you change?

---

### Post by J V on 2010-04-18
> **abrianb said:**
> I have not tried deleting config files. What is done to replace them?Firefox will make brand new config files next time it is started up, just delete them (Or rename them if you want a backup) and viola, fresh settings. That should fix any problems you are having: You might want to export your bookmarks first though...

---

### Post by barnaclebill18 on 2010-04-18
This issue used to bother me, also.

The way I got around it was to use the add-on Tab Mix Plus, and set it to open links in a new tab, that way when I go back, I am always where I left  from.

Instead of using the back button, I either close the current tab or click on the tab I want to go back to.

---

### Post by MattTastic on 2010-04-18
> **barney385 said:**
> Uhmmm...what exactly did you change?

Just did what coffeecat suggest way back on post #3

---

### Post by senorian on 2010-04-23
I posted this in "general help" but, if allowed, would like to repost here as , in my case,it seems that my problems are caused by a recent update. I have made no changes on my own to Ubuntu 9.10


A couple of days ago the home/end keys, the page up and down keys, the arrow up and down keys all stopped or became erratic
I thought that it was my old keyboard, so I bought a new one--same problems
.
So I loaded DSL as a live cd and now all keys work

(Iam typing this on the live cd)
One of the recent Ubuntu 9.10 updates may have borked something).
I hope they fix it soon
senorian is offline   	Reply With Quote

---

