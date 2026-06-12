---
title: "graphics card"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by pepperbdl on 2009-01-30
:(I want to see if my graphics card can handle compiz. However I can't locate the information about what kind of card is in my laptop. Can anyone help?

---

### Post by pepperbdl on 2009-01-30
I need to know if the graphics card in my laptop will support compiz, but I don't know where to find the information on what kind of graphics card I have. Can anyone help?

---

### Post by overdrank on 2009-01-30
Hi and welcome, please do not make multiple threads on the same issue.
Threads merged :)
Have you tried to enable the effects by going to system, preference, appearance.  Then use the visual effects tab and select normal or extra.
To identify your hardware, you may use the command lspci in the terminal which is located under, applications, accessories. Look for VGA and this is the graphics.

---

### Post by pepperbdl on 2009-01-30
thanx and sorry about the double post. i didn't think the first one went thru.

---

### Post by pepperbdl on 2009-01-30
I did that and it said "command not found"

---

### Post by overdrank on 2009-01-30
> **pepperbdl said:**
> I did that and it said "command not found"

the command is ```
lspci
``` that is a lower case L

---

### Post by pepperbdl on 2009-01-31
THANK YOU   It lists alot of stuff......20 lines of info. The VGA you mentioned states this  "VGA compatible controller..ATI Technologies Inc. Radeon Mobility M6 LY." Is this my graphics card and if so, can I put updated drivers in this card so I can use compiz more effectively or is this computer to old?

---

### Post by overdrank on 2009-01-31
> **pepperbdl said:**
> THANK YOU   It lists alot of stuff......20 lines of info. The VGA you mentioned states this  "VGA compatible controller..ATI Technologies Inc. Radeon Mobility M6 LY." Is this my graphics card and if so, can I put updated drivers in this card so I can use compiz more effectively or is this computer to old?

Hi and it would appear that is the  Radeon 7000 and I have it working pretty well with Hardy 8.04 and the effects. 
What version are you using
You can find this under system, about Ubuntu.

---

### Post by pepperbdl on 2009-01-31
ubuntu 8.10 intrepid I believe ... because this is an older (gateway 400 SD4) computer i may need down grade to hardy...u tell me...?

---

### Post by overdrank on 2009-01-31
> **pepperbdl said:**
> ubuntu 8.10 intrepid I believe ... because this is an older (gateway 400 SD4) computer i may need down grade to hardy...u tell me...?

That would be up to you. :) Have you tried to enable the effects? You may also look at [compiz-check]("http://ubuntuforums.org/showthread.php?t=799070") as it is a great tool.

---

### Post by pepperbdl on 2009-01-31
...OK...if i can not get compiz to run with my graphic ability ...i may need to use hardy...yes,i went to add/remove and check 4 compiz...however that all i was able to do.I played around with it for awhile and was unable to change anything...was i suppose to do something else after the add/remove process ? what is compiz-check...i could not find it anywhere?

---

### Post by pepperbdl on 2009-01-31
Thankz so much for all of your help--the compiz link was a big help! And even tho' I still didn't get the pointer thingy to work I now know that compiz works on my computer. I did get wobbley windows and cube screen to work.:D I've only been using Ubuntu for a few days, but I don't think I could ever go back to windoze. Thanks again for all of your help.

---

