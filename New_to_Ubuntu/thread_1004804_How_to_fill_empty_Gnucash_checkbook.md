---
title: "How to fill empty Gnucash checkbook???"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Pappy1911 on 2008-12-07
I exported MSMoney into a .qif file.
Then imported into Gnucash.
All my entry's show up in Accounting as a list, but, I can't get them into the check register.

I've set up the checkbook register which shows empty.
How do I get my imported .qif entry's into the checking account register??

All I want is a simple checking account register.

Thanks to anyone who can help.

---

### Post by Pappy1911 on 2008-12-09
Bump..Anybody??
I really tried and cannot find answer anywhere.

---

### Post by SamNSane on 2008-12-10
I'm a GnuCash user (about 2 years), but would hardly call myself an expert. I'm afraid that I don't know what you mean by "checkbook". GnuCash views everything as an account -- no categories or whatnot like in MSMoney. (Man, I really hated Money.) But if the data you exported from Money / imported into GnuCash was complete (with each of your bank accounts represented) you should have a corresponding account for each after importing -- with a register to show the complete transaction history for each.

It took me a while to get used to the different way of doing things (like the double-entry methods GnuCash employs), but I love it now. You might need to look into the preferences dialogs to set the registers up so that they look more like what you're used to, but you do need to be aware that GnuCash does most things very differently than Money or Quicken.

There are some folks at [this forum]("http://www.nabble.com/GnuCash-f1248.html") who seem to be pretty knowledgable. If you can provide really precise information about what you're doing and what you see from GnuCash on that forum you may be able to find some help.

---

### Post by Pappy1911 on 2008-12-10
Thanks SamNSane.
I have used 2002 MSMoney for years and it fits my needs perfectly, however since switching to Linux Ubuntu, I wanted something to replace Money. I still use Money through Wine.
So I loaded Gnucash.
Exported Money into a .QIF file.
Imported the .QIF file into Gnucash.
And it's all there in Gnucash Accounts, altho in a list form.
I made a sub-account - checking account.
It shows headings etc. that I want, but is empty.
Question is, how to get all my history into the empty checking account??

Thanks again and now to look at your suggested link.

---

### Post by SamNSane on 2008-12-10
I believe you'll find that your imported transaction list from your checking account is already in one of those accounts / lists. You shouldn't need to create a new one to populate because it should already be there. It just may be hard to recognize because of the way it's displayed. Through the preferences dialogs you can have quite a bit of control over the display and the way various controls like the Enter key work in the registers.

You should be able to reorganize the accounts if you need to do so. For instance, you could create a parent account called bank. This "bank" account could be just a "place holder" or it can be set to show as its balance the sum of all accounts placed under it in the organizational tree. You could move your checking, savings, certificates of deposit, whatever into position as children of the parent bank account.

You will probably need to do a lot of rethinking to use GnuCash after having been used to the way Money does things. Remember that GnuCash views as accounts the things that you probably called categories in Money. This makes a material difference in the way transactions are recorded, displayed, and accounted for. There's very little difference between the groceries account and the checkbook register in GnuCash. They are only different types of accounts (asset and expense), but they are displayed in the same format. I like the way it works, but it confused me at first. My wife, on the other hand, is a CPA. She loved it right from the beginning and always hated the single-entry stuff like Quicken and Money. You will have a much easier time if you remember that EVERY time you make an entry in one account, there must be entries in another account (or accounts) to balance it. When you spend money in the form of a check from the check account (an asset account) to the hardware store, for instance, you will have to make a manual entry or entries into the expense account or accounts (supplies, hardware, whatever you've named the expense accounts).

Your process of exporting from Money and importing into GnuCash may be made more complex by the age of the Money application you are using. I'm sure that Money's ability to export data has been changed (whether "enhanced" or not) with each subsequent version of the software. I suppose it's possible that the .qif files produced by your version of Money may not work well for importing into your version of GnuCash. So, it may be important when you are asking experts for guidance that you provide the GnuCash version as well as the Money version in your posts.

---

### Post by Pappy1911 on 2008-12-10
Thank you again. I will do a little playing around later. I'm just too weary at this point.

I plan to get a new computer in a month or so.
I think Dell has a unit with Linix installed and that was my first choice. Then I remembered TAX time is coming up and I need Windoze for TurboTax. So it looks like an HP unit with a large (1TB drive)and partition MS into a back corner. 
And of course, still using Money....sigh..

Scary that MS has such a strong grip on the computer world...

Regards

---

### Post by SamNSane on 2008-12-10
> **Pappy1911 said:**
> Thank you again. I will do a little playing around later. I'm just too weary at this point.

I plan to get a new computer in a month or so.
I think Dell has a unit with Linix installed and that was my first choice. Then I remembered TAX time is coming up and I need Windoze for TurboTax. So it looks like an HP unit with a large (1TB drive)and partition MS into a back corner. 
And of course, still using Money....sigh..

Scary that MS has such a strong grip on the computer world...

Regards

Hi, Pappy1911.

You should use whatever works best and most comfortably for you. Choice of operating systems is only a matter of a cost vs benefit analysis, and nothing more. As virtual monopolies go, I really think Microsoft isn't that bad. (I can think of lots of big corporations that are really pretty evil. Trying to apply that adjective to MS is probably a no go -- especially for those who have some understanding of the context in which the company operates.)

I do systems administration work for publishers who use Windows and MacOS almost exclusively on the desktop and for most applications servers, but all of my remote admin machines are Linux, and everything around the house is Linux. My wife is a systems analyst (and CPA to boot) and is really good at it, but she's too busy to be conscripted for our purposes right now.

;)

We only made the switch to Linux a couple of months ago, though I had taken a look at a few distros over the past three years or so. There were a few rough edges, to be sure. Some of the teething problems a newcomer to Linux is likely to run into (unless s/he gets a machine that was actually designed to work with Linux) can be pretty daunting. A lot of other problems that new Linux folks run into are caused by thinking that they must continue to interact with their systems the way they did under Windows.

I'm certain that, especially with compliant hardware, you'll have no trouble adjusting to the new environment. But I think you should always keep it on the fun side. If it stops being fun, you're either using the wrong tools, or you're not using them as they were intended to be used.

Don't forget to look to other sources for information, too. I found the pop-up tutorial that comes with GnuCash to be really useful. And there may be forums / newsgroups where you can find some real experts.

I have enjoyed talking with you. I hope this will be a fun adventure for you.

---

### Post by Pappy1911 on 2008-12-10
Thank you and the best to you and yours..

---

### Post by bobnutfield on 2008-12-10
> **SamNSane said:**
> Hi, Pappy1911.

You should use whatever works best and most comfortably for you. Choice of operating systems is only a matter of a cost vs benefit analysis, and nothing more. As virtual monopolies go, I really think Microsoft isn't that bad. (I can think of lots of big corporations that are really pretty evil. Trying to apply that adjective to MS is probably a no go -- especially for those who have some understanding of the context in which the company operates.)

I do systems administration work for publishers who use Windows and MacOS almost exclusively on the desktop and for most applications servers, but all of my remote admin machines are Linux, and everything around the house is Linux. My wife is a systems analyst (and CPA to boot) and is really good at it, but she's too busy to be conscripted for our purposes right now.

;)

We only made the switch to Linux a couple of months ago, though I had taken a look at a few distros over the past three years or so. There were a few rough edges, to be sure. Some of the teething problems a newcomer to Linux is likely to run into (unless s/he gets a machine that was actually designed to work with Linux) can be pretty daunting. A lot of other problems that new Linux folks run into are caused by thinking that they must continue to interact with their systems the way they did under Windows.

I'm certain that, especially with compliant hardware, you'll have no trouble adjusting to the new environment. But I think you should always keep it on the fun side. If it stops being fun, you're either using the wrong tools, or you're not using them as they were intended to be used.

Don't forget to look to other sources for information, too. I found the pop-up tutorial that comes with GnuCash to be really useful. And there may be forums / newsgroups where you can find some real experts.

I have enjoyed talking with you. I hope this will be a fun adventure for you.

Very well written comments and I enjoyed reading them.  While I disagree with you about Microsoft's dominance of the desktop (I believe it is very bad for the industry as a whole), I certainly agree that keeping it fun is the ingredient that counts.  I remember the days of agonizing with a piece of hardware in Linux (Red Hat back in 1997).  But now with a sound understanding of the OS, even the problems are fun.  However, I recently had the experience of loading Windows on a laptop for a friend.  Converts like yourself (a professional in the business) will help the open source cause.

By the way, for what it is worth, a close friend is an executive with MS in the UK.  Their dominence is coming to an end, and they know it.

---

### Post by SamNSane on 2008-12-10
> **bobnutfield said:**
> Very well written comments and I enjoyed reading them.  While I disagree with you about Microsoft's dominance of the desktop (I believe it is very bad for the industry as a whole), I certainly agree that keeping it fun is the ingredient that counts.  I remember the days of agonizing with a piece of hardware in Linux (Red Hat back in 1997).  But now with a sound understanding of the OS, even the problems are fun.  However, I recently had the experience of loading Windows on a laptop for a friend.  Converts like yourself (a professional in the business) will help the open source cause.

By the way, for what it is worth, a close friend is an executive with MS in the UK.  Their dominence is coming to an end, and they know it.

Oh, I'm not thrilled with the ubiquitous presence of Windows in industry. It gets used for many purposes for which it couldn't be more poorly suited -- like control of real-time production processes, for instance. Couple the poor choice of OS with the atrociously written, high-priced production controls software, and you've got a system that is always on the verge of failing. I oversee bindery lines over 20 years old controlled by ancient Unix boxes, and I oversee "modern" brand new lines which have Windows controllers. Care to guess which ones are not only the most reliable, but also the most versatile?

But the "captains of industry" (many of them, at least) steadfastly continue to purchase new systems based on the unbelievably ignorant assumption that, because most of their users have Windows computers at home, they will be better able to use this OS in functions for which it and the software riding on it is hopelessly inadequate. Then, of course, they hire a boob like me to try to make it run without falling down.

Eh, it's a living.

;)

---

