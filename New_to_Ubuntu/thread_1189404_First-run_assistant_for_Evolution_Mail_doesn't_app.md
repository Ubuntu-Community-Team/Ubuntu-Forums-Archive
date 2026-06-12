---
title: "First-run assistant for Evolution Mail doesn't appear"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by hector24 on 2009-06-16
I am totally new to all this - only had Ubuntu installed last weekend.  I need to know a few things.  I can't get my mail in Evolution Mail as the First-run assistant doesn't appear.  Is there another way of getting connected?

Many thanks for any help that may be out there.

---

### Post by abhiroopb on 2009-06-16
Have you used it before?

If not go to your /home/<user> folder and click Ctrl+H, then look for .evolution folder and delete it.

This will WIPE all your evolution settings and reset it. If you have not used it before, this won't delete anything important. But if you have been using it it will delete all your evolution data, so be careful.

But deleting this and restarting evolution should show the first-run assistant.

---

### Post by hector24 on 2009-06-18
Many thanks for your help.  I can find 'Home' in 'Places' but nothing which says <user>.  Am I looking in the wrong place?

---

### Post by abhiroopb on 2009-06-18
Usually when people in the forum right <user> it just means your name...for example mine is...

/home/abhiroop

Anyway go to Places>Home and then do the rest like I suggested.

---

### Post by hector24 on 2009-06-18
I've just found it.  I tried using Evolution to send an email.  Does that mean I shouldn't delete it?  Under the .evolution folder there is: addressbook, cach, calendar, mail, memos and tasks.  Do I delete all these?

---

### Post by hector24 on 2009-06-18
Thanks, you're very patient.

I've done as you said and deleted the .evolution file.  I went back into Evolution but there was no first-run assistant.  Can you think of anything else?

---

### Post by abhiroopb on 2009-06-18
Just a bit of clarification - the first run assistant is what you get when you start up evolution right? There's a wizard asking for information?

Just glad to help...bear in mind though I don't use evolution so my tips are very general, based on what works with MOST software.

---

### Post by hector24 on 2009-06-18
Yes, I'm expecting to see a wizard to guide me through setting up Evolution to use with my Tiscali account.  Still no wizard.

Does anyone use Evolution?  Is there another way to connect without the wizard?

---

### Post by mgmiller on 2009-06-18
In Evolution click on Edit > Plugins.
The plugin manager should appear.  Scroll down the list to the "Setup Assistant" entry and make sure it's checked.   Exit Evolution.  Then you can delete the .evolution folder as mentioned earlier and try restarting Evolution.  

Failing that, you can set up a new account and specify all the needed things by going to Edit > Preferences and clicking on the Mail Accounts on the left side and then the Add button on the right.  You can then step through everything to set up the new account.

---

### Post by hector24 on 2009-06-19
Many thanks for your help.  I have now got Evolution up and running.  :P

---

### Post by t0p on 2009-06-19
If anyone else has the same problem, I thought I'd point out that you don't need the "first-run assistant" in order to create a new account in Evolution.  Click on **Edit > Preferences > Mail Accounts > Add**.  You can then configure a new email account.

You can also do the above at any time to create a second/third/whatever account.  So you can get mail from, for example, your ISP account, your Gmail account, your Yahoo premium... etc.

---

