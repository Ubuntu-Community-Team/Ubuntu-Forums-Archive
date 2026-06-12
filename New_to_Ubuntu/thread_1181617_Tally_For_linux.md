---
title: "Tally For linux"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-06-08
Is there any software like tally for linux , Or can i use tally in wine.Will it work properly

---

### Post by ad_267 on 2009-06-08
What is Tally? A link to the website would be helpful.

---

### Post by ravi_buz on 2009-06-08
Tally is an Indian Accounting software 
here is its website
[http://tallysolutions.com/newwebsite/html/index.html](http://tallysolutions.com/newwebsite/html/index.html)

---

### Post by Mornedhel on 2009-06-08
Hello,

Tally will not work under Wine : [http://appdb.winehq.org/objectManager.php?sClass=application&iId=6321](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6321)

Compatibility is rated Garbage, the lowest compatibility software can get under Wine.

If you need to run an ERP under Linux, a quick search brought up openerp-client and openerp-server. If it's for a business, chances are you're better off staying with Windows.

---

### Post by mikechant on 2009-06-08
If you look at the detailed test results under Wine, there are three things to note:
a) Although the application has a rating of 'garbage' it appears to run OK in some sort of unlicensed 'demo' mode.
b) The only problem identified (which is obviously a serious one) is that the license related code fails. 
c) Wine has gone through a number of releases since this test was done.

So *if* the license code works under the latest version of Wine, it looks like there is a reasonable chance the application could work acceptably. In other words, it might be worth a try.

Otherwise, running Tally under a VM could be a good idea if this is the only windows software you need.

---

### Post by ravi_buz on 2009-06-08
Thanks For your help :D,

---

### Post by Sir Jasper on 2009-06-08
Hi,

It would seem toTally inappropriate to run the program via Wine unless this has already been tried and tested.

Any data corruption or malfunction could have major consequences in terms of difficulty, time and expense in reconstruction/re-input of data.

Can you not have the best of both worlds (Linux and Windows) with  dual boot or perhaps separate dedicated computers?

My regards

---

