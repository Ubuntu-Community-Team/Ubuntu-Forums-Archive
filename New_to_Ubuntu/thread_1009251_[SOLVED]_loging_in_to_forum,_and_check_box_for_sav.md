---
title: "[SOLVED] loging in to forum, and check box for save password does not work"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by newbie1000 on 2008-12-12
When I log into this forum (8.10 and Firefox 3.0.4) the text box for my login name will only allow me to enter text if I click on the bottom line of the text box.  Clicking on the area inside the text box does nothing.  All other text boxes appear to work.

I  also can not click the 'save password' box.

:confused:
The confused icon is sure getting used a lot by this newbie.
:lolflag:

---

### Post by Duck2006 on 2008-12-12
Are you running compiz?

---

### Post by newbie1000 on 2008-12-12
compiz?
You are talking to a complete idiot here.
:p

---

### Post by Duck2006 on 2008-12-12
Do you have visual effects turn on?

---

### Post by wolfen69 on 2008-12-12
sounds like firefox is corrupted. reinstalling it may help.

go to system>administration>synaptic package manager and search for firefox. choose completely remove. then go to applications>accessories>terminal and type in:
```
sudo apt-get clean
```then ```
sudo apt-get autoremove
```
then open your home folder and do Ctrl-h. this will show you your hidden files. delete your .mozilla folder. then go back to synaptic and reinstall firefox.

---

### Post by newbie1000 on 2008-12-12
Under Sys>Pref>Appearance> Visual Effects
It's set to 'Normal'
Should I make it 'None'?

---

### Post by Duck2006 on 2008-12-12
No leave it as is. Try what "wolfen69" has posted, and see if that fixes it.

---

### Post by newbie1000 on 2008-12-12
*delete your .mozilla folder. then go back to synaptic and reinstall firefox.*

Will FireFox work if the .mozilla folder is gone?

---

### Post by Duck2006 on 2008-12-12
> **newbie1000 said:**
> *delete your .mozilla folder. then go back to synaptic and reinstall firefox.*

Will FireFox work if the .mozilla folder is gone?

When you reinstall it again, it will put the mozilla folder back.

---

### Post by newbie1000 on 2008-12-12
Thanks, guys.   I'm going to do some reading before I try it.
):P

---

### Post by newbie1000 on 2008-12-22
> **wolfen69 said:**
> sounds like firefox is corrupted. reinstalling it may help.

go to system>administration>synaptic package manager and search for firefox. choose completely remove. then go to applications>accessories>terminal and type in:
```
sudo apt-get clean
```then ```
sudo apt-get autoremove
```
then open your home folder and do Ctrl-h. this will show you your hidden files. delete your .mozilla folder. then go back to synaptic and reinstall firefox.

This worked like a charm.

---

