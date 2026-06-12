---
title: "Evolution not showing new emails"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by ashwat on 2009-03-18
Couple of days back, I was asked by Evolution to enter the passwords for the accounts that  had setup. After this, whenever Evolution fetches the new emails it has not shown them. On the server the messages are being shown as read, so that means they are being fetched for sure. All I want to know is where is Evolution hiding my emails and why and also what ransom do I have to pay to get them back.

---

### Post by jpoRS on 2009-03-18
I had a similar problem awhile back.  I am trying to find the thread but no luck so far.

The solution I found:
```
sudo apt-get install thunderbird
```

Evolution is buggy as all get out.  I am not saying T-Bird is the solution, I just figured you would appreciate knowing that if you are committed to Evolution there is a long road ahead of you.

Good luck!
jim

---

### Post by stchman on 2009-03-18
> **jpoRS said:**
> 
Evolution is buggy as all get out.  I am not saying T-Bird is the solution, I just figured you would appreciate knowing that if you are committed to Evolution there is a long road ahead of you.

Good luck!
jim

I could not disagree more.  I have been using Evolution for over two years and it checks all 5 of my email accounts very well.  Evolution has never given me any problem.  It does the job very well.  When I first started using Evolution I was able to set it up in a matter of say 10-15 minutes.

Now I do like that Thunderbird keeps ALL its settings in the ~/.thunderbird folder where Evolution keeps emails in the ~/.evolution folder while other settings in the ~/.gnome folder.

Is it perfect?  No.  Name me one email program that is perfect.

Apparently the OP has a wrong setting somewhere.  That is a much better explanation that <insert program> is buggy as all get out.

Email clients are a matter of personal preference.  I was an Outlook user for years and Evolution's familiar interface was a natural for me.

---

### Post by ashwat on 2009-03-18
> **stchman said:**
> I could not disagree more.  I have been using Evolution for over two years and it checks all 5 of my email accounts very well.  Evolution has never given me any problem.  It does the job very well.  When I first started using Evolution I was able to set it up in a matter of say 10-15 minutes.

Now I do like that Thunderbird keeps ALL its settings in the ~/.thunderbird folder where Evolution keeps emails in the ~/.evolution folder while other settings in the ~/.gnome folder.

Is it perfect?  No.  Name me one email program that is perfect.

Apparently the OP has a wrong setting somewhere.  That is a much better explanation that <insert program> is buggy as all get out.

Email clients are a matter of personal preference.  I was an Outlook user for years and Evolution's familiar interface was a natural for me.

could you please tell me what settings could have gone wrong. I disabled the accounts and put the account settings in again afresh and still the problem persists.

As far as Thunderbird goes, the instructions I was given to backup my mails on T-Bird went astray such that when I restored, the settings were maintained but the mails were lost, whereas with Evolution backup is a default option and it works the way it is supposed to. So I for one am not going to give up on Evolution. All I need is a way to figure my way through this situation.

---

### Post by plucky on 2009-03-18
Try **View > Preview > Show Message preview** is ticked.

Also it might help if you post a picture of your Evolution window,but make sure all personal information is blanked out.

Does your Inbox show you have new messages?

If your window looks like the attached picture,then click and drag where indicated to open the window to show message preview.

Good Luck

---

### Post by ashwat on 2009-03-18
Surprise Surprise. They are all in my Junk. Now I do not know how that happened but once i UNJUNKED them messages, and tried receiving, it has started working. Now all I want to know is what the hell happened in the first place.

---

### Post by avdzm on 2009-12-03
Ah, thats where they have been hiding...
thanks,
i don't know i didn't see the junk folder growing...
anyhow thanks

---

