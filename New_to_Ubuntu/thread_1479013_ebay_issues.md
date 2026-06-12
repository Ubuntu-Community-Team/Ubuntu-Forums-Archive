---
title: "ebay issues"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by cosmic ted on 2010-05-10
Hi guys sorry if someone has posted this already but .since the last update I cannot log into my ebay or paypal A/cs, all ok on internet explorer on my other PC though.
As you can gather I dont Know alot about Ubuntu.Its all of a mystery!!!! to me.:confused:
Has anybody had the same probs.
Thanks.

---

### Post by Sealbhach on 2010-05-10
What sort of error messages are you getting from those websites?

.

---

### Post by cosmic ted on 2010-05-10
Not sure It takes ages to load up and then a message appers Ebay ISAP (5 ).dll and sometimes ( 4 ).dll.

---

### Post by Sealbhach on 2010-05-10
OK, a suggestion. Remove the cookies you have got from those sites.

In Firefox, select from the menu Edit/Preferences, hit the Privacy tab and in the middle of the dialog box you will see some blue writing. Click on remove individual cookies, put "ebay" in the search box and remove all the Ebay cookies.

When you go back to Ebay you will have to log in again.

.

---

### Post by cosmic ted on 2010-05-10
Hi. did that,done this, still nada.the task bar is not loading at all.
Downloads box appears with  EbayISAPI(8).dll

---

### Post by crjackson on 2010-05-10
Wow, this seems strange.  I have 12 machines and run an ebay business on them.  All of the machines use Ubuntu / Firefox.  I've never encountered anything like this.

---

### Post by cosmic ted on 2010-05-10
Thanks for your replies, but no fixes yet. Ive been trying to to solve the prob myself but have a very limited understanding of the linux file system.
Would it be better to start from scratch.? 
What I can remember, the 2 updates that I installed on Saturday where called xrunner or similar to that,but not entirely sure.
Help!!!

---

### Post by Sealbhach on 2010-05-10
Right, xulrunner is something that works with your browser, as far as I know. I would suggest to uninstall xulrunner and Firefox, also remove the .mozilla folder in your home folder.

Then reinstall Firefox and see if it's fixed. If you have loads of Bookmarks you want to back up, you can use the Xmarks add-on to do that.

.

---

### Post by cosmic ted on 2010-05-10
Cheers............I'll try that in the morning.
Will let you know how i get on.
Thanks.

---

### Post by crjackson on 2010-05-10
What version of Ubuntu are you using?

What browser version are you using?

Did you get your firefox updates from an added repository, or the standard (default) Ubuntu repositories?

---

### Post by cosmic ted on 2010-05-11
Just dowloaded 3.6.3 still no joy.As stated i know F/A about this system,will this auto upgrade the browser or do I need to do something,also downloaded Opera,how do I intall it on my desktop??
I cant find the update or file for this xulrunner to delete it still.Oh and can I restyore system also,
Will this restore to before updates.
Cheers.

---

### Post by cosmic ted on 2010-05-11
Hi, as stated I know FA, just dowloaded 3.6.3 still no joy will thjis auto ugrage the browser or do I need to initialize it.Also downloaded Opera how do I intall onto desktop,Cant find file for this xulrunner either so still stumpped.,and would a system restore be of any use to to restore before the last update.how to do this also.
Sorry for all the questions but it is really blind leading the blind.
Cheers.

---

### Post by gandaran on 2010-05-11
did you remove (backup first) the .mozilla folder from you hidden home directory? then restart firefox, a new firefox profile is created, it should fix the problem, no need for reinstalls.
to install opera if you have the .deb file just double click it and hit the install button.

---

### Post by cosmic ted on 2010-05-11
Can anybody guide me through this.!!!!
Thanks.

---

### Post by gandaran on 2010-05-11
> **cosmic ted said:**
> Can anybody guide me through this.!!!!
Thanks.
exactly what?
if you reinstall firefox if won't fix the problem if you still have your old firefox profile, you have to create a new one, so first answer the question did you remove the .mozilla folder from the hidden home user directory?

---

### Post by cosmic ted on 2010-05-11
No,how to do.
Thanks.

---

### Post by gandaran on 2010-05-11
open your home user folder, on the menu bar go to view > show hidden files then scroll down to .mozilla and rename it to something else now launch firefox, you should have a brand new firefox profile now, check if it works on ebay now.

---

### Post by cosmic ted on 2010-05-11
Still no joy,  should i get rid of xulrunner?

---

### Post by gandaran on 2010-05-11
> **cosmic ted said:**
> Still no joy,  should i get rid of xulrunner?

no, you cant remove it, only reinstall it! 
 
another question, have you been using firefox as root or are you running a root ubuntu system, well since removing your user .mozilla profile didn't work it leads me to believe you have or somehow you have modified the root firefox profile, if this is the case you'll have a hard time fixing this as reinstalling firefox won't remove the modified files.

---

### Post by cosmic ted on 2010-05-11
Hi, i did as instructed, I get your point.but as stated this ony occured after the update,prior to this fine.Anyway I'll Have a fiddle when not to busy as this is eating my day up.
Thanks foor the advise.
Cheers.

---

### Post by Sealbhach on 2010-05-11
To install Opera, just select Ubuntu from the [Download Page]("http://www.opera.com/browser/download/") here.

You will  have downloaded a .deb file, you just double-click it, enter your password and it installs. Much the same process as with Windows.

.

---

### Post by cosmic ted on 2010-05-12
Well.....! I've given up for now.I'm thinking of dumping ubuntu alltogether and going back to windows, no body seems to know what my problem is and anyone local just takes a big sidestep with this issue.
But anyway thanks for your advice on this and will post if I find a fix.

---

