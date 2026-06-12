---
title: "No Sound Ubuntu 9.10"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by Jolicoeur on 2010-09-01
[FONT=Arial]I am using sound debugging tuturial. Ran uname -r and the result was not 2.6.31 (should be this).  Next to fix this I entered and ran;[/FONT][FONT=Arial]sudo update-grub and then restarted and checked uname -r again 

Same wrong number. Says, if this happens then 
"please see the documentation for grub for further troubleshooting." 
I don't know what this means and I don't see a link for it. 
Can somebody please help?[/FONT][FONT=Arial] [/FONT]

---

### Post by madverb on 2010-09-01
Try upgrade to 10.04.

---

### Post by Tracy177 on 2010-09-01
> **Jolicoeur said:**
> [FONT=Arial]I am using sound debugging tuturial. Ran uname -r and the result was not 2.6.31 (should be this).  Next to fix this I entered and ran;[/FONT][FONT=Arial]sudo update-grub and then restarted and checked uname -r again 

Same wrong number. Says, if this happens then 
"please see the documentation for grub for further troubleshooting." 
I don't know what this means and I don't see a link for it. 
Can somebody please help?[/FONT]

there could be anything it depends what kernel was shipped with your 9.10 and what kernel did you install latter u dont neet to worry about version of your kernel. 

i dont think there is an issue between your sound card and the karnel u have got. 

and sudo update-grub wont help you make your sound card work.

first at all check type alsamixer and check up if everything is unmuted .

not every sound card work with 9.10 and 10.04 out of the box for example i have acl1200 and had to install drivers and other things to make it work corectly.

---

### Post by Achilles124 on 2010-09-01
Better, use gnome alsamixer. Can be downloaded from the ubuntu download center. And indeed, make sure that nothing is unmuted that shouldn't be.

---

### Post by Jolicoeur on 2010-09-01
A couple days ago I updated to 10.04 and my laptop would not boot.  I loaded 9.10 again and then tried to load 10.04 by cd and it would not progress and load.  Any ideas on how to get the 10.04 cd to load?

---

