---
title: "OOo Calc Dog Slow"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by ebates on 2010-02-19
Trying to work with an approx 14MB MSExcel file in Calc.  It's full of formulas , conditional formatting, and several graphs.  While it runs normally in Office 2003, in Calc it is just Dog Slow.  A quick look at CPU (using a AMD quad core 9750), memory (4GB), usage.  It apppears only about 800MB is being used.  Is it possible to allocate additional memory to tasks or applications running under Ubuntu.

Tx
EBates

---

### Post by HermanAB on 2010-02-19
Howdy,

I never use Calc - POS.  Gnumeric is much better.

---

### Post by mikewhatever on 2010-02-19
I don't know about all applications, probably not, but why is it relevant if you want OO to use more RAM? Anyway, take a look at the links below.

[http://lmgtfy.com/?q=ubuntu+office+speedup](http://lmgtfy.com/?q=ubuntu+office+speedup)
[http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu)

---

### Post by ebates on 2010-02-21
> **mikewhatever said:**
> I don't know about all applications, probably not, but why is it relevant if you want OO to use more RAM? Anyway, take a look at the links below.

[http://lmgtfy.com/?q=ubuntu+office+speedup](http://lmgtfy.com/?q=ubuntu+office+speedup)
[http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu)
Sorry, mikewhatever for having offended you, but as the forum title implies this a forum for gross newbies.  Which is exactly what I am. I was probably raised wrong.  I was taught that there is no such thing as a dumb question, but I guess that doesn't apply to forum threads. I'll to read the section on constructing a thread topic in order to avoid upsetting the community in the future.

Back to the subject.  Thanks for the information.  I'll give it a try.

Tx
EBates

---

### Post by Sir Jasper on 2010-02-21
Hi,

A few thoughts:

(1a) Does it use a macro that just adds rows or are the formatting changes more complicated?
(1b) Does it need to recalculate after every new entry or only at certain intermediate points or when all new entries are finalised?
(1c) Dependent upon the answers to the above,  you might try turning off automatic recalculation and just use F9 (or whatever the OO button is) to recalculate as and when necessary.

(2a) Are you saving it in OO or Microsoft format?
(2b) If appropriate, you might try saving it in OO format to see if there is any significant speed improvement when you next use it.

(3) I have read that Wine can successfully run Office 2003; so you might google to check or use the Search facility above.

(4) OO cannot [always] use Microsoft macros, so I suggest you check the output carefully; especially as that is a massive spreadsheet and KPMG (a major firm of international accountants) recently stated that 97% of business spreadsheets contain errors (presumably without the added complication changing programs).

My regards

Please let us know how to get on.

---

### Post by mikewhatever on 2010-02-21
> **ebates said:**
> Sorry, mikewhatever for having offended you, but as the forum title implies this a forum for gross newbies.  Which is exactly what I am. I was probably raised wrong.  I was taught that there is no such thing as a dumb question, but I guess that doesn't apply to forum threads. I'll to read the section on constructing a thread topic in order to avoid upsetting the community in the future.

Back to the subject.  Thanks for the information.  I'll give it a try.

Tx
EBates

Take it easy, you haven't offended anyone. Your question was perfectly legitimate, and the links I posted, very useful.:P

Best of luck.

---

### Post by lotharmat on 2010-02-21
> **mikewhatever said:**
> Take it easy, you haven't offended anyone... 

Maybe it was the lmgtfy link - Most people use them to convey annoyance at people not bothering to google (when did google become a verb?) an answer.

I know it is what I do to colleagues when they ask me dumb questions...

---

### Post by ebates on 2010-02-21
> **Sir Jasper said:**
> Hi,

A few thoughts:

(1a) Does it use a macro that just adds rows or are the formatting changes more complicated?
(1b) Does it need to recalculate after every new entry or only at certain intermediate points or when all new entries are finalised?
(1c) Dependent upon the answers to the above,  you might try turning off automatic recalculation and just use F9 (or whatever the OO button is) to recalculate as and when necessary.

(2a) Are you saving it in OO or Microsoft format?
(2b) If appropriate, you might try saving it in OO format to see if there is any significant speed improvement when you next use it.

(3) I have read that Wine can successfully run Office 2003; so you might google to check or use the Search facility above.

(4) OO cannot [always] use Microsoft macros, so I suggest you check the output carefully; especially as that is a massive spreadsheet and KPMG (a major firm of international accountants) recently stated that 97% of business spreadsheets contain errors (presumably without the added complication changing programs).

My regards

Please let us know how to get on.
Thanks for the food for thought.

In answer to your questions:
(1a) The spread sheet has no macros. Conditional formating has been used in the Office 2003 version, but has been disabled in the OOo version.  The only other formatting applied are display related font colors and cell background colors.

(1b, 1c) Calculation has been set to manual in all sheets.

(2a, 2b) Per your suggestion I have created a OOo version, but did not notice a significant change.

(3) I'm running dual boot Winxp pro and Ubuntu 9.10, so to this point MSOffice is still the preferred tool. Haven't tried Wine yet.

(4) No macros in the spreadsheet.

A quick description of this huge spreadsheet:
Three sheets, each containing (Rows/Columns) 6300/50,2800/6, 8800/45.  The contents is investment data, with formulas calculating delta, % change in value, earned value, and contributions.
Charts are included to display the data for analysis.  There are a total of nine charts within the three sheets.
All sheets are filtered to allow a look at an individual account or all accounts combined.

While trying out your suggestions, I note that updating the charts is where Calc really struggles.  I've deleted the charts from all of the sheets, as an experiment, which did make a significant difference in performance. I have to wonder about OOo ability to turn off automatic recalculation on charts.  Another possibility is that the video driver is not updating the display as quickly as it should.

You've provided some very good suggestions.  I much appreciate your help.

Struggling to learn
EBates

---

### Post by llamabr on 2010-02-21
i think lmgtfy is quite funny.  it doesn't hurt also for a new user to see how an experienced user googles for solutions.

In any case, I thought the reply was right on.  I'm not sure why you'd want to allocate additional ram to calc, nor how to do it, but there are simple fixes to speed up ooffice.  ask google.

---

### Post by ebates on 2010-02-21
> **mikewhatever said:**
> Take it easy, you haven't offended anyone. Your question was perfectly legitimate, and the links I posted, very useful.:P

Best of luck.
Sorry again, mikewhatever.
I read your salutation as a slap against my posting.  As I see your response, I recognize that it is your salutation.
I'm new please forgive my ignorance.

Tx
EBates

---

### Post by Sir Jasper on 2010-02-21
Hi again,

Thank for your response. Your application is very interesting. May I enquire if they are all Stock Market investments and, if yes, which market(s).

I have only two other thoughts:

Virtual box within 9.10, thus enabling 2003 Excel duplication might be OK and save a small amount of time switching from Ubuntu to Windows.

Alternatively, there are a couple other spreadsheets in the Synaptic Package Manager (but I do not know if they can read Excel or how fast they are). Gnumeric, mentioned above, may be already installed.

My regards

---

### Post by ebates on 2010-02-21
> **Sir Jasper said:**
> Hi again,

Thank for your response. Your application is very interesting. May I enquire if they are all Stock Market investments and, if yes, which market(s).

I have only two other thoughts:

Virtual box within 9.10, thus enabling 2003 Excel duplication might be OK and save a small amount of time switching from Ubuntu to Windows.

Alternatively, there are a couple other spreadsheets in the Synaptic Package Manager (but I do not know if they can read Excel or how fast they are). Gnumeric, mentioned above, may be already installed.

My regards
Sorry for my delayed response.
Found a new Nvidia driver and was installing it.

The spreadsheet data is daily tracking of Fidelity Investments stock and index accounts offered to my IRA at work.  I track the accounts I am invested in daily, and all 46 accounts on a weekly basis.  The data is used to guide the movement of assets from one account to another.  But, the last couple of years results seem to indicate that it's not the silver bullet I'd hoped for (Lol).

Virtual Box - To this point I am not smart enough to configure it.  Still a work in progress.  Never have tried it myself.  But, I've heard from others that I would not like it, too slow.

Gnumeric - Only learned about it today, plan to give it a try.

For now The dual boot works ok.

Until I get good enough with Ubuntu to be able to install and tweak it and it's apps, Winxp pro and it's apps will be there.

Note: The issues caused by the charts are related to recalculation.  In MS Excel the data in the charts is updated when the F9 (manual recalculate) key is pressed.  OOo updates the charts no matter the choice of auto or manual recalculate.  Really would like to keep my charts, so I'll google for a while on ways to stop that.

The new video driver was no magic bullet either

---

### Post by Sir Jasper on 2010-02-21
Hi,

Thank you for your update. I have the pragmatic view that since most ¨firms¨ use Windows it&#347; a good idea to keep one&#347; hand in however much one may grow to like ´buntu (as I have with considerable help and support from this Forum).

My regards

---

