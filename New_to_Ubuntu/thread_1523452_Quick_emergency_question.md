---
title: "Quick emergency question"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by 29732 on 2010-07-03
I am installing BURG
[http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html)
and im on step on the BURG PPA and after it downloaded every thing, it showed me this:
[ATTACH]162318[/ATTACH]

HELP

---

### Post by 29732 on 2010-07-03
I
need 
help
please!

---

### Post by MooPi on 2010-07-03
What is the problem ? I can't tell from your post. Have you completed the install ?

---

### Post by 29732 on 2010-07-03
Well, since noone helped, 
I did what I thought was Best and now I'm going to test it

Ill reply if anything goes wrong

---

### Post by 29732 on 2010-07-04
And now I have a new question..

I have like 3 ubuntu images with their recovery console and 2 VIstas

Can I remove some of them to make the boot screen a bit cleaner???

---

### Post by 29732 on 2010-07-04
no response?

---

### Post by SoFl W on 2010-07-04
It is a holiday weekend, not everyone here uses BURG, not everyone here knows everything about it.  Your title "Quick Emergency Question" isn't too descriptive to get people to look at the thread.

My suggestions?
1) [https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)
2) [http://www.burgloader.com/bbs/](http://www.burgloader.com/bbs/)
3) Wait until Tuesday when more people will be around.
4) Use a search engine and see if other users from other linux distros have suggestions.

---

### Post by Penguin Guy on 2010-07-04
Please don't bump your threads so often. I'm installing BURG now, so I'll do a bit of experimenting and I'll post back here if I find a solution.

---

### Post by 29732 on 2010-07-04
k, thanks

^.^

---

### Post by MooPi on 2010-07-04
Please be patient. We are all just voluntarily helping and not always immediately. You will need to update grub. ```
sudo update-grub
``` Check with a reboot.

---

### Post by 29732 on 2010-07-04
> **MooPi said:**
> Please be patient. We are all just voluntarily helping and not always immediately. You will need to update grub. ```
sudo update-grub
``` Check with a reboot.

I don't really need to do that since Burg is working 

I'm just waiting on how to remove a few entries in burg like those older generic images

---

### Post by gandaran on 2010-07-04
> **29732 said:**
> I don't really need to do that since Burg is working 

I'm just waiting on how to remove a few entries in burg like those older generic images
if you are referring to the older linux kernels then just uninstall them, use synaptic package manager.

---

### Post by 29732 on 2010-07-04
how?

---

### Post by MooPi on 2010-07-04
deleted

---

### Post by tom.swartz07 on 2010-07-04
> **MooPi said:**
> Please be patient. We are all just voluntarily helping and not always immediately. You will need to update grub. ```
sudo update-grub
``` Check with a reboot.

It should be ```
sudo update-burg
``` instead, if you use update grub, it'll undo everything.

---

### Post by 29732 on 2010-07-04
i know, i know 

im just talking about removing 'older images and the vista and ubuntu recovery console so i lust wont see them but i would be able to get to them

except those images
i'd like to completely remove them

---

