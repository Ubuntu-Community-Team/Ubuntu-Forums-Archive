---
title: "Firefox is using UK English for spell checker instead of US English"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by aharown07 on 2009-08-31
For some reason my Firefox is using UK English for the spell check... so centre is OK, but not center, for example.

I can't seem to find any info on why this is or how to switch it to US English.

(Using FF 3.0.13 and Jaunty)

---

### Post by gardara on 2009-08-31
Can't you just install the US one?

[https://addons.mozilla.org/en-US/firefox/browse/type:3](https://addons.mozilla.org/en-US/firefox/browse/type:3)

:)

---

### Post by Giant Speck on 2009-08-31
Right-click in a text box within Firefox and go to Languages.  There should be a list of spellcheck languages to choose from.

---

### Post by cascade9 on 2009-08-31
Edit-> Preferences-> Content-> Languages. Easy 

Unless they moved it after 3.0.6 anyway

---

### Post by aharown07 on 2009-08-31
I probably should have mentioned that already did all that. Downloaded English US, selected in the menu. No change. Still using UK English in the spell checker.
I think the menu option under tools actually applies to the interface anyway and not the spell checker. 

I think I read somewhere that FF and other apps actually get that from Linux somehow. But what I read was for people who were getting the US and wanted the UK, and the advice was to switch languages in "gdm."
But the posts were a few years old and I couldn't find anywhere to select language in gdm (assuming I even correctly identified what "gdm" was... they didn't say). 

When I installed, I'm pretty sure I selected English US but it's possible that I hurried by that screen and got a bit sloppy. But I don't know where to change this.

---

### Post by rbc on 2009-08-31
How about this....unless you have also tried already, at the logon screen, before you type in your username and password, select Options-->Select Language

---

### Post by gn2 on 2009-08-31
Something to try at your own risk: type about:config in the address bar 
See if you can find the general.useragent.locale value, double click on it and change it to en-US

---

### Post by aharown07 on 2009-08-31
Did the log on options language select... no change. About:config: already has en-US.

Yet, as I type right now, "centre" is not flagged as misspelled but "center" is. Same with theater, skeptic and and honor.  
So somehow it's still using a UK dictionary anyway.

---

### Post by winotree on 2009-09-01
By chance did you run *localepurge* and select some version of English other than US to save??  I can't imagine how to correct it but someone else may -- just trying to help narrow your list of possibilities.  ;)

---

### Post by aharown07 on 2009-09-01
No, didn't do any purge.

---

### Post by winotree on 2009-09-01
Have you thought about creating a new profile in the off-chance that yours somehow became corrupted?  Here's a starting point [http://kb.mozillazine.org/Profile_folder_-_Firefox](http://kb.mozillazine.org/Profile_folder_-_Firefox) if you didn't already have it bookmarked.

---

### Post by aharown07 on 2009-09-02
> **winotree said:**
> Have you thought about creating a new profile in the off-chance that yours somehow became corrupted?  Here's a starting point [http://kb.mozillazine.org/Profile_folder_-_Firefox](http://kb.mozillazine.org/Profile_folder_-_Firefox) if you didn't already have it bookmarked.
No, haven't tried that. Will give it a whirl.

---

### Post by aharown07 on 2009-09-02
Deleted profile (after backing up) and profile.ini. Ran FireFox. 
It then makes a new profile.
Tested spelling... sill using UK English. 
I think I found the problem thugh. The version under Help About says en-GB.
So the real question is why did Ubuntu install the GB version when I installed. I selected the wrong language mabye? 
How would I find out if that's what I did. Is there a command I can run to show what language I installed in? I know it's set to US now, so... maybe if I uninstall and reinstall FF, I get the US version?


Edit: uninstalled FF completely with Synaptic. Then installed FF 3.5.2 using Ubuntuzilla. The version now shows as en US. But still it uses UK/GB English for the spell checker!
(BTW, I installed Opera 10 and it uses the right language, for whatever that's worth. FF is my main browser either way, but there is something different about it handles spell checking in Linux)

---

### Post by aharown07 on 2009-09-02
Well, I finally installed the SpellBound addon for FireFox and selected US English. Now everything's fine.
Still no idea why it goes to GB/UK like that w/o the plugin, though.

---

### Post by winotree on 2009-09-02
Ah!  Good deal!  :D  I'm just thinking out loud now but I was under the impression that uninstalling and re-installing Firefox -- while you still had the old profile -- made no difference because it (Firefox) kept copies of itself that were unaffected by the uninstall, etc.  Regardless, you've got your system working the way you want it right now, eh?  ;)

---

### Post by aharown07 on 2009-09-02
> **winotree said:**
> Ah!  Good deal!  :D  I'm just thinking out loud now but I was under the impression that uninstalling and re-installing Firefox -- while you still had the old profile -- made no difference because it (Firefox) kept copies of itself that were unaffected by the uninstall, etc.  Regardless, you've got your system working the way you want it right now, eh?  ;)
Yes... I deleted the old profile also. Didn't make any difference.

---

### Post by lotus49 on 2009-09-10
> **Giant Speck said:**
> Right-click in a text box within Firefox and go to Languages.  There should be a list of spellcheck languages to choose from.

This worked for me after I had installed the British English (ie English) dictionary manually (my problem was the same but the other way round).

---

