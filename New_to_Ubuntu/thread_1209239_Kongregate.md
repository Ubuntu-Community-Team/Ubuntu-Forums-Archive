---
title: "Kongregate"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by wertha on 2009-07-10
I installed the flash plugin from Adobe's site. But i can't play any game at kongregate. It doesn't load.

---

### Post by earthpigg on 2009-07-10
> **wertha said:**
> I installed ____________ from _______'s site.

unless there is a good reason not to or a feature that you desire lacking, your best bet is almost always to install from the repositories :)

```
sudo apt-get install ubuntu-restricted-extras
```

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by earthpigg on 2009-07-10
i just went to that site and loaded the first random game i saw, played fine with ubuntu-restricted-extras installed :P

ensure that after you install ubuntu-restricted-extras, you restart your browser.

---

### Post by wertha on 2009-07-10
earthpigg thanks for the answer. I tried that command, and still can't play any game. I reinstall flashplugin from the repository and nothing. I install the nonfree flashplugin and nothing. 

This is pissing me off.

---

### Post by earthpigg on 2009-07-10
thinking back to my first ubuntu install, i had trouble making flash work after making the same initial mistake you did and installing from the adobe website, too. i dont remember exactly what i did to correct it. but, lets see what we can do for you....

system -> administration -> synaptic package manager

look for 'adobe' and 'flash' in the search bar.

all you should have, i believe, is flashplugin-installer and flashplugin-nonfree. what do you have?

in firefox, put about:plugins in the address bar and press enter. what flash-related things are listed there?



basically, our goal is to remove anything flash-related except what is included in ubuntu-restricted-extras. you may have to reinstall firefox, too... im not sure. lesson learned, though: stick to the repos when possible, in the future ;)

edit: about:plugins is supposed to be "about : plugins" - but with no space in there. ubuntuforums.org is trying to be smart and turn the : followed by 'p' into a smiley face.

---

### Post by binbash on 2009-07-10
can you see the flash plugin at about:plugins ?

---

### Post by mikodo on 2009-07-10
> **earthpigg said:**
> i just went to that site and loaded the first random game i saw, played fine with ubuntu-restricted-extras installed :P

ensure that after you install ubuntu-restricted-extras, you restart your browser.

earthpigg: If I can break into this thread; could you explain what restricted-extras is and how it is different than the Ubuntu applications available in ADD/remove Applications? Is it more than the All available applications; All open source applications; Supported applications; Third party applications; and Installed applications.

Is it the packages available in Synaptic Package Manager? ie.Main; Universe;Restricted; Multiverse.

Thank you

mikodo

---

### Post by zvacet on 2009-07-10
@ **mikodo**

You can find it in add/remove>all available applications>ubuntu-restricted-extras.You need mutliverse repo for that.

@ **wertha**

Edit your source list with 

```
gksudo gedit /etc/apt/sources.list
```

and add this line 


deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

System>admin>synaptic>remove flashplugin-nonfree and install adobe-flashplugin.

---

### Post by wertha on 2009-07-10
thanks a lot :)

---

### Post by earthpigg on 2009-07-10
@wertha - glad we got you squared away.

> **mikodo said:**
> earthpigg: If I can break into this thread; could you explain what restricted-extras is and how it is different than the Ubuntu applications available in ADD/remove Applications? Is it more than the All available applications; All open source applications; Supported applications; Third party applications; and Installed applications.

Is it the packages available in Synaptic Package Manager? ie.Main; Universe;Restricted; Multiverse.

Thank you

mikodo

there is usually more than one way to skin a cat, so to speak, in ubuntu.

a) applications -> add/remove programs -> show: all available applications -> search for ubuntu-restricted extras -> check it -> apply changes

b) find it in synaptic package manager and install from there.

c) ```
sudo apt-get install ubuntu-restricted-extras
```

all do the *_exact_* same thing.

but typing sudo apt-get install ubuntu-restricted-extras is easier than going in depth with the click here click there, so that is usually what i (and many/most others on this forum) tell people to do.... about 80% of the terminal commands people post on the forums can also be done by pointing and clicking. i happen to have 'sudo apt-get install whatever' memorised, so that's what i went with as the quickest and easiest way to tell wertha how to solve his problem and get back to doing whatever it is he wants to _**do**_ on his computer.

ubuntu-restricted-extras is in the non-free multiverse repository because it is non-free software... ie: _**your**_ freedoms are restricted, because you do not have all four essential software freedoms.

[http://www.fsf.org/licensing/essays/free-sw.html](http://www.fsf.org/licensing/essays/free-sw.html)

> * The freedom to run the program, for any purpose (freedom 0).
* The freedom to study how the program works, and change it to make it do what you wish (freedom 1). Access to the source code is a precondition for this.
* The freedom to redistribute copies so you can help your neighbor (freedom 2).
* The freedom to improve the program, and release your improvements (and modified versions in general) to the public, so that the whole community benefits (freedom 3). Access to the source code is a precondition for this.

freedom 0 - you would have to read the EULA for adobe flash and everything else included with ubuntu-restricted-extras to figure this one out. i sincerely doubt we have this freedom, but i am no lawyer.

freedom 1 - since we can not see the source code for everything in ubuntu-restricted-extras, we do _**not**_ have this freedom if we chose to install that software.

freedom 2 - adobe let's ubuntu pass its software on to neighbours (me and you), so i suppose we have that one.

freedom 3 - we do _**not**_ have this freedom in any way whatsoever with ubuntu-restricted-extras.

ubuntu does not include ubuntu-restricted-extras for these reasons. see: [http://www.ubuntu.com/community/ubuntustory/philosophy](http://www.ubuntu.com/community/ubuntustory/philosophy). however, if _**we**_ choose to restrict our own freedom in order to watch youtube or play mp3 files, ubuntu _**empowers us**_ to make that decision for ourselves.

some gnu/linux distributions do not give you that choice - they either include non-free stuff by default, or they make you jump through hoops and hack your system to hell and back to get the stuff to work.

Ubuntu's compromise, in my opinion, is both practical and outstanding.



/end rant.

---

### Post by mikodo on 2009-07-10
Thank you earthpigg. That answers the questions. I have learned some more about open source and Ubuntu. I should have said ( Free Software) to correctly quote the thread and link.


mikodo

---

