---
title: "Installing Dictionary.."
date: 2010-04-14
forum: New to Ubuntu
---

### Post by karthick87 on 2010-04-14
Is there any Dictionary to use it in ubuntu.?If so pls someone tell me how to install the package..Thanks in advance

---

### Post by skyeric on 2010-04-14
there is one built into ubuntu presuming you have the 'Gnome Desktop Utilities' package.
If you dont have it just search for it in the software centre. I suppose it's posible it's not auto-installed on 9.04. It should be in Applications>Office>Dictionary.
hope this helps,
Eric

---

### Post by karthick87 on 2010-04-17
I need something like [COLOR=Red]oxford [/COLOR]dictionary.

---

### Post by SwatKat on 2010-04-17
The latest versions of oxford advanced learner's dictionary and longman's dictionary can be installed in linux. If you are looking for one thats free, I think Artha is a good general purpose dictionary. Its in the repos. 
```
sudo apt-get install artha
```
But It has no audio pronunciations.

---

### Post by karthick87 on 2010-04-17
```
karthick@Learners-desktop:~$ sudo apt-get install artha
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package artha

```

---

### Post by SwatKat on 2010-04-18
It was in the Karmic repos, so I assumed it would be in Jaunty's as well. Sorry, my bad. Follow this please
[http://ubuntuforums.org/showthread.php?t=1065384](http://ubuntuforums.org/showthread.php?t=1065384)

---

### Post by Linuxforall on 2010-04-18
Apart from Artha, stardict is another excellent choice with myriads of dictionaries including Oxford, Webster and others and has voice support as well.

---

### Post by Phil Hansen on 2010-04-18
> **SwatKat said:**
> It was in the Karmic repos, so I assumed it would be in Jaunty's as well.

It is in Jaunty and works perfectly for me.

---

### Post by IndyGunFreak on 2010-04-18
> **Phil Hansen said:**
> It is in Jaunty and works perfectly for me.

Then he likely has a source issue...

---

### Post by go_beep_yourself on 2010-04-21
> **Phil Hansen said:**
> It is in Jaunty and works perfectly for me.

Can you confirm which repository yours came from?

---

